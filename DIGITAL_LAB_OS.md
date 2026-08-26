# Digital Lab OS 2026

> Turn the archive into a lab. Turn the lab into proof.

## Purpose

Digital Lab OS is a personal R&D operating system for connecting local-first AI, browser research, simulations, technical art, automation, evidence, benchmarking, portfolio work, and archived experiments into one disciplined workflow.

The system is designed around a recurring question: **What do we know, how do we know it, and what is the next falsifiable step?**

## Core loop

1. **Explore** — collect ideas, references, hypotheses, unusual mechanisms, source pages, code, datasets and questions.
2. **Build** — turn the idea into a prototype, simulation, browser experiment, model, tool or visual.
3. **Measure** — attach metrics, benchmarks, profiling, tests, screenshots, model outputs and reproducible observations.
4. **Verify** — classify each claim as verified, analysis-only, speculative or abstained; record provenance and limits.
5. **Present** — generate a clean case study, visual explanation, demo and concise public summary.
6. **Archive** — preserve versions, failed attempts, receipts, notes, snapshots and lessons without letting old experiments dominate the professional front door.

## Major subsystems

### 1. NexusMind Evidence Gate
A trust boundary inspired by the Nexus/Supermix architecture.

Every candidate result passes through an evidence object:

```json
{
  "claim": "...",
  "status": "verified | analysis_only | speculative | abstained",
  "evidence_class": "deterministic | benchmark | source-backed | heuristic | anecdotal",
  "provenance": [],
  "limitations": [],
  "reproduction": [],
  "confidence_is_correctness": false
}
```

Rules:
- Internal confidence never becomes correctness by itself.
- Consensus among agents is not verification.
- A receipt records evidence; it does not create evidence.
- Unsupported closed-world questions fail closed.
- If verification is possible, recompute independently.
- If a claim cannot be grounded, expose the limitation instead of fabricating certainty.

### 2. Supermix Model Foundry
A local-first model experimentation area for small-model deployment, ONNX, WebGPU/WebNN, routing, curriculum design and benchmark diagnostics.

Tracks:
- model/version lineage
- dataset recipe
- packing strategy
- repeated-procedure vs diverse-knowledge curriculum balance
- generated exact-match benchmarks
- checkpoint selection rationale
- inference provider/fallback path
- memory footprint and throughput
- failure localisation

A core training lesson is encoded as a design rule: **optimise the corpus for the capability you are trying to teach, not for an abstract notion of dataset uniqueness.**

### 3. OctoBrowse Research Engine
A privacy-first research surface combining:
- readable-page extraction
- deterministic local extractive summaries
- quote anchors with prefix/exact/suffix relocation
- research notes
- named workspaces
- offline snapshots with provenance manifests
- frecency-ranked history
- bounded unified search
- extension permission inspection
- public-suffix-aware site boundaries

Remote content is always treated as data, never as authority.

### 4. Simulation Forge
A home for interactive scientific and engineering experiments:
- gears and drivetrains
- motor/gearbox efficiency
- biological systems
- neuroscience-inspired visualisations
- DNA/helix experiments
- physical systems
- tile/card/game systems
- procedural environments

Each simulation should expose assumptions, units, editable parameters and measurable outputs.

### 5. 3D / Technical Art Lab
Rebuild visibility around modelling, materials, UV workflows, environment work, props and browser-based 3D tools.

Every case study should show:
- problem
- reference / constraints
- modelling approach
- topology/UV/material decisions
- technical challenge
- final render or realtime result
- what changed after critique

### 6. Toolsmith Bench
Practical utilities such as AutoClicker, file tools, registry experiments, browser utilities and small desktop apps.

Portfolio rule: describe legitimate engineering value precisely. Avoid framing that makes a useful automation or testing tool look like abuseware.

### 7. Claim Observatory
A reusable inspection surface for products, articles, videos, scientific claims and AI outputs.

For any claim, capture:
- literal claim
- source
- evidence type
- independent corroboration
- marketing language
- uncertainty
- mechanism vs demonstrated outcome
- date/freshness
- decision impact

