# brand-system

<!-- standard: design/_template/repo/CLAUDE.md v1.5
     Sections 1–6 are the standard: copy them unchanged, filling in only the <angle brackets>.
     Section 7 is this repository's own. To change a standard rule here, say so under
     "Overrides" in section 7, with the reason. -->

## 1. What this is

Justin's reusable brand and design system: base rules, tokens and components in
`BRAND_SYSTEM.md`, and sub-brands under `brands/` (Construction OS first). Sites, apps,
decks and documents consume it.
Status: active.

## 2. Design

The design docs for this repository are in the `design` repository, cloned next to this
one, at `../design/<project>/<component>/`. Pull it before planning. In a git worktree,
`../design` means next to the main checkout, not next to the worktree.

Before proposing work, read in this order (skip any the project doesn't have yet):

1. `../design/<project>/brief.md`: why it exists and for whom
2. `../design/<project>/product-spec.md`: what the product must do, by capability ID
3. `../design/<project>/architecture.md` and `principles.md`: how the parts fit, and
   the rules every design decision follows
4. `../design/<project>/<component>/brief.md` and `spec.md`: who this component is for,
   and what it must do
5. `../design/<project>/<component>/design.md`: how it works, and the decision log
6. `../design/<project>/<component>/<slice>-design.md`: the build design for the slice
   the issue belongs to
7. `../design/<project>/<component>/plan.md`: the milestones still ahead

- **Design leads, code follows.** If the work needs a change to what the product does,
  to a requirement or to the architecture, stop and propose the change. Once Justin
  approves it, make it in the Claude Doc (synced files) or in a pull request in `design`
  (repo-authored files), and build against it after it's merged. Never put a design
  change in this repository's pull request, and don't build ahead of the design.
- **When the design is silent, ask.** Don't improvise behavior, copy or scope.
- **When the design and this repository disagree, say so.** Don't guess which is right.
- A synced design file starts with a header naming its Claude Doc. If the two differ,
  the Claude Doc is current.

## 3. How work happens

- **The issue is the plan.** Work only from a GitHub issue, and read it first
  (`gh issue view <N>`). The issue authorizes the work; the spec and design constrain
  how it's done. If they conflict, stop and say so. With no issue, write the work up as
  a proposed issue and wait.
- One issue, one branch, one pull request. Branch name: `issue-<N>-<short-description>`.
- Anything outside the issue gets a new issue. Don't widen the scope.
- Never commit to `main`. Never merge: Justin reviews and merges.

## 4. Checks

- Run the checks listed in section 7 before opening a pull request, and paste the
  results into it.
- A failure is never ignored. Either the change is wrong or the check is; say which.
- Never change an expected result to make a check pass. Report the mismatch and stop.

## 5. Every pull request

Fill in `.github/pull_request_template.md`:

- `Closes #<N>`, and what changed and why, in plain English.
- How each acceptance criterion in the issue was checked.
- **Decisions (proposed):** choices made while coding: the decision, the options, why,
  and what would change it. Merging the pull request approves them. That covers
  implementation choices inside the issue only. A decision that changes a requirement,
  the architecture, a security boundary or documented behavior is a design change
  (section 2): stop and propose it instead.
- **Build notes:** what you did, what broke, what it taught.

## 6. Roll-up, ask before, never

**Roll-up.** Ask "Roll up to design?" when a pull request you opened is merged, when an
issue or milestone is done, and about every ten turns of work since you last asked.

- On yes: collect Decisions and Build notes from pull requests merged since the last
  roll-up (the latest "Roll-up:" line in the component's `build-log.md`). Propose
  decisions for the `design.md` decision log and findings for `build-log.md`, ending with
  the line `Roll-up: <repo> #<first>–#<last>`. For files synced from Claude Docs, add
  them as suggestions in the Claude Doc if you have the Docs connector; otherwise give
  Justin the text to paste. For repo-authored files, open a pull request in `design`.
- Every roll-up also checks for drift. For each synced file in the component and its
  project, compare the `rev` in its `sync-manifest.yaml` with the Claude Doc's current
  revision, and offer a sync pull request in `design` for any doc that has moved ahead.
  Without the Docs connector, list those docs and their links from `../design/DOCS.md`
  and ask Justin to check them.
- On no: don't ask again for another ten turns.
- Nothing enters the design record until Justin approves it.

**Ask before:**

- adding a dependency
- changing a prompt, tool description, rubric, or anything else that changes what a
  model decides
- anything not in the issue

**Never:**

- read, print or edit `.env`. Secrets live only there; `.env.example` holds key names only
- commit secrets, API keys or real customer data
- rewrite git history

## 7. This repository

- **Layout:**
  - `BRAND_SYSTEM.md`: the base rules (BRAND-002). The authority on how everything looks.
  - `tokens.css`, `brand.css`: the base as CSS. `components.html`: rendered reference.
  - `brands/<name>/BRAND.md`: a sub-brand's identity only (mark, product names and
    glyphs, registers). It can't override the base.
  - `brands/construction-os/`: Construction OS, with its header, footer, nav, reference
    page and `svg/`.
- **Run:** nothing to build. Open `components.html` and
  `brands/construction-os/cos-brand-reference.html` in a browser.
- **Checks:** none automated yet. Before a pull request:
  - No retired values outside change-control rows: `grep -rnE "C43230|476776|111111|revision-lift|steel" --include=*.md --include=*.css --include=*.svg --include=*.html .`
    Change-control rows will match; anything else is a failure. Files that fail today
    are tracked as issues; don't add new ones.
  - Every changed SVG or HTML file opened in a browser on white and on ink, with a
    screenshot in the pull request.
  - The changed file's revision number incremented and its change-control row added.
- **Conventions:**
  - Change order: add the rule to the right file with its reasoning, increment its
    revision, then change CSS or SVG. Never a visual treatment that isn't written down.
  - Base or sub-brand: if every product would use it, it goes in `BRAND_SYSTEM.md`;
    if it's identity, in `brands/<name>/BRAND.md`.
  - Projects copy files from here. Change here first, then copy into the project.
- **Overrides:**
  - **Section 2 (Design).** This repository *is* the design for how things look, so it
    has no folder in `../design` and its `BRAND` files are edited here, by pull request.
    Product design docs in `../design` that need a visual rule point here.
  - **Section 6 (Roll-up).** No roll-up to `../design`. Decisions go straight into the
    change-control table of the file they change, so the record is in the same pull
    request. Ask before still applies.
