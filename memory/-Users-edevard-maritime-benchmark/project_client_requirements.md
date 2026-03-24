---
name: Client requirements — target metrics and entity type
description: Specific metrics and entity type from the client. Overrides the generic "~20 metrics" mentioned in early planning docs.
type: project
---

Client (Norwegian) clarified the following on 2026-03-19:

## Target Metrics (6 specific)

| Norwegian | English | Notes |
|-----------|---------|-------|
| bruttopremie | gross written premium | |
| nettopremie | net written premium | |
| utbetalte skader | paid claims | Note: "paid claims" not "loss ratio" — raw paid amount, not ratio |
| combined ratio | combined ratio | Same term in Norwegian |
| solvensmargin | solvency margin | Regulatory capital metric, different section of report than P&L metrics |
| investeringsinntekt | investment income | |

## Entity Type

Marine insurance clubs specifically:
- **P&I clubs** (Protection & Indemnity) — e.g. Gard, Skuld, Norwegian Hull Club, West of England, UK P&I
- **Hull clubs** — e.g. Norwegian Hull Club

Not general maritime insurers or commercial insurers.

## Reference Document

A reference document is expected soon from the client. It will define how metrics should be measured for consistency across clubs. This becomes a canonical reference for normalization rules.

**Why:** How to apply: When this document arrives, add it as a canonical ref in CONTEXT.md and REQUIREMENTS.md. Normalization rules (HYPO-03, Phase 3) should align with its definitions.

## Source

PDFs are uploaded manually to a Unity Catalog Volume (already in design). No web crawling needed for Phase 1 — PDFs are provided.

## Impact on Planning

- REQUIREMENTS.md metric list should be updated from "~20 metrics" to these 6 specific ones
- Gold standard annotation templates should use these 6 metric names (not the generic ones in current templates)
- `solvensmargin` may appear in a different report section (Solvency II disclosure / notes) than the P&L metrics — worth flagging in hypothesis testing