This subsystem reflects repeated investigations into supplement marketing, research chemicals, engineering specifications, product listings, AI consciousness claims and software metadata.

### 8. Portfolio Compiler
Transforms internal evidence into public-facing proof.

Input:
- project manifest
- screenshots
- benchmarks
- changelog
- tests
- architecture diagram
- lessons learned

Output:
- 30-second summary
- case-study page
- README section
- short demo script
- portfolio card
- evidence appendix

The archive stays available, but the homepage contains only the strongest proof.

## Project object

Every project can be represented as:

```yaml
id: project-slug
title: Project title
status: active
category: ai | browser | simulation | 3d | utility | archive
problem: What problem is being explored?
hypothesis: What is expected to work?
constraints: []
artifacts: []
metrics: []
claims: []
receipts: []
failures: []
lessons: []
next_experiments: []
public_summary: ""
```

## Evidence ladder

| Level | Meaning | Example |
|---|---|---|
| E0 | Idea | mechanism or concept only |
| E1 | Prototype | works in one demonstration |
| E2 | Repeatable | reproduces locally |
| E3 | Measured | benchmark/profile/test attached |
| E4 | Independently checked | verifier or independent method agrees |
| E5 | Public proof | reproducible case study and artefacts |

No project is penalised for being E0/E1; the level simply states what kind of claim is justified.

## The Idea Reactor

When the lab receives a new idea, generate five transformations:

- **Mechanise it** — what physical system or engineering analogy clarifies it?
- **Localise it** — what can run entirely on-device?
- **Visualise it** — what interactive view would make the invisible state understandable?
- **Verify it** — what test could prove or falsify the central claim?
- **Productise it** — what is the smallest useful version another person could understand in 60 seconds?

Then select one experiment using a score:

`priority = novelty × learning_value × demonstrability × feasibility × verification_strength`

The score is a planning heuristic, never correctness confidence.

## Suggested flagship integration

### Project: Kai Lab Observatory

A desktop/browser control room combining:
- local Supermix inference
- Nexus evidence states
- OctoBrowse research workspaces
- simulation cards
- project metrics
- provenance receipts
- 3D previews
- portfolio publishing queue

Main interface:

**Left:** project graph and workspaces  
**Centre:** active experiment / visualisation  
**Right:** evidence inspector  
**Bottom:** benchmark + provenance timeline

A user should be able to select any project and immediately answer:
1. What is it?
2. What is running locally?
3. What evidence exists?
4. What failed?
5. What is the next experiment?
6. What can safely be claimed publicly?

## Non-negotiable design principles

- Local-first where practical.
- Graceful fallback rather than fake capability.
- Bounded work rather than unbounded background loops.
- Deterministic output where verification matters.
- Provenance attached to research artefacts.
- Explicit trust boundaries.
- Honest abstention.
- Experiments preserved, but isolated from production surfaces.
- Performance costs visible.
- Privacy-sensitive data minimised.
- No score is called confidence unless it truly represents calibrated correctness probability.

## First build milestones

### Milestone A — Manifest + evidence engine
Create project manifests and evidence receipts. Import Supermix, NexusMind, OctoBrowse, AutoClicker, simulations and 3D projects.

### Milestone B — Observatory UI
Build the project graph, evidence inspector, active experiment panel and provenance timeline.

### Milestone C — Local AI router
Integrate ONNX/WebGPU/WebNN/WASM capability detection and expose actual fallback decisions to the UI.

### Milestone D — Research workspace
Connect page extraction, quote anchors, deterministic summarisation, notes, snapshots and source provenance.

### Milestone E — Portfolio compiler
Generate project cards and case-study drafts only from evidence stored in manifests.

### Milestone F — Public Digital Lab
Publish a polished root portfolio with `/projects`, `/lab`, `/3d`, and `/archive` separated cleanly.

## Success criteria

The project succeeds when a stranger can open one flagship project and see not just **what was built**, but **why it was built, what evidence supports it, where it failed, and exactly what would be tested next**.

That is the central identity of Digital Lab OS: experimental creativity with an evidence spine.
