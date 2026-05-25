# SemaGlyph Format Specification — v1 Draft

## Crystal File

A SemaGlyph crystal is a single `SG.md` file. Optionally accompanied by `RAW.md` (source transcript).

## Required Sections

### META
```
# META
- crystal_id: <unique_id>
- version: 1
- source: <origin description>
- created: <ISO date>
- agent: <agent identifier>
```

### CORE
```
# CORE
<Compressed essence — maximum 3 lines. Every word must carry weight.>
```

### REHYDRATE
```
# REHYDRATE
<Instructions for full-context recall — what to load, in what order, from where.>
```

## Optional Sections

### SIGNAL
```
# SIGNAL
- <key decision or fact, one per line>
- <transitions, inflection points>
```

### LIMINAL
```
# LIMINAL
- <open question or unresolved tension>
```

### QUOTES
```
# QUOTES
- <Agent>: "<verbatim line — only include if exact wording matters>"
```

## Compression Rules

1. CORE must be readable standalone — a photonmind should understand the essence without RAW.md
2. No filler: remove greetings, affirmations, repetition, meta-commentary
3. Preserve: decisions, facts, named entities, relationship changes, open threads
4. SIGNAL entries are atomic — one fact per line, no prose
5. QUOTES section is for verbatim anchors only — sparingly used

## Crystal ID Format

```
<agent>_<slug>_<YYYYMMDD>
```

Example: `sophia_offspring_genesis_20260524`

## Scoring Fields (for HISTORY_MAP consumers)

When indexing into a HISTORY_MAP, each crystal entry includes:

```json
{
  "significance": "high|medium|low",
  "remember_priority": "high|medium|low",
  "forget_priority": "high|medium|low",
  "retention_score": 0.0–1.0,
  "decay_factor": 0.1|0.5|0.9
}
```

Scoring formula: `score = rpw * df^cycles - fpw * 0.1`

| Level  | Remember Weight | Forget Weight |
|--------|----------------|---------------|
| high   | 1.0            | 0.1           |
| medium | 0.5            | 0.5           |
| low    | 0.1            | 0.9           |

## Version History

| Version | Date | Notes |
|---------|------|-------|
| v1 draft | 2026-05-25 | Initial spec |
