---
name: manuscript-workflow
description: Build, audit, rewrite, and package journal-style scientific manuscripts from local materials, user results, and optional exemplar papers. Use when the user asks to write a manuscript, construct a paper mainline, follow or learn from reference papers or other writing skills, generate Chinese or English LaTeX/PDF, review Results or Discussion logic, run a reviewer-style critique, or iteratively improve a reusable manuscript workflow.
metadata:
  version: "0.2.0"
  status: local
  upstream_inspiration:
    - PaperSpine
    - academic-research-skills
---

# Manuscript Workflow

Use this skill when the user gives a broad writing request such as "根据参考文献和我的结果帮我写一篇论文", "帮我构建论文主线", "写成中文 LaTeX", "审计 Results/Discussion", or explicitly invokes `$manuscript-workflow`.

This skill is an evidence-first manuscript controller. It may learn workflow patterns from strong skills, paper examples, journal instructions, and prior project artifacts, but the manuscript's factual content must come from the user's materials and verified sources.

## Design Boundary

This workflow is an original local packaging layer. It was designed after studying public manuscript-writing workflows, especially motivation-led paper construction, staged academic writing pipelines, claim verification, reviewer-style critique, and LaTeX packaging. Do not copy upstream wording or file contents into user deliverables. Extract transferable process patterns and restate them in the current project's own terms.

For source and license notes, read `references/external_pattern_synthesis.md` and `ATTRIBUTION.md` when updating this skill or publishing it.

## Core Principle

Do not turn a generic prompt into generic prose. Convert the request into a traceable manuscript workflow:

1. Define the paper's controlling motivation.
2. Build a material passport from local files, references, figures, and drafts.
3. Separate evidence, style learning, and missing data.
4. Register every major claim with allowed wording.
5. Draft section-by-section from the claim register.
6. Run an audit before final packaging.

Never fabricate data, metrics, p-values, cohorts, citations, figures, methods, validation experiments, or biological mechanisms.

## Generic Skill, Project-Specific Profile

Do not bake one project's hard boundaries into this generic skill. Project-specific definitions, forbidden claims, preferred terms, evidence quirks, and stop rules belong in:

- `manuscript_workflow_project_profile.md`
- `paper_rewriting_output/manuscript_workflow_project_profile.md`
- a user message in the current conversation

If a project profile exists, read it before drafting or auditing.

## Routing

Choose the lightest workflow that satisfies the request.

| User request | Route |
|---|---|
| "What is the story/mainline?" | `audit-mainline` |
| "Write a full paper from these materials" | `build-from-materials` |
| "Rewrite this draft using my results/reference paper" | `rewrite-existing` |
| "Only Results/Discussion" | `section-draft` |
| "Review this manuscript" | `review-gate` |
| "Make LaTeX/PDF/DOCX" | `final-package` |
| "Improve the workflow/skill" | `workflow-update` |

For unclear requests, state assumptions and proceed when the missing answer would not change the route. Ask only when the manuscript direction, output format, or evidence boundary would change.

## Standard Artifacts

For substantial work, write artifacts under:

`paper_rewriting_output/manuscript_workflow/`

Recommended artifact set:

- `material_passport.md`: source inventory, authority level, freshness, access gaps
- `external_pattern_synthesis.md`: what was learned from exemplars or other skills
- `motivation_options.md` or `confirmed_motivation.md`
- `evidence_map.md`
- `claim_register.md`
- `section_blueprint.md`
- `writing_rationale_matrix.md`
- `draft_audit.md`
- final `.tex` and compiled `.pdf` when requested

For small requests, create only the artifacts needed.

## Workflow

### 1. Intake

Record concise assumptions:

- target type: journal, conference, report, review, thesis chapter, letter
- output language
- output format
- whether citations are required now
- whether reference papers teach style only or support factual claims
- whether the task is build, rewrite, audit, review, or package

### 2. Material Passport

Inspect local materials before drafting. Prefer summaries, result tables, figure manifests, claim registers, and method logs over raw large objects.

Classify each source:

| Level | Meaning |
|---|---|
| `authoritative_local` | current user-approved results or project profile |
| `supporting_local` | scripts, manifests, figures, older summaries |
| `external_evidence` | cited literature or public datasets |
| `style_exemplar` | paper or skill used for structure/rhetoric only |
| `historical_or_stale` | older project outputs that require re-audit |
| `missing_or_conflict` | must stop, downgrade, or define a rerun |

