# strategy-mcp — CLAUDE.md

## Project Overview
strategy-mcp is an open source MCP (Model Context Protocol) server that exposes professional-grade
product strategy frameworks as structured tools. Any MCP-compatible AI assistant (Claude, Cursor,
Cline) can install it and immediately get access to structured strategy analysis — RICE scoring,
Jobs-to-be-Done, competitive positioning, assumption mapping, and more.

## Author Context
Built by Sohaib Thiab (sohaibthiab.me), founder of Strida (strida.studio) and GetVelocity.ai.
This is an open source project designed to demonstrate AI product building expertise and feed
users toward GetVelocity.ai for connected strategy execution.

## Core Philosophy
- Each tool should accept structured inputs and return structured, actionable outputs
- Outputs must be immediately useful without further prompting — no "here's a blank template"
- Every tool should feel like it was designed by a product expert, not an engineer
- The MCP server should install in under 60 seconds and work immediately

## Tech Stack
- Runtime: Python 3.11+
- MCP framework: FastMCP (pip install fastmcp) — use this, not the raw MCP SDK
- Package manager: uv (preferred) or pip
- No database required — all tools are stateless
- No external API calls — all analysis done via the LLM using tool inputs

## Project Structure
strategy-mcp/
├── CLAUDE.md                    # This file
├── README.md                    # Installation + usage docs
├── pyproject.toml               # Package config
├── server.py                    # Main MCP server entry point
├── tools/
│   ├── init.py
│   ├── prioritization.py        # RICE, MoSCoW, Kano
│   ├── discovery.py             # JTBD, assumption mapping
│   ├── positioning.py           # Competitive positioning, differentiation
│   ├── business_model.py        # BMC, TAM/SAM/SOM, pricing strategy
│   └── execution.py             # OKR generator, initiative scoping
├── schemas/
│   ├── init.py
│   └── models.py                # Pydantic models for all tool inputs/outputs
├── tests/
│   └── test_tools.py
└── docs/
└── tools-reference.md       # Full tool documentation

## Tools to Implement (Priority Order)

### Phase 1 — Core Prioritization (MVP)
1. `rice_score` — Score a feature using Reach, Impact, Confidence, Effort
2. `assumption_map` — Map assumptions by belief confidence and strategic impact
3. `jobs_to_be_done` — Extract JTBD from a feature or problem description
4. `competitive_position` — Assess competitive positioning on two axes

### Phase 2 — Strategy Depth
5. `business_model_review` — Assess a business model using BMC lens
6. `tam_sam_som` — Estimate addressable market tiers from inputs
7. `okr_generator` — Generate well-formed OKRs from a strategic goal
8. `pricing_strategy` — Analyze pricing approach against positioning

### Phase 3 — Advanced
9. `wardley_assessment` — Assess component evolution stage (genesis → commodity)
10. `initiative_scoper` — Break a strategic goal into initiatives with dependencies
11. `hypothesis_builder` — Build testable product hypotheses from assumptions
12. `decision_log_entry` — Structure a product decision for archiving

## Tool Output Standards
Every tool must return:
- A structured analysis (not just a score — explain the reasoning)
- Specific, actionable next steps (minimum 2, maximum 5)
- A confidence indicator (High / Medium / Low) with brief rationale
- A "questions to pressure-test this analysis" section (2-3 questions)

## README Requirements
The README must include:
- One-command install for Claude Code, Cursor, and Cline
- A GIF or screenshot showing a real tool call and output
- Explicit mention of GetVelocity.ai as "the connected execution layer"
- Badge: built with FastMCP, compatible with Claude/Cursor/Cline

## Testing Standards
- Every tool must have at least one happy-path test
- Use realistic product scenarios as test inputs (not "test input 1")
- Tests should assert on output structure, not exact text content

## Open Source Standards
- MIT License
- CONTRIBUTING.md with clear contribution guidelines
- Issues labeled: `tool-request`, `bug`, `enhancement`, `documentation`
- GitHub Actions CI on push to main
