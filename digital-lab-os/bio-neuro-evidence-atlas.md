# Bio / Neuro Evidence Atlas

> Digital Lab OS 2026 — research evidence layer
>
> Research use only. This module intentionally does **not** convert study protocols, stimulation parameters, or investigational methods into personal-use instructions.

## Purpose

The Bio / Neuro Evidence Atlas turns a recurring stream of neuroscience, neuromodulation, cognition, pharmacology, and biological-simulation questions into a structured evidence workflow. It is designed to keep **observations, mechanistic hypotheses, trial status, and verified conclusions separate**.

## Evidence states

Every claim is assigned exactly one public state:

- **SUPPORTED** — convergent evidence suitable for a bounded claim.
- **SUGGESTIVE** — promising but incomplete, heterogeneous, or indirect evidence.
- **ONGOING** — active or not-yet-complete registered research; no outcome claim permitted.
- **CONFLICTED** — credible evidence points in materially different directions.
- **ABSTAIN** — the available evidence is insufficient to support the requested claim.

Internal model confidence, agent agreement, popularity, citation count, or mechanistic plausibility **cannot promote** a claim between states.

## Current seed: non-invasive neuromodulation and cognition

### 1. Post-stroke cognition and TMS — SUGGESTIVE

A 2024 systematic review and meta-analysis in *BMC Neurology* identified 10 randomized controlled trials with 414 participants and reported a large pooled effect on global cognitive outcomes, while also reporting high heterogeneity and non-significant findings on some specific cognitive scales. The authors called for larger, multicentre, double-blind trials.

**Evidence object**
- DOI: `10.1186/s12883-024-03726-9`
- PMID: `38969994`
- Study type: systematic review / meta-analysis of RCTs
- Atlas state: **SUGGESTIVE**
- Why not SUPPORTED: limited study count, substantial heterogeneity, and inconsistent domain-specific results.

### 2. Non-invasive neuromodulation for cognitive enhancement — SUGGESTIVE

Recent reviews describe tDCS, tACS and TMS as active research areas for modulating attention, memory and executive function, but protocol variability, target selection, subject heterogeneity and task-specific effects remain major limitations.

**Evidence object**
- DOI: `10.3390/brainsci14040354`
- PMID: `38672006`
- Study type: narrative/review evidence
- Atlas state: **SUGGESTIVE**

### 3. Emerging stimulation modalities — SUGGESTIVE / ONGOING

Reviews of transcranial focused ultrasound and other emerging techniques describe improved spatial targeting as scientifically attractive, but clinical cognitive-enhancement evidence remains early and indication-specific.

**Evidence object**
- DOI: `10.3390/brainsci14030218`
- PMID: `38539607`
- Atlas state: **SUGGESTIVE**

## Trial Radar contract

Registered trials enter the Atlas as **ONGOING** until results are posted and independently assessed. A trial registration is evidence that a study was planned or conducted; it is not evidence that the intervention worked.

For each trial, store:

```json
{
  "registry_id": "NCT...",
  "title": "...",
  "status": "RECRUITING | ACTIVE_NOT_RECRUITING | COMPLETED | ...",
  "intervention_class": "DEVICE | DRUG | BEHAVIORAL | ...",
  "population": "...",
  "primary_endpoints": ["..."],
  "results_posted": false,
  "atlas_state": "ONGOING",
  "source_url": "...",
  "retrieved_at": "ISO-8601"
}
```

Promotion from **ONGOING** requires a separate evidence object for posted results or a peer-reviewed publication.

## Mechanism Graph contract

Mechanistic evidence is stored separately from clinical outcome evidence.

```json
{
  "entity": "target / receptor / pathway / brain region / network",
  "relation": "activates | inhibits | correlates_with | projects_to | modulates",
  "object": "...",
  "evidence_type": "biochemical | imaging | electrophysiology | animal | human",
  "source_id": "DOI / PMID / database accession",
  "confidence_class": "direct | indirect | inferred",
  "claim_scope": "mechanism only"
}
```

A mechanism graph can explain **why a hypothesis is plausible**. It cannot, by itself, establish that an intervention improves cognition in humans.

## Closed-loop research architecture

The safe research architecture is deliberately synthetic at the intervention layer:

1. **Observe** — import public literature, trial registrations, datasets, and simulated signals.
2. **Model** — build causal/mechanistic hypotheses with explicit uncertainty.
3. **Simulate** — test candidate interventions only in software models or synthetic datasets.
4. **Measure** — define pre-registered metrics and negative controls.
5. **Verify** — compare model predictions against held-out public evidence.
6. **Present** — publish evidence state, provenance, uncertainty, and falsification conditions.
7. **Archive** — freeze source IDs, retrieval dates, code revision, and result hashes.

No step converts an investigational stimulation protocol into personal-use instructions.

## Example falsification-first question

> Does a stimulation-linked cognitive effect generalize beyond the exact task, population, montage/target, and outcome scale on which it was originally reported?

A strong experiment therefore attempts to reproduce the effect across at least one held-out task or dataset rather than merely optimizing the original endpoint.

## Integration with the rest of Digital Lab OS

- **OctoBrowse Research Engine** captures source snapshots, quote anchors and local research notes.
- **NexusMind Evidence Gate** assigns the public evidence state and blocks unsupported certainty.
- **Supermix Model Foundry** can generate hypotheses and classify papers, but its output remains analysis-only until verified.
- **Simulation Forge** runs synthetic neural/network models and records residuals and failure cases.
- **Portfolio Compiler** can publish the work only when the evidence bundle contains source IDs, limitations, and reproducible artefacts.

## Research quality checklist

Before a Bio / Neuro claim can be published as SUPPORTED, ask:

- Is the evidence human, animal, in-vitro, computational, or mixed?
- Was the study randomized, blinded, controlled, and adequately powered?
- Are endpoints pre-specified and clinically/cognitively meaningful?
- Are effect sizes reported with uncertainty, not only p-values?
- Is heterogeneity material?
- Does the result replicate across independent groups?
- Is the mechanism evidence direct or merely plausible?
- Are negative or null findings preserved?
- Are conflicts, retractions, and registration/result mismatches recorded?
- Can the conclusion be reproduced from the stored sources without relying on an LLM's memory?

The intended culture is simple: **mechanisms generate hypotheses; trials test interventions; verification controls claims.**
