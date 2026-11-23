# brand-system

Justin's reusable brand and design system. One set of rules, drawn from construction
drawing conventions, for every site, app, deck and document, with sub-brands that add
their own identity on top.

**Status:** active

## What's here

| Path | What it is |
| --- | --- |
| [`BRAND_SYSTEM.md`](BRAND_SYSTEM.md) | Base rules: color, type, lines, metadata, primitives, dimensions, composition, prohibitions, rendering outside the browser |
| `tokens.css`, `brand.css` | The base as CSS custom properties and classes |
| `components.html` | Rendered component reference |
| [`brands/construction-os/`](brands/construction-os/BRAND.md) | Construction OS: mark, product glyphs, product names, document registers, header/footer/nav |
| [`brands/personal/`](brands/personal/BRAND.md) | Personal, for justinyurasits.com: an independent sub-brand with its own visual system, from the approved design handoff. `BRAND_SYSTEM.md` §1–§10 don't apply to it |

## Using it

Copy the files a project needs into it: `tokens.css` and `brand.css` for any web project,
plus the sub-brand's CSS, JS and `svg/` files. Read `BRAND_SYSTEM.md` before designing
anything new, and the sub-brand's `BRAND.md` for its identity. Change rules here first,
then copy them into the project.

[justinyurasits.com](https://github.com/justinyurasits/justinyurasits.github.io) uses it:
the live site on `main` follows the base and Construction OS, and v2, on the `v2`
branch, follows the personal sub-brand.

## Changing it

Every change comes in through a pull request. Write the rule with its reasoning,
increment the file's revision and add a change-control row, then change the CSS or SVG.
See [CLAUDE.md](CLAUDE.md).
