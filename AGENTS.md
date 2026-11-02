# AGENTS.md

## What this repo is
- Documentation-only collection of reference architectures. There is no package manifest, build, test, lint, or CI config; verification is manual.
- Content lives under topic directories: `ai/`, `analytics/`, `devops/`, `migration/`, `networking/`, `security/`, `interview-questions/`. Images go in the matching `*/images/` folder.

## Critical: line endings
- Committed blobs (`HEAD`/index) are LF, but the current working tree is CRLF. As a result, `git status` reports almost every tracked Markdown file as modified even when content is unchanged.
- Review real changes with `git diff --ignore-space-at-eol`; do not stage or commit line-ending-only churn.
- There is no `.gitattributes`. If you need a content-only diff, convert the edited file to LF rather than mass-normalizing the repo.

## Editing conventions
- `README.md` is the index. Add new docs under the matching section (some sections still have unlinked placeholder bullets), but note the index is incomplete: several existing docs are not listed.
- Links are mixed root-relative (`/ai/...`) and relative (`./ai/...`); images use paths relative to the doc (usually `./images/...`). When renaming/moving files, update every link and image reference.
- Mermaid diagrams are embedded inline using fenced `mermaid` code blocks. Ensure they still parse/render after edits.
- Most architecture docs follow: Problem Statement → Business Opportunity/Solution → Architecture/Diagrams → Technical Stack → Outcomes or Failure Modes. Match the surrounding doc's structure.
- Keep client and company names redacted, per the README's NDA/confidentiality note.

## Before finishing
- Manually verify internal links and image targets resolve, Mermaid blocks render, and `README.md` links any newly added document. (`CONTRIBUTING.md` requires these checks.)
