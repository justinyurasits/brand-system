# Personal — sub-brand

**Sheet:** BRAND-004
**Issued:** 2026-11-23
**Revision:** 01
**Base:** BRAND-002 (`../../BRAND_SYSTEM.md`) rev 17, as an independent sub-brand

The visual system for justinyurasits.com, Justin's personal professional site. It's an
**independent sub-brand**: BRAND-002 §1–§10 (the drawing language) don't apply to it.
BRAND-002 §11 (rendering outside the browser), §12 (change control) and the WCAG 2.2 AA
floor do.

---

## 1. What's authoritative

The design-lab handoff Justin approved as the working visual direction on 2026-11-23:

- **[`DESIGN_HANDOFF.md`](DESIGN_HANDOFF.md)**, v4: color, type, layout, components,
  navigation and footer, responsive rules, page patterns. It's copied here verbatim.
- **[`tokens.css`](tokens.css):** the values. Its first `:root` block is the prototype's,
  verbatim. The second adds the colors §3 below and the handoff document, which the
  prototype hard-codes.
- **[`reference/`](reference/):** the eight prototype pages, `styles.css` and `main.js`,
  verbatim. They show how the components fit together. They're a reference, not
  production code: build components from the handoff and tokens, and don't copy these
  pages wholesale.
- **[`screenshots/`](screenshots/):** the v4 set (Training, About, Work with me, footer, at
  1280px and 375px), compressed to WebP.

Where the handoff and its earlier `justinyurasits_v2_visual_design_direction_v0.1.md`
disagree, the handoff and `styles.css` win; the direction doc isn't copied here.

The copies match the design-lab originals:

| File | SHA-256 |
| --- | --- |
| `DESIGN_HANDOFF.md` | `adf3b046e76a238cfa8446135e80bafb9e5502fdc66dc8d860d6e98389429d45` |
| `reference/styles.css` | `a4f8792c791cc889d94ee8ac651942ce1203d541fdf74bb44e529eb3764e095d` |
| `reference/main.js` | `3ab29b7dd8b6a50dd4db59c14fd16e36cc4f4fd6cf8941d809e7f3cf8daf66b3` |
| `reference/index.html` | `aa947d6fbad58b660f895b6042860d01af0d51535808e5b59cf478c8fa4215a2` |
| `reference/solutions.html` | `1790898d4eb2f542b240f160cceb50d7f0994a6f1ea97b85e13af9b12256654e` |
| `reference/demos.html` | `bd9899e0256b2ea3d207d08ea616ab245480775cffef0df94b1fa21caf9745f3` |
| `reference/writing.html` | `371c44c52030adcf0fb2ebc6f949027db41a9b4c50ca80badab885e0ed609c6a` |
| `reference/article.html` | `46143e8d4da2ed316b46c920df78dba808b970495c09fe185e2929a792e61db9` |
| `reference/training.html` | `f128189ce2f5444ddc5ca01f17f8b602185778006a812a85332a020a338bf7e2` |
| `reference/about.html` | `0835d2f99eb0e77d65060ced4a15187bfbbc8793bf54a5aea4b29a5b87fed9e6` |
| `reference/work-with-me.html` | `18f0dbc63557fe4754a42710ae2d6d57ffc485a93d465043cc39ea18c87cd7f8` |

The prototype's concept image (`assets/`) isn't included: it isn't Justin's likeness.

## 2. Where it applies

Every page on justinyurasits.com, including its Solutions, Construction OS and case-study
pages. Construction OS's own separate properties keep the Construction OS brand
(BRAND-003).

## 3. Status

A project's maturity is shown as a badge, using the handoff's outlined pill:

| Maturity | Badge |
| --- | --- |
| `live` | `--status-live` (`#4A6A4E`) |
| `beta` | `--accent` on `--accent-pale` (the prototype's `.badge-build`) |
| `prototype` | `--status-proto` (`#7A5E3C`) |
| `experiment`, `in-development` | `--muted` with a `--line-strong` outline (the prototype's `.badge-draft`) |

**Demo availability is text in the details row, never a badge:** "Public demo", "Demo on
request" or "No demo". The prototype's "Active Build" and "Demo on Request" badges aren't
used, and "Draft" never appears on a published page.

All four badge colors pass AA on every surface they sit on: 4.8:1 or better against
ivory, white, the pale blue and the stone panel.

## 4. Pages the handoff doesn't cover

Pages the handoff doesn't show are built **only from its documented components**: page
intro, eyebrow, cards, panels, check and dash lists, definition rows, badges, filter
chips, text links, buttons, the article reading column, and placeholder media until
real media arrives. No new color, radius, type size, shadow, motion or component.

| Page | Built from |
| --- | --- |
| Case study (`/demos/<id>/`) | Page intro with badge; definition rows; the article reading column; cards for related writing |
| Construction OS products (`/solutions/construction-os/`) | Page intro; one section per product with definition rows and badges; text links |
| Legal (`/privacy.html`, `/terms.html`) | Page intro; the article reading column |
| 404 | Page intro; a text link |
| Category and tag pages | The Writing page's "All writing" header and article rows |

A page that needs something these can't do needs a design-lab change first (§6).

## 5. Using it in a project

- **Tokens:** copy `tokens.css` into the project and record the brand-system commit it came
  from in the copy's header. The build never reads this repository.
- **Fonts:** self-host Inter (400, 500, 600, 700) and Source Serif 4 Italic (400, 600),
  with their licenses. No font CDN.
- **Components:** implement them from the handoff and the tokens, in the project's own
  framework.
- **Copy:** the prototype's text is illustrative, not approved copy. Claims come from the
  project's own sources (on justinyurasits.com, its facts register).

**Checks a consuming project runs:**
- Colors only from its tokens file, with no hex values anywhere else.
- Type sizes only from the handoff's §2 scale, defined as tokens.
- No inline styles.
- No requests to a font CDN.
- No placeholder media at launch (handoff §8).
- The handoff's §1 contrast pairs and the §3 badge colors.
- Visible focus, a skip link, and no transitions under `prefers-reduced-motion`.

## 6. Change control

A change starts in the design lab. Once Justin approves it, it lands here by pull request:
the handoff copy and its hash updated, this file's revision incremented, and a row added
below. Projects then copy the new tokens and record the new commit.

| Rev | Date | Change |
| --- | --- | --- |
| 01 | 2026-11-23 | Created from the approved design-lab handoff v4. Adds the status mapping (§3) Justin approved, with demo availability as text, and the composition rule for pages the handoff doesn't cover (§4). |
