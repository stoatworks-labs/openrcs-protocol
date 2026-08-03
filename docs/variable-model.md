# Variable model

Everything the device exposes — settings, status, and actions — is a
**variable**. A variable has:

- a **mnemonic**: the token used on the wire, normally 5 characters
  (`<2-letter subsystem><3-char parameter>`), with a few 1-character specials;
- a **name**: the symbolic identifier, e.g. `TBAR`;
- a **group**: the subsystem it belongs to, e.g. `GRP_TAKE_CONTROL`;
- an **index shape** (`dims`): the size of each index axis, outermost first;
- an integer **range** (`min`…`max`) and a **default**;
- **access**: read/write, or read-only for status variables.

The request and reply mnemonics are identical except for a few debug/identify
specials (see below).

## Indices

`dims` gives the addressable range of each index. A variable with
`dims = [8, 24]` is addressed as `screen, layer` where `screen` is `0…7` and
`layer` is `0…23`. A variable with no dims takes no indices. Sending the wrong
number of indices returns `E12`.

Common axes on LiveCore: **screen** `0…7`, **layer** `0…23`, **input** `0…23`,
**plug** `0…5`, **memory slot** `0…143`, **still slot** `0…100`.

## Values

Values are integers within `min`…`max`. Some are plain quantities, some are
booleans (`0…1`), and some are enumerations whose numeric codes map to named
options. A few maxima reach `4294967295` (full 32-bit) and some index bounds
reach into the millions, so hold values in at least 32-bit signed and index
bounds in unsigned 32-bit.

### Actions

Action variables are writes whose value triggers behaviour rather than storing
state — for example a memory `SAVE` or a `TAKE`. Writing the documented value
performs the action; the device typically reports related state changes back.

## Layer geometry

Layer position and size are carried by the `PRESET` group (`PR*`), indexed by
`screen, context, layer`:

- `PRpoh` / `PRpov` — the layer **centre**, in screen pixels, **biased by
  +32768**. A centred full-screen 1080p layer reads `33728, 33308`
  (`32768 + 960, 540`). Pixel position is therefore `value − 32768`; the bias
  lets a layer's centre move off-screen (negative) in either direction.
- `PRsih` / `PRsiv` — the layer **size** in screen pixels.
- `PRalp` — opacity, `0…256` (256 = fully opaque).

The `context` axis selects the program vs preview buffer; edits are typically
made to the preview buffer and moved to program with a take.

## Memories

Two memory systems store and recall arrangements:

- **Screen memories** (`PRESET_MEMORIES`, `PM*`) — per-screen presets, 144
  slots. Save with `PMscf` (source screen), `PMmet` (target slot), then `PMsav`;
  recall with `PMloa`, or recall-and-take with `PMlot`.
- **Master memories** (`MASTER_PRESET_MEMORIES`, `PS*`) — full-device presets
  across all screens, 144 slots. `PSmet` selects the slot, `PSsav` saves,
  `PSloa` / `PSlot` recall / recall-and-take; `PSval` reports which slots hold a
  memory.

## Mnemonic prefixes

Midra subsystem prefixes: `SY` system, `IT` LAN, `CT` control, `DF` device
flags, `DI` device info, `SB` standby, `VE` version, `IN` input, `IS` input
signal, `IE` input settings, `SM` settings memories, `PI`/`PR`/`PU`/`PM`
presets, `GC` global & take control, `OU`/`OC` output, `VO` video out,
`SC`/`SG` screen, `SE` soft edge, `EI`/`EO` EDID, `AU` audio, `PS`/`PC` still &
capture, `OS` OSD, `RT` clock, `TE` temperature, `FA` fan. LiveCore shares most
of these and adds `SP` simple presets, `ML`/`MM` monitoring, `SL` stills
library, `PS` master memories, and others.

## Identify specials

A few 1-character mnemonics identify the device and differ between request and
reply:

| Send | Name | Reply mnemonic |
|---|---|---|
| `?` | DEV | `DEV` |
| `!` | DEV_PLATFORM | `PDEV` |
| `*` | READY | `*` |

On Midra there are additionally `@` (`ADBG`) and `>` (`DDBG`) debug specials.

## Full reference

- [Midra series — all 562 variables](midra.md)
- [LiveCore series — all 1014 variables](livecore.md)

Machine-readable tables are in [`../data/`](../data): each entry carries its
mnemonic, reply mnemonic, name, group, dims, min/max/default and read-only flag.
