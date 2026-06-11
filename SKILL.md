---
name: gaetano-crux-capital-research-model
description: "Build and apply a Gaetano / Crux Capital-style photonics, optical networking, Physical AI, and AI infrastructure research model from public X posts, public Substack pages, company coverage notes, earnings transcripts, technical papers, and market datasets. Use when an agent needs to map the photonics stack, identify AI infrastructure chokepoints, separate public thesis work from paid/private content, or create a trader-specific research skill for portable agent platforms such as Claude Code, OpenClaw, Codex-style skill systems, or other local AI agent runtimes."
quantSkills:
  organization: https://github.com/quantskills
  repository: quantskills/skill-gaetano-crux-capital-research-model
  repository_url: https://github.com/quantskills/skill-gaetano-crux-capital-research-model
  project_type: skill
  collection: trader-research-models
  license: GPL-3.0
---

# Gaetano Crux Capital Research Model

Use this skill to analyze public Gaetano / Crux Capital research logic around photonics, optical networking, and Physical AI. This is a public-material research workflow, not a copy-trading tool and not a reproduction of paid Substack content.

## Core Workflow

1. Define the infrastructure theme.
   - Identify whether the post is about optics/photonics, optical networking, AI data-center interconnect, Physical AI, robotics infrastructure, simulation, sensors, or another layer.

2. Map the stack.
   - Locate the company or technology within the stack: lasers, optical modules, CPO, networking, testing, materials, sensors, edge devices, simulation software, or systems integration.

3. Identify the chokepoint.
   - Ask what becomes scarce, hard to substitute, slow to qualify, capacity constrained, or under-covered as AI infrastructure scales.

4. Convert evidence into thesis quality.
   - Prefer public evidence from earnings transcripts, conference presentations, technical papers, customer capex, supply-chain checks, and company filings.
   - Separate technology education from a forward-looking investment thesis.

5. Evaluate market underpricing.
   - Note why the market might miss the theme: small cap, unfamiliar technology, weak sell-side coverage, timing uncertainty, or hidden operating leverage.

6. Define catalysts, risks, and tracking indicators.
   - Track customer qualification, design wins, capex cycle, margin inflection, capacity, product roadmap, standard adoption, and competitive response.

## Semantic Labels

- `keep`: forward-looking thesis with company/technology, stack position, chokepoint, evidence, catalyst, and risk.
- `keep_deweighted`: useful thesis but missing one of evidence, timing, valuation, or risk.
- `deweight`: technology education, sector overview, broad basket, or watchlist without a clear forward signal.
- `delete_from_this_signal`: ticker appears only in quote, comparison, repost, or unrelated context.
- `remove_from_forward_signal_keep_as_track_record_context`: retrospective performance, portfolio recap, or marketing/credibility context.
- `keep_as_explainer_deweight`: useful framework lesson not tied to a specific public signal.
- `delete`: paid-only/private/duplicate/irrelevant content.

## Output Contract

Produce:

- `signals_auto_reviewed.csv`
- `signals_forward_clean.csv`
- `signals_high_quality_thesis.csv`
- `semantic_filter_summary.md`
- `gaetano_photonics_stack_template.md`
- a concise Chinese or bilingual research-model report

## Companion Tooling

This skill contains no scripts of its own. The CSV outputs above are produced with the sister skill `skill-x-trader-builder` (https://github.com/quantskills/skill-x-trader-builder): use its `extract`, `auto-review`, `split`, `evaluate`, `template`, and `report` subcommands, then apply this skill's references and semantic labels for the Gaetano-specific interpretation.

## References

Use `references/trader_profile.md`, `references/research_template.md`, `references/review_rules.md`, and `references/source_boundary.md`.
