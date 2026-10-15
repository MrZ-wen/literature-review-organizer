---
name: literature-review-organizer
description: Organize local academic literature, assign structured tags, generate detailed reading notes, and synthesize research progress, limitations, gaps, and potential innovations.
---

# Literature Review Organizer

Use this skill when a user provides a folder of academic papers and wants to organize, tag, summarize, compare, or synthesize the literature.

## Scope

This skill is domain-agnostic. It can be used for life sciences, agriculture, medicine, engineering, materials science, environmental science, social science, and other research areas.

## Inputs

- A local folder containing PDF, EPUB, or other academic literature files
- An optional research topic
- An optional user-defined tag system
- An optional output format

If the user provides a tag taxonomy, preserve it. Otherwise create candidate tags from the literature and mark them as automatically generated and requiring review.

## Default tag dimensions

- Topic: research subjects, biological processes, materials, diseases, technologies, or theories
- Method: experimental, computational, statistical, imaging, omics, modeling, or review methods
- Object: species, cell type, tissue, material, population, dataset, or system
- Phenotype/Outcome: measured traits, endpoints, performance indicators, or outcomes
- Environment/Condition: location, time, treatment, stress, dose, temperature, or other context
- Reading status: to-read, skimmed, deep-read, data-extracted
- Research role: background, method, evidence, candidate mechanism, controversy, limitation, innovation, to-validate

Use multiple tags per dimension when justified. Do not force a paper into a category unsupported by its title, abstract, or full text.

## Workflow

1. Scan the user-specified folder and list supported literature files.
2. Preserve original files. Do not rename, move, overwrite, or delete them unless explicitly requested.
3. Extract available metadata: title, authors, year, journal or venue, DOI or identifier, abstract, keywords, research question, materials or datasets, methods, outcomes, conclusions, and limitations.
4. Assign multi-dimensional tags using the user's taxonomy or the default dimensions above.
5. Mark evidence status for important fields:
   - verified from full text;
   - extracted from abstract or metadata;
   - inferred from context;
   - requires manual review.
6. Generate a searchable literature index with one row per paper.
7. Generate a structured reading note for each paper using `references/note-template.md`.
8. Generate a theme-method-evidence matrix and a research-gap summary when the corpus is large enough to support synthesis.
9. Distinguish reported results, author interpretations, assistant inferences, and proposed research directions.
10. Before writing outside the workspace or modifying original literature files, request confirmation.

## Default outputs

- `literature_index.csv`
- `literature_index.xlsx` when spreadsheet output is requested and supported
- `reading_notes.md`
- `theme_method_evidence_matrix.csv`
- `research_gaps_and_innovations.md`

Each index row should include the file path, bibliographic metadata, all applicable tags, research question, study object, methods, major outcomes, key evidence, limitations, reading priority, relevance to the user's topic, DOI or identifier, and evidence status.

## Quality rules

- Treat a candidate gene, locus, mechanism, or causal explanation as unverified unless the paper provides functional or otherwise direct evidence.
- Do not invent DOI values, sample sizes, effect sizes, or experimental conditions. Use `not found` or `needs review`.
- Preserve the distinction between correlation, association, prediction, and causation.
- For reviews, record the scope, search period, inclusion criteria if reported, and whether claims are primary evidence or secondary synthesis.
- For single-paper summaries, include what the study proves, what it does not prove, and the most useful follow-up question.
