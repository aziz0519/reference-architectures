# AGENTS.md

## Repo shape
- Docs-only collection of reference architectures: no package manifest, build, test, lint, formatter, or CI. Do not add tooling/scaffolding unless asked.
- Content is grouped by topic: `ai/`, `analytics/`, `devops/`, `migration/`, `networking/`, `security/`, `interview-questions/`. Images live in the matching `*/images/` folder (not every topic has one).
- Docs are standalone Markdown with inline Mermaid and doc-relative images; there is no site generator or front matter.

## Critical: line endings
- Committed blobs (`HEAD`/index) are LF, but working-tree Markdown is CRLF. `git status` reports almost every tracked doc as modified even when content is unchanged.
- Review real changes with `git diff --ignore-space-at-eol` (add `--name-only` to list them); do not stage or commit line-ending-only churn.
- There is no `.gitattributes`. Preserve each file's existing endings (CRLF for docs, LF for this file) rather than mass-normalizing the repo.

## Editing conventions
- `README.md` is the public index; add new docs under the matching section. It is incomplete: several tracked docs are unlisted, and some bullets (e.g. Databricks Unity Catalog, VPC Peering, Air-Gapped) have no file yet. Do not invent links for placeholders.
- Links are mixed root-relative (`/ai/...`) and relative (`./ai/...`); images are doc-relative (`./images/...`). Renaming/moving a doc requires updating every reference and the README entry.
- Preserve the misspelled path `networking/3Tier_AWS_Achitecture.md` unless you update all references.
- Most architecture docs follow: Problem Statement → Business Opportunity/Solution → Architecture/Diagrams → Technical Stack → Outcomes or Failure Modes. Match the surrounding doc's structure.
- `ai/ResponsibleAI_Architecture.md` and `security/Defense_in_depth.md` are tracked but contain only a title; expand them rather than assuming content exists.
- Keep client and company names redacted per the README's NDA/confidentiality note; use generic roles/industries.

## Before finishing
- There are no automated checks. Manually verify every internal link and image target resolves, fenced `mermaid` blocks still render, and any new doc is linked from `README.md` (`CONTRIBUTING.md` requires these).
- Use `git diff --ignore-space-at-eol -- <files>` to confirm only intended content changed.
