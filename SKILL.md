---
name: manuscript-workflow
description: Build, audit, and draft journal-style scientific manuscripts from local materials, user results, and optional exemplar papers. Use when the user asks to write a manuscript, construct a paper mainline, follow a reference paper's writing pattern, generate Chinese or English LaTeX, review Results or Discussion logic, or iteratively improve a reusable manuscript workflow.
metadata:
  version: "0.1.0"
  status: local
---

# Manuscript Workflow

Use this skill for manuscript construction when the user gives broad instructions such as "根据参考文献和我的结果帮我写一篇论文", "帮我构建论文主线", "写成中文 LaTeX", "审计 Results/Discussion", or explicitly invokes `$manuscript-workflow`.

This skill is a workflow controller. It can borrow useful constraints from paper-writing, review, citation, LaTeX, and domain skills, but it must keep the user's evidence and project-specific rules as the source of truth.

## Core Rule

Do not turn a generic prompt into generic prose. First convert the request into a manuscript-specific evidence workflow:

1. What is the controlling motivation?
2. What local evidence supports each claim?
3. What is only style learned from exemplars?
4. What must be stopped, downgraded, or marked as missing?
5. What final artifact did the user ask for: audit, outline, Markdown, LaTeX, PDF, DOCX, response letter, or revision plan?

Never fabricate data, metrics, p-values, cohorts, citations, figure content, sample sizes, methods, or validation experiments.

## Scope

This is a generic manuscript workflow. Do not bake a single project's hard boundaries into the skill. Project-specific definitions, forbidden claims, preferred terms, evidence quirks, and stop rules belong in the current conversation, local materials, or a per-project profile file.

If the working directory contains any of these files, read the most relevant one before drafting:

- `manuscript_workflow_project_profile.md`
- `paper_rewriting_output/manuscript_workflow_project_profile.md`
- `paper_rewriting_output/claim_register.md`
- `paper_rewriting_output/evidence_bank.md`
- `paper_rewriting_output/writing_rationale_matrix.md`
- `paper_rewriting_output/source_map.md`

## Required Workflow

### 1. Intake and Assumptions

State concise assumptions before writing or editing:

- target type: journal, conference, report, review, thesis chapter, letter
- language and output format
- whether literature/citations are required now
- whether exemplar papers are for style only or factual support
- whether the task is draft, audit, rewrite, or final packaging

Ask only when a missing answer would change the manuscript direction. Otherwise proceed and record the assumption.

### 2. Evidence Inventory

Inspect local materials before drafting. Prefer existing result summaries, figure maps, claim registers, tables, and method logs over reading raw large objects.

Create or update a compact evidence map in the output directory when the task is substantial:

| Claim | Evidence file or source | Exact numbers or figure | Evidence level | Allowed wording |
|---|---|---|---|---|

Evidence levels:

- `established_local`: directly supported by local results
- `supported_external`: supported by external validation or citation
- `exploratory_local`: computational or discovery-only support
- `hypothesis`: mechanism or translation direction not experimentally proven
- `missing_or_conflict`: stop, ask, rerun, or explicitly mark as limitation

### 3. Motivation and Claim Register

Choose one controlling motivation. A manuscript should not read like a list of analyses.

Write a claim register before the full draft:

- primary claim: one sentence
- secondary claims: 3 to 6
- forbidden or downgraded claims
- terminology definitions that must stay consistent
- figure-to-claim mapping
- evidence gaps and stop rules

If a claim lacks evidence, downgrade the verb instead of strengthening the prose.

### 4. Section Blueprint

Draft the manuscript row by row before writing full prose. Use journal-like structure unless the user asks otherwise:

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
- References or reference placeholders
- Supplementary Notes when needed

Results should usually follow the figure order. Each Results subsection should carry one evidence action:

1. lead finding
2. cohort or input
3. method in one short phrase
4. exact quantitative result
5. figure pointer
6. boundary sentence if the claim is exploratory

### 5. Drafting Standards

For Results:

- lead with findings, not methods
- report exact sample sizes, effect sizes, p-values, and model metrics when available
- keep figure references in order
- avoid causal language for correlation, enrichment, CellChat/NicheNet, SCENIC, trajectory, drug prediction, or machine-learning signatures unless causal evidence exists
- separate cell type, cell state, gene program, signature, model, and mechanism

For Discussion:

- paragraph 1: restate the main finding and evidence ladder
- paragraph 2 to 4: interpret biological or theoretical meaning, comparing with literature only when citations are being handled
- paragraph 5: translational or practical implications
- paragraph 6: limitations tied to specific evidence weak points
- final paragraph: precise conclusion and next validation steps

For Methods:

- make analysis reproducible at the level supported by local materials
- include software versions and thresholds only when known
- if details are unavailable, write a placeholder rather than inventing them

For reference papers:

- learn structure, figure logic, rhetoric, and section rhythm
- do not import their biology, numbers, or citations as if they were user results
- cite them only when the user requests references or when background claims need support

### 6. Audit Before Final

Before final delivery, audit the draft against:

- every numerical claim has a source
- no project-specific term is mixed with a different level of biology or analysis
- no validation claim exceeds the actual design
- no mechanistic claim exceeds computational inference
- every figure caption says what the figure proves and what it does not prove
- Discussion limitations match the weakest Results claims
- output format compiles or opens when feasible

For detailed audit phrasing and section-level constraints, read `references/manuscript_quality_contract.md` when writing a full manuscript, Results, Discussion, or LaTeX output.

## Output Conventions

Default output folder for substantial work:

`paper_rewriting_output/manuscript_workflow/`

For LaTeX drafts:

- use a new filename unless the user explicitly asks to overwrite
- compile PDF when a TeX engine is available
- keep prior drafts intact
- report both `.tex` and `.pdf` paths

For iterative improvement:

- record what failed in the previous output
- update the per-project profile or claim register, not the generic skill, unless the user explicitly asks to change the skill

## Compatibility With Other Skills

Use specialized skills as subordinate helpers when available:

- `academic-paper`: formatting, abstract, citation style, output packaging
- `academic-paper-reviewer`: adversarial review and revision roadmap
- `paper-spine`: exemplar-driven paper structure and source-map discipline
- `scientific-manuscript`: biomedical journal section norms and statistical reporting

If another skill conflicts with this one, manuscript-workflow controls evidence boundaries, claim strength, and project-specific definitions. The other skill may influence format and style only.
