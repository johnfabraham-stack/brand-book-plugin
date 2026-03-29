# Brand Book Generator

A Claude Code plugin that extracts brand identity from any folder of real assets — logos, documents, slide decks, proposals, websites, images — and builds a comprehensive, AI-ready brand system with interactive refinement.

Unlike tools that generate brand identities from moodboards or web scraping, this plugin analyzes your **actual brand artifacts** to discover what your brand already is, then helps you evolve it toward what you want it to become.

## What Makes This Different

| Feature | Brand Book Generator | Competitors |
|---------|---------------------|-------------|
| **Input** | Your real folder of assets (SVGs, PDFs, DOCX, PPTX, images, CSS) | Moodboard images, company name, or manual Q&A |
| **Analysis** | Reads SVGs for hex codes, extracts text from DOCX/PPTX, scans CSS for fonts, reads images visually | Web scraping or GPT-generated suggestions |
| **Output depth** | 15+ sections: colors, typography, voice, messaging, boilerplate copy, team bios, elevator pitches, tone calibration, document templates, content decision trees | Color palette + basic guidelines |
| **Dual output** | AI-ready (BRAND-BOOK.md) + human-ready (styled HTML) | Single format |
| **Refinement** | Interactive loop: aspirational brands, gap filling, differentiation, design direction exploration | One-shot generation |
| **Evidence** | Full audit trail of every asset analyzed and what was extracted | No provenance |

## Install

```bash
claude plugin add github:johnfabraham-stack/brand-book-plugin
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

## The 5-Phase Process

### Phase 1: Asset Discovery
Scans your folder recursively and catalogs every file by type — logos, documents, slide decks, spreadsheets, web assets, images, and config files. Reports the inventory before proceeding.

### Phase 2: Brand Signal Extraction
Analyzes each asset type to pull brand signals:

- **Visual Identity** — hex colors from SVGs/CSS, font families from stylesheets, logo variants, imagery style from photographs, layout patterns from documents
- **Voice & Tone** — writing style, formality level, vocabulary patterns, point of view, sentence structure from real documents
- **Messaging** — value propositions, taglines, positioning statements, audience signals, key narratives repeated across materials
- **Document Patterns** — structure templates, header/footer patterns, naming conventions, data presentation style

### Phase 3: Brand Book Assembly
Writes a structured `BRAND-BOOK.md` optimized for AI consumption:

- **Quick Reference** — one-page cheat sheet (colors, fonts, voice snapshot, key stats)
- **Visual Identity** — full color system with usage rules, typography scale, logo guidelines, imagery direction
- **Voice & Tone** — brand voice attributes with real examples, tone variations by context, writing do/don't rules, vocabulary preferences
- **Messaging Framework** — value propositions, audience profiles, key messages, taglines
- **Document Templates** — reusable structures for proposals, articles, outreach emails, press releases
- **AI Prompt Instructions** — color/typography/voice calibration rules specifically for AI models to follow
- **Brand Foundation** — origin story, mission, vision, values, brand personality archetype
- **Boilerplate Copy Library** — short/medium/long descriptions for every entity, ready to paste
- **Team Bios** — extracted from documents with voice notes per team member
- **Real Brand Voice Examples** — gold-standard paragraphs, opening/closing lines by context, recurring phrases
- **Tone Calibration** — off-brand vs on-brand comparison pairs, tone gradient across registers
- **Elevator Pitches** — 30-second and 60-second versions
- **Content Decision Tree** — audience > context > tone lookup for AI models

### Phase 4: Confidence Assessment
Rates each section High/Medium/Low with evidence counts. Flags gaps and suggests what additional assets would strengthen weak sections.

### Phase 5: Aspirational Refinement (Interactive)
Guides you through iterative improvements:

1. **Aspirational anchors** — Name public brands you admire (e.g., "Apple's minimalism + Mailchimp's warmth") and the brand book adjusts to channel that energy
2. **Gap filling** — Targeted questions for low-confidence sections
3. **Differentiation** — What makes your brand instantly recognizable
4. **Design direction exploration** — Can generate multiple alternative visual paths for your portfolio
5. **Satisfaction check** — Review and iterate until it feels right

## What It Analyzes

| Asset Type | Extensions | What's Extracted |
|------------|-----------|-----------------|
| Logos | .svg, .png, .jpg, .ai, .eps, .pdf | Hex colors, font families, logo variants, clear space patterns |
| Documents | .pdf, .docx, .doc, .txt, .md | Voice, tone, writing patterns, messaging, boilerplate copy, bios |
| Slide decks | .pptx, .ppt, .key | Visual themes, structure templates, color palettes, content patterns |
| Web assets | .html, .css, .js | Color palette, fonts, layout patterns, design tokens |
| Images | .png, .jpg, .gif, .webp, .svg | Imagery style, photography direction, mood |
| Config | .json, .yaml, .xml | Brand metadata, style tokens, design system variables |

## Example Output

When pointed at a folder containing logos, investor decks, outreach emails, editorial articles, event proposals, and strategic documents, the plugin produced:

- A 1,200+ line AI-ready brand book with 16 sections
- A styled HTML brand guidelines page matching the actual brand aesthetic
- Three alternative design direction proposals with visual previews
- Boilerplate copy in short/medium/long variants for 6 entities
- Elevator pitches (30s and 60s) for 4 brands
- 17 recurring brand phrases cataloged with frequency and context
- 5 off-brand vs on-brand tone calibration pairs
- A content decision tree mapping audience > context > tone

## Requirements

- Claude Code CLI
- A folder containing brand assets (the more diverse the assets, the richer the output)

## License

MIT
