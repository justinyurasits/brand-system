# Construction OS — sub-brand

**Sheet:** BRAND-003
**Issued:** 2026-11-19
**Revision:** 04
**Base:** BRAND-002 (`../../BRAND_SYSTEM.md`) rev 15

This file adds Construction OS identity to the base system: the mark, the product names and glyphs, and the document registers. Every other rule — color, type, lines, primitives, composition, prohibitions — comes from `BRAND_SYSTEM.md`, and where the two disagree the base wins. Change this file the same way: add the treatment with its reasoning, increment the revision, then implement.

---

## 1. Wordmark

**Construction OS**, in sentence case, Archivo 600. Never set "OS" apart in caps, another color, or a block. The live lockup — mark, 10px gap, 17px wordmark — is in `cos-header.css` (`.cos-logo`).

---

## 2. The mark

Two opposed corner brackets around a centred plate, drawn on a 100×100 grid: polyline `16,54 16,16 54,16` and `84,46 84,84 46,84`, stroke 11, around a 32×32 plate at (34,34). The bracket is the line; the plate is the change mark. Shown at 22px as the eyebrow mark.

**Color.** The plate uses `--c-mark` and is fixed regardless of surface — it is not a change indicator and does not follow `--change` (base §4). Brackets take the surface foreground.

**Lockup and use**
- Clear space: one plate width (32/100 of the mark's height) on all four sides.
- Minimum sizes: mark alone 16px; lockup with a 15px wordmark.
- Single color: drop the plate, keep the two brackets.
- Don't scale linearly — strokes are optically corrected by size. At 16px use the two-bracket form.
- No rounded container, app-icon tile, gradient, or shadow behind the mark (base §10).

---

## 3. Product wordmarks

The four product names — Construction Intelligence, Document Workbench, Project Intelligence, Operations Automation — may be set in capitals: Archivo 600, 13px, 0.1em tracking, `text-transform: uppercase`. This is the sub-brand use of the base §3 exception. They function as identifiers, not labels. Status text under a wordmark is plain text, never a chip, box, or pill.

---

## 4. Product glyphs

The four 40×40 glyphs draw on the mark's 100×100 grid and take the mark's vocabulary, not its outline. They are companions to the mark, not geometric reductions of it, and they are a documented family — not an icon set (base §10).

**Grid and terminals:** 100-unit grid, orthogonal strokes, butt caps, mitred corners, no curves — as the mark.

**Stroke hierarchy:** the mark's single 11-unit stroke splits into two weights — 9 (primary, = the bracket) and 5 (secondary, = reference/datum). At 40px these render at 3.6px and 2px; do not scale linearly to other sizes.

**Plate role:** where a glyph shows a change or exception, that one stroke takes `--c-mark` / `--c-mark-lift` (the plate's color role). Only Project Intelligence and Operations Automation carry a delta.

Per glyph:
- **Construction Intelligence:** 5-unit datum on the centre axis (y=50, the mark's axis of symmetry); two 9-unit paths converge on it from y=20/80.
- **Document Workbench:** 9-unit sheet `14,26` 52×60; behind it a 5-unit offset corner `30,14 86,14 86,72` — the one direct quotation of a mark bracket.
- **Project Intelligence:** 5-unit frame `6,18` 88×64; 9-unit baseline and three bars rising 14/26/38 units; the tallest bar is the delta.
- **Operations Automation:** three 9-unit segments on y=28, three 5-unit drops, 9-unit baseline on y=74 as the delta.

**Color:** primary and secondary strokes take the row's foreground on dark rows; on light rows primary is warm black (`--c-ink`), secondary warm graphite (`--c-graphite`). The delta is `--c-mark` on light rows and `--c-mark-lift` on dark rows.

---

## 5. Registers

Construction OS documents use the base format (`PREFIX-NNN`, `REV NN`, ISO dates — base §6) with these prefixes:

| Prefix | Document |
|---|---|
| `CASE` | Case studies |
| `AOS` | Operational architecture assessments |
| `SOW` | Statements of work and proposals |
| `SPEC` | Operational architecture specifications (Phase 1 deliverable) |
| `FN` | Field notes — LinkedIn carousels, short posts |

The register itself lives in the project that issues the documents (the website keeps it in `/content/register.json`).

---

## 6. Files

| File | What it is |
|---|---|
| `cos-header.css`, `cos-footer.css`, `cos-nav.js` | Site header, footer and nav (the `SiteNav` primitive) |
| `cos-brand-reference.html` | Visual reference page |
| `svg/cos-mark.svg` | The mark per §2, 22px |
| `svg/cos-mark-sm.svg` | Two-bracket form for 16px and single color |
| `svg/glyph-*.svg` | The four product glyphs per §4, 40px |

**Using the SVGs.** Strokes read `--glyph-p`, `--glyph-s` and `--glyph-delta`, and the plate reads `--c-mark`. Inline in a page, set those per row or surface (dark rows: `--glyph-p` and `--glyph-s` white, `--glyph-delta` `--c-mark-lift`). Loaded as an image, they fall back to the light-surface colors: primary `currentColor`, secondary graphite, delta and plate `#692524`.

**Known gaps, to fix in follow-up changes:**
- `svg/icon-custom-solutions.svg` is the Purpose-Built Systems icon, used on `products/custom-solutions.html`. It isn't part of the §4 glyph family and still uses retired colors (`#111111`, steel `#476776`). Decide whether Purpose-Built Systems is a fifth product with its own glyph, then redraw or retire it.

---

## 7. Change control

| Rev | Date | Change |
|---|---|---|
| 01 | 2026-11-19 | Split from BRAND_SYSTEM.md rev 13: mark (§10), product wordmarks (§3), product glyphs (§10), registers (§6). Wordmark and lockup rules kept from the retired `CONSTRUCTION-OS-BRAND-KIT.md`, with clear space restated for the 32-unit plate. That file's palette, stroke table and benefits-band spec predate base rev 08 and were dropped. |
| 02 | 2026-11-19 | `svg/cos-mark.svg` redrawn to §2 (stroke 11, 32×32 plate at 34,34, `--c-mark`); retired steel and revision-red fallbacks removed. `svg/cos-mark-sm.svg` unchanged in geometry, embedded C2PA metadata stripped. Four retired benefits-band `svg/icon-*.svg` replaced by `svg/glyph-*.svg`, taken from the website home page and matching §4. `icon-custom-solutions.svg` kept (still in use) and listed as a gap. |
| 03 | 2026-11-19 | `cos-header.css` brought to base rev 15. CTA hover was the retired `--c-steel` (no longer defined, so the hover had no fill); it now follows base §7 interactive states — ink fill inverts to outline, with a 1.5px border at rest and a 2px focus ring. `.cos-nav__marker` moved from monospace to Archivo annotation style with tabular figures (base §10). `.cos-nav__group-label` uppercase and steel removed: sentence case, annotation tracking, `--fg-muted` (base §3). Known gap for the marker removed. |
| 04 | 2026-11-19 | `cos-footer.css` brought to the current palette. Every hard-coded color (retired ink `#111111`, graphite `#5F6466`, line `#B8B9B5`, white) replaced by role tokens (`--fg`, `--fg-muted`, `--rule-*`, `--surface`), so the footer follows its surface class. Contact-email hover was retired steel; it now follows base §7 interactive states (rev 15): a 1px `--fg` underline that steps to 1.5px. Title block values moved from monospace to Archivo small with tabular figures (base §7 TitleBlock), and the product-list markers to Archivo annotation style (base §10). |
