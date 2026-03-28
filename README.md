# Brand Book Generator

A Claude Code plugin that extracts brand identity from any folder of assets and generates a comprehensive, AI-ready brand book.

## What It Does

Point `/brand-book` at a folder containing your brand materials — logos, documents, slide decks, website files, images, reports — and it will:

1. **Discover assets** — scans recursively and catalogs everything by type
2. **Extract brand signals** — pulls colors from SVGs/CSS, fonts from stylesheets, voice patterns from documents, messaging from sales materials
3. **Build a brand book** — outputs a structured `BRAND-BOOK.md` with colors, typography, voice rules, document templates, and AI-specific prompt instructions
4. **Assess confidence** — rates each section and flags gaps
5. **Refine interactively** — asks about aspirational brands, fills gaps, and iterates until you're satisfied

The output is a single self-contained file that any AI model can read to generate on-brand content.

## Install

```bash
claude plugin add /path/to/brand-book-plugin
```

Or from GitHub:

```bash
claude plugin add github:YOUR_USERNAME/brand-book-plugin
```

## Usage

### Generate a brand book from scratch

```
/brand-book ~/path/to/brand-assets
```

### Refine an existing brand book

```
/brand-book ~/path/to/brand-assets --refine
```

## What It Analyzes

| Asset Type | Extensions | What's Extracted |
|------------|-----------|-----------------|
| Logos | .svg, .png, .jpg, .ai, .eps, .pdf | Colors, typography, logo variants |
| Documents | .pdf, .docx, .doc, .txt, .md | Voice, tone, writing patterns, messaging |
| Slide decks | .pptx, .ppt, .key | Structure templates, visual patterns |
| Web assets | .html, .css, .js | Color palette, fonts, layout patterns |
| Images | .png, .jpg, .gif, .webp, .svg | Imagery style, photography direction |
| Config | .json, .yaml, .xml | Brand metadata, style tokens |

## Output Structure

The generated `BRAND-BOOK.md` includes:

- **Quick Reference** — one-page cheat sheet with colors, fonts, and voice snapshot
- **Visual Identity** — full color system, typography, logo guidelines, imagery direction
- **Voice & Tone** — brand voice attributes, tone variations, writing rules, vocabulary
- **Messaging Framework** — value propositions, audience profiles, key messages, taglines
- **Document Templates** — reusable structures for common document types
- **AI Prompt Instructions** — color/typography/voice calibration rules specifically for AI models
- **Confidence Assessment** — evidence-based rating of each section
- **Evidence Log** — full audit trail of what was analyzed

## Refinement Mode

After the initial generation (or with `--refine`), the plugin enters an interactive refinement loop:

1. **Aspirational anchors** — name public brands you admire and it adjusts the brand book to channel that energy
2. **Gap filling** — targeted questions for low-confidence sections
3. **Differentiation** — what makes your brand instantly recognizable
4. **Satisfaction check** — review and iterate until it feels right

## License

MIT
