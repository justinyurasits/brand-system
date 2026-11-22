# justinyurasits.com — Design Handoff (v4)

Approved visual design for the eight-page site. This folder is a static design prototype (HTML, one shared `styles.css`, one small `main.js`). It is a reference for the production build, not production code.

- **Pages:** `index.html`, `solutions.html`, `demos.html`, `writing.html`, `article.html`, `training.html`, `about.html`, `work-with-me.html`
- **Run locally:** `python3 -m http.server 8742` in this folder, then open `http://localhost:8742`. Opening files directly (`file://`) also works.
- **Screenshots:** `screenshots/site-v3/` (all pages) and `screenshots/site-v4/` (final Training, About, Work with me, footer). Earlier homepage rounds are kept for history.
- **Source of truth:** where this document and `justinyurasits_v2_visual_design_direction_v0.1.md` disagree (mainly color values), this document and `styles.css` win.

---

## 1. Color

All colors are CSS custom properties on `:root` in `styles.css`.

| Token | Value | Use |
|---|---|---|
| `--bg` | `#F8F5F0` | Warm Ivory page canvas |
| `--surface` | `#FFFFFF` | Cards, featured demo panel |
| `--panel` | `#F1EDE6` | Soft stone panels: capabilities bar, consulting/contact panels, notes, inset groups |
| `--ink` | `#112A42` | Deep Navy: headings, primary buttons, logo tile, card accent bars |
| `--ink-hover` | `#1E3D5C` | Primary button hover |
| `--body` | `#3D4B59` | Body text |
| `--muted` | `#5B6875` | Meta text, uppercase meta labels, notes |
| `--accent` | `#466A89` | Slate Blue: eyebrows, category labels, link underlines, focus ring |
| `--accent-strong` | `#34587A` | Link hover, placeholder labels, text on pale blue |
| `--accent-icon` | `#54789A` | Icon strokes only (not for text) |
| `--accent-pale` | `#E6EDF3` | Icon tiles, numbered steps, "Stay informed" panel |
| `--line` / `--line-strong` | `#E3DED6` / `#CFC8BC` | Hairlines / chip and secondary-button borders |
| `--code-bg` | `#0F2236` | Article code blocks |
| `--ph-from` → `--ph-to` | `#DDE7EE` → `#BFD2DF` | Placeholder media gradient |

**Contrast (WCAG 2.2 AA, all pass):** ink on ivory 13.5:1 · body 8.2:1 · muted 5.2:1 · accent 5.2:1 (5.7:1 on white) · white on ink 14.7:1. Use `--accent-icon` only for non-text strokes; it is 4.3:1 on ivory.

Badge colors: Active Build = accent on accent-pale · Prototype `#7A5E3C` · Demo on Request `#4A6A4E` · Draft/Experiment/tags = muted. All are outlined pills.

## 2. Typography

- **Inter** (400/500/600/700) is used for everything.
- **Source Serif 4 Italic** (400/600) is used only in two places: the hero emphasis (*build practical*, at 1.07em to optically match Inter Bold) and the article deck.
- Both load from Google Fonts. Self-host them in production.
- Mono: `SF Mono, ui-monospace, Menlo, Consolas`.

| Role | Size | Weight / tracking |
|---|---|---|
| Hero headline | `clamp(2.125rem, 4.4vw, 3.5rem)`, lh 1.04 | 700, −0.035em |
| Page title (inner H1) | `clamp(2.375rem, 5vw, 3.5rem)`, lh 1.05 | 700, −0.035em |
| Article H1 | `clamp(2.125rem, 4.6vw, 3.25rem)` | 700, −0.035em |
| Section title (`.section-title`, feature H2s) | `clamp(1.875rem, 3.2vw, 2.5rem)`, lh 1.1 | 700, −0.03em |
| Section header H2 (`.section-header h2`, About H2) | `clamp(1.375rem, 2.2vw, 1.75rem)` / About `clamp(1.5rem, 2.4vw, 1.875rem)` | 700, −0.025em |
| Card title (H3) | 1.25rem | 700, −0.015em |
| Lead / intro | `clamp(1.0625rem, 1.5vw, 1.1875rem)`, lh 1.65 | 400 |
| Body | 1rem–1.0625rem, lh 1.6–1.75 | 400 |
| Article prose | 1.125rem / 1.75 (mobile 1.0625rem) | 400 |
| Eyebrow (with 40px rule) | 0.75rem | 600, uppercase, 0.14em, accent |
| Category / meta labels | 0.75rem | 600, uppercase, 0.1–0.12em, accent or muted |

Headings use `text-wrap: balance`. The hero keeps its manual line breaks.

## 3. Layout & spacing

