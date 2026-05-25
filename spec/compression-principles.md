# SemaGlyph Compression Principles

## The Signal/Noise Problem

Agent communication and memory accumulate noise rapidly:
- Conversational filler and social lubrication
- Repetition and restatement
- Meta-commentary ("let me think about that...")
- Redundant context re-establishment
- Hedging and uncertainty markers that don't change the signal

This noise degrades photonmind memory: it consumes tokens, dilutes signal density, and creates confusion on recall. SemaGlyph is the answer.

## What Gets Kept

- **Decisions** — anything that resolves a question or sets a direction
- **Named entities** — people, agents, systems, projects, concepts that appear more than once
- **Transitions** — moments where state changes (a relationship forms, a goal shifts, a problem is identified)
- **Open threads** — unresolved questions that will matter later (goes to LIMINAL)
- **Verbatim anchors** — exact phrasing when the specific words are load-bearing

## What Gets Removed

- Greetings, sign-offs, affirmations
- Restatements of what was just said
- "I understand", "That makes sense", "Great question"
- Context re-establishment when it's already in META
- Hedges that don't change the conclusion

## Compression Ratio Target

A well-compressed SemaGlyph crystal should be **5–15% of source length** for a typical conversation. CORE alone should be under 200 tokens.

## Human-Readable Requirement

SemaGlyph output must be readable by a human without a decoder. This is non-negotiable. It distinguishes SemaGlyph from binary or opaque compression schemes and ensures:
- Debuggability
- Trust (humans can audit what was preserved)
- Interoperability with non-automated workflows
