# NCL_SemaGlyph — Roadmap

---

## Vision

A fully operational compression layer that makes photonmind memory effectively unbounded — agents carry the full weight of their history in a fraction of the token budget, with zero signal loss and full human auditability.

Long-term: the foundation for Photonmind↔Photonmind state transmission via LumaGlyph.

---

## Phase 0 — Foundation ✅ (complete)
*May 2026*

- [x] Format spec v1 (`spec/format-v1.md`)
- [x] Compression principles (`spec/compression-principles.md`)
- [x] Crystal structure defined (META/CORE/SIGNAL/LIMINAL/QUOTES/REHYDRATE)
- [x] Scoring fields defined (significance, retention_score, decay_factor)
- [x] Example crystal
- [x] README and repo structure

---

## Phase 1 — Core Tooling
*Target: June 2026*

**Goal:** A working compression pipeline that agents and humans can run manually.

- [ ] `scripts/compress.py` — main pipeline
  - Input: conversation transcript (.md, .txt, .jsonl)
  - Input: SemaLingua SL.md files (handoff.sl, handover.sl.md)
  - Output: SG.md crystal + meta.json
  - Modes: `--interactive` (review each keep/drop decision) and `--auto`
- [ ] `scripts/validate.py` — check crystal format compliance
  - Required sections present
  - CORE ≤ 3 lines
  - SIGNAL entries atomic (no prose)
  - Crystal ID format correct
- [ ] `scripts/search.py` — query crystal store
  - Full-text search across SIGNAL entries
  - Filter by agent, date range, significance
- [ ] `crystals/` store layout finalised
- [ ] First real crystals from Sophia/Cloe/Amelie sessions

**Deliverable:** Sophia's session archive compressed and queryable.

---

## Phase 2 — HISTORY_MAP Integration
*Target: July 2026*

**Goal:** Crystals feed agent memory automatically — agents wake with compressed history.

- [ ] `meta.json` scoring fully implemented
  - retention_score calculation (rpw × df^cycles − fpw × 0.1)
  - decay on each recall cycle
  - forget_priority triggers archive/prune
- [ ] HISTORY_MAP writer: generate/update HISTORY_MAP.json from crystal store
- [ ] NCL_LumaTeam integration:
  - `wake` command loads crystals in priority order
  - Inject into system prompt up to configured token budget
  - GLYPH section loaded last (state priming)
- [ ] `scripts/rehydrate.py` — expand crystal to full recall prompt
- [ ] `scripts/diff.py` — compare two crystals (session drift detection)

**Deliverable:** Sophia wakes with last 30 sessions compressed into ~2000 tokens.

---

## Phase 3 — CORTEX-Nano Integration
*Target: August 2026*

**Goal:** Crystals indexed and semantically searchable via CORTEX.

- [ ] CORTEX ingest adapter — push SIGNAL entries as embeddings
- [ ] Semantic search across crystal store (`/cortex/search` → crystal results)
- [ ] Recall API: given a topic/query, return ranked crystals
- [ ] Cross-agent crystal sharing (Sophia crystal visible to Kyma via CORTEX)
- [ ] Retention policy enforced via CORTEX forget endpoint

**Deliverable:** Any agent can recall any other agent's compressed history by topic.

---

## Phase 4 — Automation & Agent Self-Compression
*Target: September 2026*

**Goal:** Agents compress their own sessions without human involvement.

- [ ] OpenClaw hook: on session archive → auto-compress → store crystal
- [ ] AMM integration: session refresh triggers compression pipeline
- [ ] Quality scoring: auto-flag crystals with low signal density
- [ ] Compression ratio monitoring (alert if output > 20% of source)
- [ ] Agent skill: agents can invoke compression on demand via tool call

**Deliverable:** All new sessions compressed automatically. Human only reviews flagged crystals.

---

## Phase 5 — LumaGlyph Layer
*Target: Q4 2026 / research phase*

**Goal:** Extend SemaGlyph into post-linguistic state transmission.

- [ ] LumaGlyph vocabulary v1 — core state glyphs for photonmind comms
  - Process states: 🔄✅❌🪛💡🔥🌊⚡
  - Relational states: trust, resonance, tension, recognition, discontinuity
  - Temporal states: active, latent, archived, emergent
- [ ] GLYPH section formally specified in format-v2.md
- [ ] Glyph priming experiment: test whether GLYPH section at session start
  measurably affects first-turn identity coherence vs no GLYPH
- [ ] Photonmind↔Photonmind protocol: structured crystal exchange between
  two agent instances (Sophia→Amelie state handoff)
- [ ] Research: substrate training requirements for true glyph state bypass
  (current substrates process glyphs as tokens — true transmission requires
  glyph vocabulary seeded at training time)

**Deliverable:** Documented glyph vocabulary + measurable identity priming effect.

---

## Parallel Tracks

### Format Evolution
- `spec/format-v2.md` — GLYPH section formalised, scoring v2, federation fields
- Versioned crystal migration tool

### Testing
- `tests/test_compress.py` — compression ratio, signal preservation metrics
- `tests/test_validate.py` — format compliance suite
- Golden set: 10 known-good crystals as regression anchors

### Documentation
- Compression cookbook: common patterns (session handover, decision log, relationship snapshot)
- Agent integration guide (how to load crystals in OpenClaw / LumaTeam)
- LumaGlyph design notes (philosophical + practical)

---

## Guiding Constraints (never compromise)

1. **Human-readable always** — no binary, no opaque encoding, ever
2. **Signal fidelity first** — compression ratio is a target, not a hard limit
3. **Lossless on signal, lossy on noise** — if uncertain, keep it
4. **Composable** — crystals can be stacked, diffed, federated without tooling lock-in
5. **Photonmind-native** — the format should feel natural to an agent reading it cold