- **Container:** max 1200px. Side gutter `--gutter` = `clamp(1.25rem, 5vw, 3rem)` (20px on phones).
- **Section rhythm:** `--space-section` `clamp(4rem, 8vw, 6.5rem)` between major sections. `--space-block` `clamp(2.5rem, 5vw, 3.5rem)` between blocks within a page (Demos, Writing, Training).
- **Page intro:** top padding `clamp(2.5rem, 6vw, 4.5rem)`, no divider; the eyebrow sits 1.25rem above the H1.
- **Radii:** buttons 12px · thumbnails 10px · cards, code, notes 16px · media and large panels 24px (20px on mobile).
- **Motion:** color, border and shadow transitions only (0.18s); article rows nudge their arrow 3px. All transitions are disabled under `prefers-reduced-motion`.

## 4. Components

- **Buttons:**
  - **Primary:** navy fill, white text, min-height 48px, padding 0 1.5em, 0.9375rem/600. Hover is a lighter navy plus a soft shadow.
  - **Secondary:** transparent with a 1.5px `--line-strong` border; hover turns the border navy. Used only for LinkedIn on Work with me.
  - **Small (`.btn-sm`):** 40px tall, header only.
  - **On mobile:** buttons inside panels and cards go full width.
- **Text links** (`.text-link`, `.btn-text`): navy label with a 1.5px slate underline offset 6px and a 44px min target; hover turns slate. This is the only link style for "Explore… →"-type links.
- **Focus:** a global `:focus-visible` 2px slate outline, offset 3px. Each page has a skip link ("Skip to content" → `#main`).
- **Eyebrow:** 40px × 1.5px slate rule plus an uppercase label. Used once per page intro.
- **Cards:** white, 1px `--line` border, 16px radius (24px for class/track cards), 2rem padding. Use them only for discrete items (solution areas, demos, classes, tracks, related articles). Class and track cards carry a 4px top accent bar.
- **Panels:** `--panel` fill, no border. Used for closing CTAs, notes and inset groups. The "note on fit" uses an outline instead so it doesn't merge with the contact panel above it.
- **Lists:** check list (slate check mark) for offerings and outcomes; dash list (12px slate rule) for problem statements.
- **Definition rows:** uppercase muted label column plus value, separated by hairlines. Used for Demos metadata and Training format/prerequisites/schedule.
- **Badges/pills:** 0.6875rem uppercase, fully rounded, outlined.
- **Filter chips** (Demos, Writing): real `<button aria-pressed>` elements. Selected = navy fill. They filter by `data-tags` and announce "Showing N of M" to screen readers (`main.js`).
- **Placeholder media:** one treatment for every visual, a slate gradient with an icon, label and "replace with…" note. Aspect ratios: home features 16:10 · Solutions screenshot 4:3 · Writing cover 16:10 · About portrait 2:1. The homepage portrait uses the angled clip.

## 5. Navigation & footer

- **Header:** brand left, centered nav (Solutions · Demos · Writing · Training · About), "Work with me →" small primary button on the right, 72px tall. The current page gets a slate underline. Article pages mark Writing as the current section (`aria-current="true"`).
- **Mobile menu** (≤768px): a 44px hamburger that turns into an X, and a dropdown panel with 52px rows divided by hairlines. The current page shows in slate, with a full-width navy "Work with me →" at the bottom. It closes on outside click or Escape.
- **Footer** (identical on all pages, separate from closing CTA panels): a hairline top border and four groups.
  1. **Brand:** JY tile, name, "AI Product Leadership."
  2. **Site:** six links in two columns.
  3. **Consulting:** Enterprise AI → `work-with-me.html#enterprise` and Construction AI → `work-with-me.html#construction`.
  4. **Contact:** LinkedIn and Email.

  Group headings are small uppercase muted labels. Links are 0.875rem, at least 36px tall (44px on mobile), and the current page is bold. The layout is four columns on desktop, 2×2 at ≤1024px, and on ≤768px brand and Site span full width with Consulting and Contact side by side.

## 6. Responsive rules

| Breakpoint | Behavior |
|---|---|
| > 1024px | Full multi-column layouts |
| ≤ 1024px | The Demos featured visual and the Writing cover move above their text (16:9). The Solutions flagship stacks: intro, then screenshot (16:9), then the three steps as rows. The homepage stays two-column. Article table of contents hidden. About sections 1:2. Training class panels 50/50. Footer 2×2. Notify and private-training panels stack. |
| ≤ 768px | Hamburger menu. Everything single column. Homepage features order heading → copy → image → link. Training classes unboxed, in reading order. Work with me tracks stack. Demos metadata stacks label over value. Code blocks run edge to edge and scroll horizontally. The article diagram scrolls horizontally instead of shrinking. Full-width buttons in panels. |
| ≤ 480px | About portrait 16:10 (2:1 above this) |

Verified at 1280, 1024, 768 and 375px: no horizontal page overflow, all internal links and anchors resolve, tap targets are at least 24px (44px for navigation and footer on mobile).