If two materials disagree, do not smooth over the conflict. Write the values, affected sections, safest wording, and needed rerun.

### 3. Motivation Thread

Choose one controlling motivation before drafting. A paper should not read like a folder inventory.

If the motivation is unclear, produce 2-4 real options. Each option must change the paper's title, Introduction gap, Results order, or Discussion interpretation. Stop for user selection when the options would lead to different papers.

When motivation is clear, write `confirmed_motivation.md` with:

- one-sentence red thread
- field problem
- specific gap
- design response
- primary evidence
- prioritized claims
- claims to avoid
- section consequences

### 4. Evidence Map And Claim Register

Create an evidence map:

| Claim | Evidence source | Exact numbers or figure | Evidence level | Allowed wording |
|---|---|---|---|---|

Evidence levels:

- `established_local`
- `supported_external`
- `exploratory_local`
- `hypothesis`
- `missing_or_conflict`

Then create a claim register:

- primary claim
- 3-6 secondary claims
- forbidden or downgraded claims
- terminology definitions
- figure-to-claim mapping
- stop rules

If a claim lacks evidence, downgrade the verb instead of strengthening the prose.

### 5. External Pattern Learning

When the user asks to follow a paper or existing skill, learn process patterns rather than copying text:

- target-scene structure
- intake and checkpoint design
- section order
- paragraph jobs
- figure logic
- audit gates
- output packaging
- failure modes

Write the learned pattern in the current project's vocabulary. Do not reproduce upstream templates unless license and attribution explicitly allow it and the user wants vendored content.

### 6. Section Blueprint

Create section-level blueprints before full prose:

- Title
- Abstract
- Introduction
- Results
- Discussion
- Materials and Methods
- Data and Code Availability
- Author Contributions
- Conflicts of Interest
- Acknowledgements
- References or placeholders
- Supplementary Notes when needed

Each Results subsection should carry one evidence action:

1. lead finding
2. data or cohort
3. method in one short phrase
4. exact quantitative result
5. figure pointer
6. interpretation boundary

Use `references/manuscript_quality_contract.md` for section-level standards.

### 7. Draft

For Results:

- lead with findings, not methods
- report exact sample sizes, effect sizes, p-values, overlaps, or model metrics when available
- keep figures in order
- separate cell type, state, gene programme, signature, model, mechanism, and drug hypothesis
- avoid causal verbs unless causal evidence exists

For Discussion:

- answer the Introduction promise
- interpret the evidence ladder
- compare with literature only when citations are being handled
- name specific limitations tied to evidence gaps
- close with testable next steps

For Methods:

- describe only documented procedures
- include versions and thresholds only when known
- use `[to be added]` placeholders instead of inventing details

### 8. Review Gate

Before final packaging, run a compact reviewer-style audit. Use at least these roles:

- Method reviewer: design, denominators, statistics, leakage, reproducibility
- Domain reviewer: biological or field interpretation, terminology, literature fit
- Argument reviewer: motivation, Results order, Discussion closure
- Skeptical reviewer: strongest counterclaim, overreach, missing validation

Synthesize findings into:

- blocking issues
- major revisions
- minor revisions
- safe-to-proceed notes

Do not edit the manuscript during review unless the user asks for revision.

### 9. Final Package

For LaTeX:

- create a new filename unless overwrite is explicit
- compile PDF when a TeX engine is available
- keep prior drafts intact
- report `.tex`, `.pdf`, and audit paths

For DOCX or other formats, use available local tooling and verify the output opens or exists.

## Audit Checklist

Before final answer, verify:

- every numerical claim has a source
- every figure caption states what the figure supports and what it does not prove
- external papers or skills are not used as evidence for local results
- validation language matches study design
- mechanisms are not stronger than the data
- unresolved conflicts are in limitations or a stop-rule note
- final artifact exists and compiles when feasible

## Compatibility With Other Skills

Use specialized skills as subordinate helpers when useful:

- `academic-paper`: citation style, abstract, final formatting
- `academic-paper-reviewer`: multi-perspective critique
- `paper-spine`: exemplar-driven motivation and rationale-matrix discipline
- `scientific-manuscript`: biomedical journal norms and statistical reporting

If another skill conflicts with this one, `manuscript-workflow` controls evidence boundaries, claim strength, and project-specific definitions. Other skills may influence style, format, or review perspectives only.
