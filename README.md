# openrcs-protocol

A reference for the **TCP control protocol** of Analog Way **Midra** and
**LiveCore** series video processors — the wire format, the variable model, and
the complete variable tables — as implemented by
[openrcs](https://github.com/stoatworks-labs/openrcs).

This repository is documentation only. It exists so anyone building control
software for these processors has a single, precise description of how they talk
on the network.

Not affiliated with or endorsed by Analog Way. Product names are used only to
describe compatibility.

## Contents

| | |
|---|---|
| [docs/framing.md](docs/framing.md) | the wire format — commands, replies, terminators, errors, push |
| [docs/variable-model.md](docs/variable-model.md) | variables, indices, values, layer geometry, memories |
| [docs/midra.md](docs/midra.md) | Midra series — all 562 variables, grouped |
| [docs/livecore.md](docs/livecore.md) | LiveCore series — all 1014 variables, grouped |
| [data/](data) | the same tables as machine-readable JSON |

## At a glance

- **Transport:** TCP port 10500, one control socket, no handshake.
- **Framing:** ASCII, asymmetric — a command ends with its mnemonic, a reply
  begins with it, and a reply's last comma-separated field is the value.
- **Terminators:** Midra sends `CRLF`, LiveCore sends `LF`; the device replies
  in `CRLF` on both.
- **Push:** the device sends value updates unsolicited, so state must be read
  continuously, not just polled.
- **Errors:** a rejected command is answered `E<code>` (`E10` unknown, `E12`
  wrong index count).

## Devices

- **Midra series:** Pulse2, Eikos2, Saphyr, SmartMatriX2, QuickMatriX, QuickVu.
- **LiveCore series:** Ascender 16/32/48, NeXtage 8/16, SmartMatriX Ultra.

## Using this

Point an implementation at [framing.md](docs/framing.md) for the codec and the
per-platform tables for the variables. The JSON in [`data/`](data) can be code-
generated into a typed table; that is exactly what `openrcs` does.

The LiveCore side of this reference has been checked against device behaviour;
the Midra tables are complete but have had less exercise against hardware. Treat
per-variable ranges as strong guidance rather than a guarantee — the device is
always the final authority.

## Licence

Documentation is licensed under [CC BY 4.0](LICENSE). You may share and adapt it
with attribution.