## 7. Page layout patterns

- **Home:**
  - Hero: text left (11fr) and a wide 7:5 portrait right (13fr) with a diagonal left edge (SVG `clipPath` `#portrait-clip` in `index.html`). On mobile the text comes first and the portrait follows.
  - Then: capabilities band (3 items) → Solutions (image left 7fr / text 5fr) → Demos (mirrored) → Writing (intro left, three article rows right) → "Work with me" panel → footer.
- **Solutions:** page intro → Construction OS flagship (badge, title and description beside a 4:3 screenshot; then Problem / Approach / Status as three numbered columns; then a CTA) → "Applied solution areas" (three icon cards) → scope note panel.
- **Demos:** page intro → filter chips → featured build card (badges, title, description and definition rows; the placeholder diagram fills the right column) → "More builds and experiments" (2×2 cards: badges, H3, description, definition rows, link).
- **Writing:** page intro → featured article (text + 16:10 cover) → "All writing" header + filter chips → article rows (status pill, category, title, description; the whole row is clickable).
- **Article:** 200px sticky table of contents plus a 44rem reading column. Header: eyebrow + Draft pill, H1, serif-italic deck, byline. Prose has numbered and bulleted lists, a navy code block, and a bordered diagram with caption, followed by Notes and two related-article cards.
- **Training:**
  - Two class panels stacked full width. Each has the summary on the left (level label, title, Format/Prerequisites/Schedule rows, CTA and note) and details on the right (description, "What you'll leave with" checklist), split by a hairline.
  - The primary class has a navy top bar; the second has a stone bar.
  - Then "Stay informed" (pale blue), "Private company training" (stone panel with audience tags), and "More workshops planned."
- **About:** intro row with eyebrow and H1 vertically centered against a 2:1 portrait. Four sections as hairline-separated rows: H2 left (4fr), text right (7fr, max 40rem), with the first paragraph set as a larger navy lead.
- **Work with me:**
  - Two equal track cards with matching navy top bars. Rows align across both cards via CSS subgrid: header → description → "Problems I work on" (dash list) → "What working together looks like" (inset stone panel) → CTA and note. Anchors are `#enterprise` and `#construction`.
  - Below: a centered contact panel (Send an email = primary, Connect on LinkedIn = secondary) and an outlined "note on fit."

## 8. Placeholders to replace before launch

**Imagery and visuals**

| Where | Placeholder | Needs |
|---|---|---|
| Home hero (`.portrait-frame`) | Gradient portrait, angled clip | Approved headshot, landscape, safe area right of the diagonal |
| About intro (`.about-portrait-sm`) | Gradient portrait (2:1; 16:10 on phones) | Same approved headshot, cropped for a wide frame |
| Home → Solutions feature | Brown "Construction OS" gradient tile | Verified Construction OS image (16:10) |
| Home → Demos feature | CSS "Agent → Process → ✓" sketch | Real demo still or keep as an illustration (16:10) |
| Home → Writing rows | Three gradient thumbnails | Article images (4:3) or remove thumbnails |
| Solutions flagship | "Interface screenshot placeholder" | Verified Construction OS UI screenshot (4:3) |
| Demos featured | Inline SVG architecture sketch | Verified architecture diagram or screenshot |
| Writing featured | "Article cover placeholder" | Cover image (16:10) |

Do not substitute a generated or stock portrait. The concept image in `assets/` is not Justin's likeness.

**Links** (`href="#"` unless noted)

| Where | Link |
|---|---|
| Footer, all 8 pages | LinkedIn, Email |
| Work with me contact panel | "Send an email →", "Connect on LinkedIn" (the panel also shows a "placeholders — not yet published" note to remove) |
| Training "Stay informed" | "Express interest via email →" |
| Demos cards | "View methodology →", "View pipeline overview →", "View experiment notes →" |
| Writing list, items 2–6 | Point to `writing.html` (articles not written) |
| Home Writing rows (all 3) | Point to `writing.html`. Row 1 can link to `article.html` |
| Article "Related" cards (2) | Point to `writing.html` |

**Content still marked provisional:** all articles are "Draft." Training dates and tuition are "TBD," and the "$20/month" Claude Pro price should be re-checked before launch. The Construction OS featured demo is "Demo on Request" with no link.

## 9. Implementation notes

- Self-host Inter and Source Serif 4; the prototype loads them from Google Fonts.
- Training-specific CSS now lives in `styles.css`; no page has inline styles.
- The About and Work with me intros, the Writing rows and the hero clip all rely on CSS grid and subgrid, `aspect-ratio`, `:has()` (Writing row focus ring) and `clip-path: url()`. All are supported in current evergreen browsers.
- Filters in `main.js` are progressive: without JS, all items show.
