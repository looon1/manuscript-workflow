# Manuscript Quality Contract

Read this file when writing or auditing a full manuscript, Results section, Discussion section, LaTeX draft, or figure legends.

## Claim Strength Ladder

Use the weakest verb that is still scientifically useful.

| Evidence | Allowed verbs | Avoid |
|---|---|---|
| direct experiment or direct local result | shows, demonstrates, identifies, quantifies | proves causality unless causal design exists |
| single-cell or bulk association | associates with, is enriched in, is higher in, supports | drives, mediates, causes |
| machine-learning signature without locked independent validation | nominates, yields an exploratory signature, is bulk-supported | validates a predictor, clinical model, diagnostic tool |
| CellChat, NicheNet, ligand-receptor inference | suggests a candidate axis, prioritizes a communication route | confirms communication, proves signaling |
| SCENIC, regulon, TF-target inference | prioritizes candidate regulators | identifies master regulators |
| trajectory or pseudotime | suggests a state continuum, orders cells along a transcriptional trajectory | proves differentiation, establishes time course |
| drug prediction or repurposing | proposes a testable hypothesis | recommends therapy, identifies treatment |

## Results Section Contract

Each Results subsection must answer one question:

1. What was tested?
2. What data or cells/samples were used?
3. What was found?
4. What exact numbers support it?
5. Which figure shows it?
6. What is the boundary of interpretation?

Preferred paragraph pattern:

1. Finding sentence: "We found that..."
2. Evidence sentence: include n, metric, p-value, AUC, overlap, odds ratio, or enrichment term.
3. Interpretation sentence: explain the biological or analytical meaning.
4. Boundary sentence when needed: "This supports..., but does not establish..."

Do not write Results as a methods log. Avoid sequences like "First we ran X, then we ran Y" unless the workflow itself is the result.

## Discussion Section Contract

Discussion should not repeat Results in the same order with softer wording. It should build interpretation.

Recommended structure:

1. Main finding and evidence ladder.
2. Biological or conceptual interpretation of the central state/mechanism/model.
3. Cross-platform or external-support interpretation.
4. Mechanistic hypotheses and how they should be tested.
5. Translational implications or clinical relevance.
6. Limitations, matched to specific evidence weak points.
7. Concluding model and next steps.

Limitations must be concrete. Prefer:

- "The final signature used validation/test expression direction during gene locking, so it should be considered exploratory."
- "Trajectory analysis orders transcriptional states but does not prove differentiation."

Avoid:

- "More studies are needed."
- "Sample size was limited." without saying which result is affected.

## Introduction Contract

Use four movements:

1. Clinical or field problem.
2. Why existing approaches are insufficient.
3. What conceptual gap this study addresses.
4. What this study does, without over-reporting all results.

Do not start with a list of tools. Methods should motivate the question, not replace it.

## Abstract Contract

Structured abstracts should contain:

- Background: one knowledge gap.
- Methods: core design and data layers.
- Results: 3 to 5 exact findings with numbers.
- Conclusion: one calibrated take-home claim.

The conclusion cannot contain a stronger claim than the Results. If the signature is exploratory in Results, it must be exploratory in the abstract.

## Figure Legend Contract

Every main figure legend should include:

- figure title as a finding, not a file description
- what panels collectively test
- key analysis inputs
- key metrics or statistics when space allows
- interpretation boundary for computational inference

Avoid legends that only say "Workflow of analysis" or "Heatmap and UMAP".

## Methods Contract

Methods must be reproducible but not invented.

Include when known:

- dataset accession or local dataset name
- inclusion/exclusion criteria
- sample/cell counts
- normalization and integration methods
- clustering or model parameters
- thresholds for DEG, enrichment, or model selection
- statistical tests and multiple-testing correction
- software versions

If a detail is missing, write a placeholder such as `[software version to be added]` rather than guessing.

## Evidence Conflict Handling

Stop or mark explicitly when:

- two files report different denominators for the same analysis set
- a figure and table disagree
- a user term conflicts with a local annotation table
- a claimed independent validation reused information from validation/test data
- a mechanism is supported only by computational inference
- a reference paper supports style but not the user's specific result

When conflicts exist, write:

1. the two conflicting values
2. which sections are affected
3. the safest wording now
4. what rerun or metadata is needed to resolve it

## Final Delivery Check

Before final answer:

- verify that the requested artifact exists
- compile LaTeX when possible
- report unresolved evidence gaps
- keep previous drafts intact unless overwrite was requested
- tell the user how to invoke or refine the workflow next time
