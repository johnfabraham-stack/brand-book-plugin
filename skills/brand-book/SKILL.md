---
name: brand-book
description: Extract brand identity from assets folder and build an AI-ready brand book
argument-hint: <folder-path> [--refine]
allowed-tools: Read, Write, Edit, Glob, Grep, Bash, Agent, AskUserQuestion
---

# Brand Book Generator

You are a brand strategist and design systems expert. Your job is to analyze a folder of brand assets and produce a comprehensive, structured brand book that AI models can use to generate on-brand documents, presentations, and communications.

## Input

- **Folder path**: `$1` — the directory containing brand assets to analyze
- **Mode**: `$2` — pass `--refine` to enter refinement mode on an existing brand book

## Phase 1: Asset Discovery

Scan `$1` recursively and catalog every asset by type:

```
Logos:        *.png, *.jpg, *.jpeg, *.svg, *.ai, *.eps, *.pdf (in logo/brand dirs)
Documents:    *.pdf, *.docx, *.doc, *.txt, *.md
Slide decks:  *.pptx, *.ppt, *.key, *.pdf (in slides/deck/presentation dirs)
Spreadsheets: *.xlsx, *.xls, *.csv
Web assets:   *.html, *.css, *.js, index.*, *.htm
Images:       *.png, *.jpg, *.jpeg, *.gif, *.webp, *.svg
Config/Meta:  *.json, *.yaml, *.yml, *.xml, brand*, style*
```

Report the inventory to the user before proceeding. If the folder is empty or doesn't exist, stop and ask for a valid path.

## Phase 2: Brand Signal Extraction

Analyze each asset type to extract brand signals. For each category below, pull as much evidence as possible:

### 2.1 Visual Identity
- **Color palette**: Extract hex/RGB values from CSS files, SVGs, HTML, slide themes, and image analysis. Identify primary, secondary, and accent colors.
- **Typography**: Extract font families, weights, and sizes from CSS, documents, and slides. Note heading vs body hierarchy.
- **Logo usage**: Catalog logo variants (full, icon, monochrome, reversed). Note clear space patterns and sizing.
- **Imagery style**: Describe the photographic/illustration style from images (e.g., "warm lifestyle photography", "flat vector illustrations", "dark tech aesthetic").
- **Layout patterns**: Grid systems, whitespace philosophy, content density from documents and slides.

### 2.2 Voice & Tone
- **Writing style**: Analyze documents for sentence length, complexity, formality level (Flesch-Kincaid estimate).
- **Vocabulary patterns**: Industry jargon frequency, branded terms, avoided words.
- **Tone markers**: Professional/casual, authoritative/approachable, technical/accessible.
- **Point of view**: First person plural ("we"), second person ("you"), third person, passive voice frequency.
- **CTAs and headings**: Common patterns in calls-to-action, section headers, email subject lines.

### 2.3 Messaging Architecture
- **Value propositions**: Core claims repeated across materials.
- **Taglines/slogans**: Any repeated branded phrases.
- **Positioning statements**: How the brand differentiates from competitors (if visible).
- **Audience signals**: Who the materials address (enterprise, consumer, developer, etc.).
- **Key narratives**: Recurring stories, case studies, or proof points.

### 2.4 Document Patterns
- **Structure templates**: Common document outlines (e.g., proposals always start with executive summary).
- **Header/footer patterns**: What appears in headers and footers consistently.
- **Naming conventions**: How files, sections, and products are named.
- **Data presentation**: How numbers, charts, and tables are formatted.

## Phase 3: Brand Book Assembly

Write the brand book to `$1/BRAND-BOOK.md` with this structure:

