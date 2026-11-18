# AGENTS.md

## Repo shape
- Docs-only collection of reference architectures: no package manifest, build, test, lint, formatter, or site generator. Do not add tooling/scaffolding unless asked.
- The only automation is `.github/workflows/updates.yaml`, which runs on pushes to `main` and just checks out the repo and echoes a success message. It does not validate links, Mermaid, or Markdown.
- Content is grouped by topic: `ai/` (8 docs) and two docs each in `analytics/`, `devops/`, `interview-questions/`, `migration/`, `networking/`, and `security/`. Images live in `ai/images/`, `analytics/images/`, and `networking/images/`; the other topics have no image folders.
- Docs are standalone Markdown with no front matter. Many embed Mermaid diagrams and use doc-relative images (`./images/...`). A few still use root-relative links (e.g. `/analytics/AWS_EnterpriseDataHub.md`, `/networking/images/3_tier_aws.jpeg`), and the GCP 3-tier doc links out to Google Cloud via raw HTML.
- `LICENSE` is MIT only; the README badge reflects that.

## Critical: line endings
- Committed blobs (`HEAD`/index) are LF, but working-tree Markdown is CRLF. `git status` reports almost every tracked doc as modified even when content is unchanged.
- `AGENTS.md` itself is LF, and `security/Defense_in_depth.md` has no trailing newline. Preserve each file's existing endings rather than mass-normalizing the repo.
- Review real changes with `git diff --ignore-space-at-eol` (add `--name-only` to list them); do not stage or commit line-ending-only churn.
- There is no `.gitattributes`.

## Editing conventions
- `README.md` is the public index and now lists every tracked doc with a doc-relative link (`./topic/file.md`). Add new docs under the matching section and link them there. Planned topics with no file (formerly Databricks Unity Catalog, VPC Peering, Air-Gapped) are not listed; don't add placeholder entries.
- Prefer doc-relative links for new or edited content, and doc-relative image paths (`./images/...`). Renaming or moving a doc requires updating every reference to it and its README entry.
- The networking file is `networking/3Tier_AWS_Architecture.md`; an earlier `Achitecture` typo was fixed in commit 30b7145. Fix any remaining references to the misspelling rather than renaming the file.
- Detailed architecture docs follow: Problem Statement → Business Opportunity/Solution → Architecture/Diagrams → Technical Stack → Outcomes or Failure Modes. Match the surrounding doc's structure.
- Several docs are thin: `ai/ResponsibleAI_Architecture.md`, `migration/Bitbucket_GitHub_Migration.md`, and `security/Defense_in_depth.md` are title-only outlines, while `migration/Migration_OnPrem_Cloud.md`, the `devops/` and `networking/` docs, and `security/Least_Privilege_Access.md` are short. Expand them rather than assuming content exists; the README marks the outlines as *(draft)*, so remove that marker when a doc is fleshed out.
- Keep client and company names redacted per the README's NDA/confidentiality note; use generic roles/industries.

## Before finishing
- There are no meaningful automated checks. Manually verify every internal link and image target resolves, fenced `mermaid` blocks still render, and every doc is linked from `README.md` (`CONTRIBUTING.md` requires link and render checks).
- Use `git diff --ignore-space-at-eol -- <files>` to confirm only intended content changed.
