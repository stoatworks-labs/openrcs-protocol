# Framing

Both the Midra and LiveCore series speak a terse ASCII protocol over **TCP port
10500**. A single control socket carries both directions; there is no banner or
handshake on connect.

## Command and reply layout

The protocol is **asymmetric** — a command ends with the mnemonic, a reply
begins with it:

```
set:    idx0,idx1,…,<value><MNEMONIC><terminator>
get:    idx0,idx1,…,<MNEMONIC><terminator>
reply:  <MNEMONIC>idx0,idx1,…,<value>
```

Each index is emitted followed by a comma. On a **set** the value is appended
with no trailing comma; on a **get** nothing follows the final comma. Worked
examples (Midra terminator shown):

```
1,2,5PMinp\r\n     set variable PMinp at indices (1,2) to 5
1,2,PMinp\r\n      request PMinp at indices (1,2)
PMinp1,2,5         the device's reply
```

## Terminators

| | Outbound (to device) | Reply (from device) |
|---|---|---|
| **Midra** | `CRLF` (`\r\n`) | `CRLF` |
| **LiveCore** | `LF` (`\n`) | `CRLF` |

The device terminates every reply with `CRLF` on both platforms. A decoder
should split incoming data on `\n` and trim a trailing `\r`.

## Decoding a reply

Scan past the leading mnemonic (the run of non-digit, non-`,`, non-`-`
characters) and split the numeric tail on `,`. **The last field is the value;
everything before it is the index tuple.** For a variable with no indices the
reply is simply `<MNEMONIC><value>`.

Replies are separated by `\n`. The device may split a reply across TCP reads, so
a receiver must buffer any trailing partial line until the rest arrives.

## Errors

A rejected command is answered with `E<code>` (followed by the reply
terminator). Known codes:

| Code | Meaning |
|---|---|
| `E10` | unknown command — the mnemonic is not recognised |
| `E12` | wrong number of indices for the variable |

An empty line draws no response. Because the error line is `E` followed only by
digits — and `E` is never a full mnemonic — it is unambiguous against a value
reply. Validating index rank and value range **before** sending avoids `E12`
entirely.

## Unsolicited updates (push)

The device pushes value updates without being asked, using the same reply
format. On connect it immediately sends the current controller count, and
thereafter any value that changes — whether from this client, another client,
or the device's front panel — is pushed. A client must therefore accept value
frames at any time, not only in response to a request, and treat them as the
source of truth for cached state.

## Concurrency

The device accepts a small number of simultaneous control sessions. Designs
that need to fan control out to many clients should place a single connection to
the device behind a proxy that re-serves it.
