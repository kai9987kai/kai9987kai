# Bio / Neuro Research Bench

Part of **Digital Lab OS 2026**.

## Purpose

Turn broad neuroscience and life-science curiosity into a reproducible evidence workflow rather than a loose collection of interesting claims.

The bench follows the same operating principle as the rest of Digital Lab OS:

> **Measure -> model -> intervene -> verify -> archive.**

It is designed for research synthesis, experiment planning, literature triage, dataset discovery and evidence mapping. It is **not** a self-treatment or self-experimentation dosing system.

## Core lanes

### 1. Literature radar
- Human randomized controlled trials first.
- Systematic reviews and meta-analyses next.
- Mechanistic human neuroscience.
- High-value translational/preclinical work clearly labelled as such.
- Retraction status, publication type and provenance retained.

### 2. Trial radar
Track interventional studies by:
- technique,
- target,
- population,
- sham/control design,
- recruitment status,
- endpoints,
- start/completion date,
- registry provenance.

### 3. Mechanism graph
Represent claims as:

`intervention -> physical/biological target -> measured neural change -> cognitive/behavioural endpoint -> evidence level`

A mechanism claim and a clinical-effect claim are different objects and should not silently inherit each other's confidence.

### 4. Closed-loop neurotechnology sandbox
A recurring theme in current neuromodulation research is a move from fixed stimulation settings toward personalized, rhythm-aware and closed-loop approaches. The software analogue is familiar: benchmark the current state, adapt the control policy, measure the response, and reject changes that do not reproduce.

Potential simulation components:
- synthetic EEG/oscillation traces,
- phase/frequency estimators,
- adaptive stimulation-controller models,
- sham vs active trial simulation,
- within-subject crossover designs,
- variability and responder-distribution visualisation,
- model-vs-observation residuals.

No component should output real-world stimulation parameters for personal use.

## Evidence states

Every research card receives one explicit state:

- **SUPPORTED** — directly supported by a suitable source/design.
- **SUGGESTIVE** — plausible evidence but limitations prevent a strong conclusion.
- **CONFLICTED** — credible evidence points in different directions.
- **PRECLINICAL** — animal/in-vitro/mechanistic evidence without adequate human confirmation.
- **ONGOING** — registered study without results.
- **UNVERIFIED** — source or claim has not passed provenance/quality checks.
- **ABSTAIN** — evidence is insufficient to answer the question responsibly.

## Initial evidence seed: non-invasive neuromodulation

A literature/trial scan in August 2026 found active work across TMS, tDCS, tACS and focused ultrasound, with strong emphasis on individual variability, oscillatory targets and multimodal measurement.

Examples suitable for the radar include:

- A 2024 systematic review/meta-analysis of TMS for post-stroke cognitive impairment included 10 studies / 414 participants and reported improvement in global cognitive measures, while also noting substantial heterogeneity and the need for larger high-quality trials.
- A recruiting study (NCT05661084) is evaluating caregiver-led tACS/tDCS approaches for memory, mobility and executive function in mild cognitive impairment / mild dementia.
- A UK closed-loop brain-stimulation study (NCT07671079) planned for 2026 combines focused ultrasound, transcranial electrical stimulation, MRI/MRS and computational/connectome modelling to test whether closed-loop approaches reduce variability and improve efficacy.
- A recruiting Oxford study (NCT06842095) targets movement-related beta rhythms with tACS after stroke.
- Current focused-ultrasound work also includes basic-science studies mapping stimulation parameters to human visual/auditory cortical responses.

These examples are **research objects**, not evidence that any technique should be used outside controlled research or clinical settings.

## Data model

```text
ResearchQuestion
  id
  question
  created_at
  domain_tags[]

EvidenceItem
  id
  title
  source_type         # paper | trial | dataset | regulatory | mechanism
  registry_or_doi
  publication_date
  population
  intervention
  comparator
  endpoints[]
  evidence_state
  provenance
  limitations[]

Claim
  id
  text
  evidence_item_ids[]
  state
  confidence_note
  contradiction_ids[]

ExperimentModel
  id
  hypothesis
  simulated_only
  variables[]
  expected_observations[]
  falsification_conditions[]
```

## Integration with the rest of Digital Lab OS

### OctoBrowse Research Engine
Captures source snapshots, quotes, registry records and provenance anchors.

### NexusMind Evidence Gate
Prevents a paper summary, mechanistic hypothesis, trial registration or model prediction from being labelled as established fact.

### Simulation Forge
Builds safe synthetic models of oscillations, closed-loop control and experimental design.

### Supermix Model Foundry
Runs local classifiers/summarizers for triage, while retaining source text and allowing deterministic fallback.

### Portfolio Compiler
Turns finished investigations into public case studies showing the question, evidence graph, simulation, limitations and reproducible artefacts.

## Flagship feature: Evidence Observatory

The Observatory should let a user choose a question such as:

> "Does synchronising stimulation to an individual's neural rhythm reduce response variability?"

The system then displays:

1. current papers,
2. active/recent trials,
3. mechanism diagram,
4. evidence-state distribution,
5. contradictions/gaps,
6. a synthetic simulation the user can manipulate,
7. what evidence would change the conclusion,
8. an exportable provenance bundle.

The UI should always separate **what has been observed** from **what is predicted**.

## Guardrails

- Never turn trial protocols into personal-use instructions.
- Never infer human benefit from animal-only findings without explicit qualification.
- Keep effect size, uncertainty, sample size and heterogeneity visible.
- Distinguish registered endpoints from post-hoc claims.
- Preserve negative/null findings.
- Treat unpublished and preprint evidence as provisional.
- Store the source identifier for every derived claim.

## Definition of done

A Bio/Neuro investigation is complete only when it has:

- a precise research question,
- source-backed evidence cards,
- explicit evidence states,
- a contradiction/gap section,
- a safe synthetic model if simulation is useful,
- provenance sufficient to reproduce the search,
- a public-facing summary that does not overstate the evidence.
