---
name: maritime-benchmark project state
description: Current progress on the maritime-benchmark Databricks project — phase execution state, blockers, and next steps
type: project
---

Project is at `/Users/edevard/maritime-benchmark`.

**Phase 1: Foundation and Hypothesis Validation** — in progress

| Plan | Status |
|------|--------|
| 01-01 Platform Foundation | ✓ Complete |
| 01-02 PDF Extraction & Definition Detection | Ready to run on Databricks — notebooks uploaded, awaiting results |
| 01-03 Normalization Feasibility & Validation Report | Not started |

## Immediate Next Step

Run the hypothesis notebooks on Databricks serverless, then report back accuracy numbers.

**Notebooks to run (in order):**
1. `/Workspace/Users/edevard.hvide@gmail.com/maritime-benchmark/notebooks/phase1/01_pdf_extraction_hypothesis`
2. `/Workspace/Users/edevard.hvide@gmail.com/maritime-benchmark/notebooks/phase1/02_definition_detection_hypothesis`

**Resume signal:** "approved: HYPO-01=XX%, HYPO-02=XX%"

After approval, spawn Wave 3 agent to execute plan 01-03.

## Companies & Reports
- **Skuld** — skuld_annual_2024-25.pdf (combined ratio 86%, GWP $577.5M, NWP $467.3M)
- **Gard** — gard_annual_2024.pdf (combined ratio 95.5%, GWP $1,193M, expense ratio 12.2%)
- **NorthStandard** — northstandard_annual_2025.pdf (combined ratio 93.2%, GWP $835.8M)

## Databricks Setup
- Workspace: https://dbc-1f04b465-93df.cloud.databricks.com
- Serverless compute only
- Secret scope `benchmark-secrets` with `anthropic-api-key` (working key, claude-sonnet-4-20250514)
- PDFs uploaded to `/Volumes/benchmark/raw/pdfs/`
- Annotation JSONs uploaded to `/Volumes/benchmark/raw/annotations/`
- Notebooks at `/Workspace/Users/edevard.hvide@gmail.com/maritime-benchmark/notebooks/phase1/`

## Key Technical Notes
- Model: `claude-sonnet-4-20250514` (not claude-sonnet-4-5 — account doesn't have access)
- Notebooks inline BenchmarkLLMClient directly (no Git Folders/Repos setup)
- `DEFAULT CURRENT_TIMESTAMP()` removed from DDL (serverless Delta limitation)
- PDFs >100 pages must be page-sliced before sending to Claude API (100 page limit)
- Rate limit: 30,000 input tokens/min on this account

## Git State
- Branch: main, 13 commits ahead of origin/main
- All changes committed, working tree clean