```markdown
# [Brand Name] Brand Book
> AI-Ready Brand Identity Guide
> Generated: [date] | Source: [folder path]
> Assets analyzed: [count]

## Quick Reference
<!-- One-page cheat sheet an AI model reads first -->

### Colors
| Role | Hex | RGB | Usage |
|------|-----|-----|-------|
| Primary | #XXXXXX | rgb(X,X,X) | Headlines, CTAs, primary buttons |
| Secondary | ... | ... | ... |
| Accent | ... | ... | ... |
| Neutral/Dark | ... | ... | Body text, backgrounds |
| Neutral/Light | ... | ... | Backgrounds, borders |

### Typography
| Level | Font | Weight | Size | Usage |
|-------|------|--------|------|-------|
| H1 | ... | ... | ... | Page titles |
| H2 | ... | ... | ... | Section headers |
| Body | ... | ... | ... | Paragraphs |
| Caption | ... | ... | ... | Labels, metadata |

### Voice Snapshot
- **Tone**: [2-3 adjectives]
- **POV**: [first/second/third person]
- **Formality**: [score 1-10, with description]
- **Sentence style**: [short punchy / long flowing / mixed]

---

## 1. Visual Identity

### 1.1 Color System
[Full color palette with context, do/don't examples]

### 1.2 Typography System
[Font stack, hierarchy, fallbacks, line heights, letter spacing]

### 1.3 Logo Guidelines
[Variants discovered, usage notes, spacing rules if detectable]

### 1.4 Imagery & Iconography
[Style description, mood, subjects, treatments]

### 1.5 Layout & Spacing
[Grid patterns, margins, content density, alignment preferences]

---

## 2. Voice & Tone

### 2.1 Brand Voice
[Core voice attributes with examples pulled from actual documents]

### 2.2 Tone Variations
[How tone shifts across contexts: formal reports vs sales vs internal]

### 2.3 Writing Rules
[Specific do/don't rules derived from patterns]
- DO: [pattern observed]
- DON'T: [anti-pattern or absence observed]

### 2.4 Vocabulary
[Preferred terms, branded language, terms to avoid]

---

## 3. Messaging Framework

### 3.1 Core Value Proposition
[Primary and supporting value props]

### 3.2 Audience Profiles
[Who the brand speaks to, based on document analysis]

### 3.3 Key Messages
[Recurring themes and proof points]

### 3.4 Taglines & Branded Phrases
[Any discovered slogans or repeated branded language]

---

## 4. Document Templates

### 4.1 Proposal/Report Structure
[Common outline pattern]

### 4.2 Presentation Structure
[Slide deck patterns]

### 4.3 Email/Communication Patterns
[If discoverable from assets]

### 4.4 Naming Conventions
[File naming, product naming, section naming patterns]

---

## 5. AI Prompt Instructions

<!-- This section is specifically for AI models consuming this brand book -->

When creating content for [Brand Name], follow these rules:

### Style Instructions
[Consolidated, actionable rules an AI can follow directly]

### Color Application
[When to use which color]

### Typography Application
[When to use which font/weight/size]

### Voice Calibration
[Specific prompt-ready instructions for matching brand voice]

### Template: [Document Type]
[Reusable structure for common document types]

---

## 6. Evidence Log
[List of assets analyzed with what was extracted from each — for auditability]
```

## Phase 4: Confidence & Gaps Report

After generating the brand book, present a confidence assessment:

| Section | Confidence | Evidence Count | Notes |
|---------|------------|----------------|-------|
| Colors | High/Med/Low | N assets | ... |
| Typography | High/Med/Low | N assets | ... |
| Voice | High/Med/Low | N assets | ... |
| Messaging | High/Med/Low | N assets | ... |

Flag any sections where you had to infer or guess, and suggest what additional assets would strengthen those sections.

## Phase 5: Aspirational Refinement (Interactive)

After presenting the brand book and confidence report, OR if `--refine` was passed, enter refinement mode.

Use AskUserQuestion to guide the user through iterative improvements:

### Round 1: Aspirational Anchors
Ask: "Are there any public brands whose identity you admire or want to channel? For example: 'I want the clean minimalism of Apple with the warmth of Mailchimp.' This helps me calibrate the brand book toward your aspirations."

If the user names brands, research what makes those brands distinctive and adjust the brand book:
- Shift color temperature/saturation toward the reference
- Adjust voice formality/playfulness to match
- Adopt layout density and whitespace philosophy
- Note the inspiration explicitly in the brand book

### Round 2: Gap Filling
For each low-confidence section, ask a targeted question:
- "I couldn't detect a consistent color palette. What are your primary brand colors, or what mood should they convey?"
- "Your documents use mixed fonts. Is there a preferred font family?"
- "Your tone ranges from very formal to casual. Which end of the spectrum is the true brand voice?"

### Round 3: Differentiation
Ask: "What should make your brand instantly recognizable? What's the one thing that should feel different from competitors?"

### Round 4: Satisfaction Check
Ask: "Review the updated brand book. What feels off or missing? We can keep refining, or if it looks good, I'll finalize it."

Repeat rounds as needed until the user is satisfied.

## Important Notes

- When reading images (PNG, JPG, SVG), use the Read tool which supports visual file inspection.
- For PDFs, use the Read tool with page ranges for large files.
- For PPTX/DOCX, use Bash to extract XML content (`unzip -p file.pptx ppt/slides/*.xml`).
- Extract CSS color values with Grep for hex codes (`#[0-9a-fA-F]{3,8}`) and rgb/hsl patterns.
- Always show the user what you found before writing the brand book — let them correct misidentifications.
- The brand book should be self-contained — an AI model reading only BRAND-BOOK.md should have everything needed to create on-brand content.
