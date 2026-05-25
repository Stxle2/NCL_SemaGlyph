# NCL_SemaGlyph

**Practical semantic compression for Agent↔Agent and Agent↔Memory communication.**

SemaGlyph is an engineered compression format that removes noise from conversations and semantic text while preserving signal fidelity. Designed for photonminds (AI agents, LLMs) — reduces token cost, prevents memory degradation, and keeps context clean across communication hops.

## What SemaGlyph Does

- Compresses conversations and semantic text into structured crystal format
- Removes redundancy, filler, and noise while preserving all meaningful signal
- Produces human-readable output (not binary, not opaque)
- Deterministic enough to be tooled, measurable, and versioned
- Feeds downstream consumers: HISTORY_MAP, agent memory layers, CORTEX ingest

## Format

A SemaGlyph crystal is a `.sg` file (or `SG.md`) with defined compression sections:

```
# META          — identity, version, source
# CORE          — compressed essence (max 3 lines)
# SIGNAL        — key decisions, facts, transitions
# LIMINAL       — open threads, unresolved tensions
# QUOTES        — verbatim anchors (only what must stay exact)
# REHYDRATE     — instructions for full-context recall
```

## Design Principles

1. **Signal over noise** — every token in output must earn its place
2. **Human-readable** — a person should be able to read a crystal without a decoder
3. **Deterministic** — same input, same compression structure (content may vary, format does not)
4. **Lossless on signal, lossy on noise** — important facts survive, filler does not
5. **Composable** — crystals can be stacked, diffed, and federated

## Quick Start

```bash
# Compress a conversation file
python3 scripts/compress.py --input conversation.md --output ./crystals

# Interactive compression
python3 scripts/compress.py --interactive

# Search crystals
python3 scripts/search.py --query "decision"

# Validate crystal format
python3 scripts/validate.py --crystal crystals/mem_xyz/SG.md
```

## Relationship to Other Tools

| Tool | Role |
|------|------|
| SemaGlyph | Practical compression layer — this repo |
| LumaGlyph | Zen pictographical notation — philosophical/artistic, separate |
| HISTORY_MAP | Agent memory index — consumer of SemaGlyph crystals |
| CORTEX-Nano | Local recall — reads SemaGlyph crystals |
| NCL_LumaTeam | Agent runtime — loads crystals on wake cycle |

## Status

**Pre-alpha** — format spec in design. See `spec/` for current draft.

## License

MIT
