# AGENTS.md — openrcs-protocol

Onboarding for LLM agents working in this repo.

## What this is

Documentation only: a reference for the TCP control protocol of Analog Way
Midra and LiveCore series video processors. The implementation that uses it is
[openrcs](https://github.com/stoatworks-labs/openrcs); this repo is the spec it
is written against.

Not affiliated with Analog Way. Device and product names appear only to state
compatibility.

## Layout

```
docs/framing.md          the wire format
docs/variable-model.md   variables, indices, geometry, memories
docs/midra.md            GENERATED — Midra variable tables
docs/livecore.md         GENERATED — LiveCore variable tables
data/*.json              the tables as machine-readable data
```

## Hard rules

- **`docs/midra.md` and `docs/livecore.md` are generated** from `data/*.json`.
  Edit the JSON (or the generator that lives with the openrcs implementation),
  never the generated Markdown by hand.
- **Documentation only** — no application code belongs here.
- **Keep it accurate to the wire.** Every claim here should match how the
  device actually behaves. If a detail is uncertain, say so rather than
  guessing.
- **Use vendor names nominatively only** — to describe compatibility, never as
  branding or in a way implying endorsement.
- **Keep the data in sync** with the `protocol/` tables in the openrcs
  repository; they are the same source of truth.
