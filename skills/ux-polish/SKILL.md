---  
name: ux-polish  
description: Performs a section-by-section visual and UX enhancement pass on the built landing page. Eliminates AI-generated patterns, injects visual sophistication, and ensures every section feels handcrafted by a senior design team. This is the core differentiator skill.  
compatibility: opencode  
metadata:  
  domain: rebuild  
  agent: rebuild-landing  
---  
  
## What I do  
  
- Analyze every section of the built landing for visual mediocrity and AI-tells  
- Apply micro-interactions, refined spacing, visual hierarchy adjustments, and layout sophistication  
- Inject craft details that distinguish a $10K agency landing from a template  
- Enforce niche-appropriate personality through component-level refinements  
- Transform "correct but generic" output into "intentional and memorable" output  
  
## When to use me  
  
Use this skill after `image-strategy` has completed, as the second step in the `rebuild-landing` workflow. The base landing is structurally correct but visually undifferentiated — this skill fixes that.  
  
Requires:  
- A built Astro project (output of `landing-base-builder`)  
- Active visual profile assignment  
- Image strategy document (for image container context)  
- Design database access (for style, palette, and UX reference)  
  
## Structural validation (before any enhancement)  
Before applying visual tweaks, verify that the base build respects the architecture's structural decisions. If it doesn't, CSS polish on a wrong structure is wasted effort.  
  
### Check 1: Layout variant compliance  
Read the architecture's header block → Layout Variant ID (e.g., `W-story`, `A-impact`).  
Compare the built hero and section structures against the variant spec in `visual-system` → Structural layout variants.  
- If the hero doesn't match the variant (e.g., variant says "full-width image with overlay" but builder made "centered text + button"), **flag as Critical** and rewrite the hero structure.  
- If sections all use the same grid pattern despite the variant specifying mixed layouts, **flag as Critical** and restructure.  
  
### Check 2: CTA format compliance  
Read the architecture's CTA Strategy → each CTA has an assigned format (button, sticky-bar, inline-link, etc.).  
- If all CTAs are standard buttons despite different formats being specified, **flag as Critical** and implement the correct formats.  
  
### Check 3: Section count compliance  
Count sections in the built page. Compare against architecture's Section Count.  
- If the builder added padding sections not in the architecture, **remove them**.  
- If the builder omitted conditional sections that have data, **add them**.  
  
**Rule:** Structural fixes happen FIRST. Only after all Critical flags are resolved do you proceed to visual enhancement.  
  
## AI-tell detection  
After structural validation, identify and flag these common AI-generated patterns:  
  
### Layout AI-tells

| Pattern                                                           | Why it's an AI-tell                | Fix                                                                          | Max file size |
|-------------------------------------------------------------------|------------------------------------|------------------------------------------------------------------------------|---------------|
| Perfect 3-column grid for everything                              | AI defaults to symmetric grids     | Vary layouts: 2-col + sidebar, asymmetric splits, full-width breaks          | 200KB         |
| Every section has the same structure: heading → subheading → grid | Predictable rhythm = template feel | Alternate structures: lead with stat, lead with image, lead with testimonial | 150KB         |
| Equal spacing everywhere                                          | AI uses uniform padding            | Create spacing rhythm — tighter in content blocks, wider for impact sections | 80KB          |
| All cards identical in size and shape                             | AI loves uniformity                | Featured card larger, different cards for different content types            | 40KB          |
| Centered everything                                               | AI defaults to text-center         | Left-align body text, use center only for headings and CTAs intentionally    | 60KB          |
| Background texture                                                | 1440×[h]                           | Not needed                                                                   | 100KB         |

Visual AI-tells

| Pattern                                 | Why it's an AI-tell       | Fix                                                                                 |
|-----------------------------------------|---------------------------|-------------------------------------------------------------------------------------|
| Single shadow depth across all elements | No visual hierarchy       | Layered shadows: subtle on inline, medium on cards, strong on modals/CTAs           |
| Border radius identical on all elements | Lazy token application    | Scale radius by element size: small on badges, medium on cards, large on containers |
| No visual texture or depth              | Flat, lifeless surfaces   | Subtle patterns, gradient overlays, border highlights, inner shadows                |
| Icons all same size and style           | AI applies uniform sizing | Scale icons by importance, vary container treatments                                |
| No whitespace hierarchy                 | AI fills available space  | Premium = generous whitespace. Create breathing room around key elements            |

Content AI-tells

| Pattern                                    | Why it's an AI-tell            | Fix                                                                    |
|--------------------------------------------|--------------------------------|------------------------------------------------------------------------|
| Every heading is 4-6 words                 | AI gravitates to medium-length | Mix: short punchy (2-3 words), medium descriptive, long statement      |
| CTAs all say "Get Started" or "Learn More" | Generic defaults               | Specific action: "Book My Free Inspection", "See Our Work", "Call Now" |
| Every section has a subtitle               | Unnecessary repetition         | Some sections need no subtitle — let the content speak                 |
| Perfectly parallel structure in lists      | AI makes all bullets match     | Natural language varies — some points are longer, some shorter         |

Enhancement techniques
1. Visual depth layering

Add depth to flat sections without changing the design system:

/* Subtle top border on cards for dimension */  
.card {  
  border-top: 1px solid rgba(var(--color-primary-rgb), 0.1);  
}  
  
/* Inner highlight on dark sections */  
.dark-section {  
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.05);  
}  
  
/* Layered shadows for elevated elements */  
.elevated {  
  box-shadow:  
    0 1px 2px rgba(0, 0, 0, 0.04),  
    0 4px 8px rgba(0, 0, 0, 0.04),  
    0 12px 24px rgba(0, 0, 0, 0.06);  
}  

2. Spacing sophistication

Replace uniform spacing with intentional rhythm:
Section A (Hero):         py-24 lg:py-32    — maximum breathing room  
Section B (Services):     py-16 lg:py-24    — standard section  
Section C (Social proof): py-12 lg:py-16    — tighter, feels connected  
Section D (CTA):          py-20 lg:py-28    — generous, important  
Section E (FAQ):          py-16 lg:py-20    — standard  
Section F (Footer):       py-12 lg:py-16    — compact, utilitarian  
Rule: Adjacent sections should never have identical padding unless intentional.

3. Layout variation  
Break the grid monotony while maintaining coherence. These are NOT suggestions — verify each one:  
  
- **Hero:** Must match the layout variant from `visual-system`. If variant says split, it's split. If it says overlay, it's overlay. Do not default.  
- **Services:** If 3+ services, use a featured card (larger, spanning 2 cols) + smaller cards. Never uniform grid of identical cards.  
- **Testimonials:** Offset layout (large quote + smaller cards), or single spotlight testimonial, or horizontal scroll. Never 3 identical quote cards in a row.  
- **Stats:** Inline horizontal strip or embedded in hero. Never a card grid.  
- **About/Team:** Asymmetric image + text split (60/40 or 40/60). Never centered text block.  
- **CTA:** Matches the assigned CTA format from architecture. Never a generic centered button if the format says sticky-bar or form-embedded.  
- **FAQ:** Single column, max-width constrained. Never full-width grid.  
  
If the built page violates any of these, restructure the section — not just restyle it.  

4. Micro-interactions
Add subtle, purposeful interactions that communicate quality:

/* Button hover — not just color change */  
.btn-primary {  
  transition: all 200ms ease-out;  
}  
.btn-primary:hover {  
  transform: translateY(-1px);  
  box-shadow: 0 4px 12px rgba(var(--color-primary-rgb), 0.3);  
}  
.btn-primary:active {  
  transform: translateY(0);  
}  
  
/* Card hover — subtle lift */  
.card {  
  transition: transform 200ms ease-out, box-shadow 200ms ease-out;  
}  
.card:hover {  
  transform: translateY(-2px);  
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.08);  
}  
  
/* Link hover — underline animation */  
.text-link {  
  text-decoration: none;  
  background-image: linear-gradient(currentColor, currentColor);  
  background-size: 0% 1px;  
  background-position: 0 100%;  
  background-repeat: no-repeat;  
  transition: background-size 300ms ease-out;  
}  
.text-link:hover {  
  background-size: 100% 1px;  
}  

5. Typography refinements
Elevate text beyond "correct" to "considered":

/* Optical sizing for large headings */  
.hero-heading {  
  letter-spacing: -0.02em;  /* Tighten at large sizes */  
  text-wrap: balance;        /* Prevent orphaned words */  
}  
  
/* Prose optimization */  
.prose {  
  max-width: 65ch;           /* Optimal line length */  
  text-wrap: pretty;         /* Better line breaks */  
}  
  
/* Label treatment by profile */  
.label-precision {  
  text-transform: uppercase;  
  letter-spacing: 0.08em;  
  font-size: 0.75rem;  
  font-weight: 500;  
}  
  
.label-warmth {  
  text-transform: none;  
  font-weight: 600;  
  font-size: 0.875rem;  
}  

6. Section transitions
How one section flows into the next:

/* Angled divider — Authority/Energy profiles */  
.section-divider-angle {  
  clip-path: polygon(0 0, 100% 0, 100% calc(100% - 3rem), 0 100%);  
  margin-bottom: -3rem;  
}  
  
/* Soft gradient transition — Warmth profile */  
.section-fade {  
  background: linear-gradient(to bottom, var(--color-surface) 0%, var(--color-background) 100%);  
  height: 6rem;  
  margin-top: -3rem;  
}  
  
/* Hard line with accent — Precision profile */  
.section-rule {  
  border-top: 1px solid var(--color-border);  
  max-width: 6rem;  
  margin: 0 auto;  
  padding-top: 4rem;  
}  

Section-by-section enhancement checklist
For EACH section, evaluate and enhance:

Structure

    Layout differs from adjacent sections

    Content hierarchy is clear without reading

    Whitespace is proportional to content importance

    Section has a clear visual entry point (where the eye goes first)

Visual craft

    Shadows create depth, not just decoration

    Border radius is proportional to element size

    Color usage follows scarcity principle (primary color is rare)

    Background treatment adds dimension (not flat color only)

    Transition to next section is intentional (not just padding)

Typography

    Heading length varies from section to section

    Body text has optimal line length (45-75 characters)

    Text alignment matches content type (left for prose, center for impact)

    Weight contrast creates scannable hierarchy

Interaction

    Hover states communicate interactivity

    Focus states are visible and on-brand

    Animations enhance comprehension, not distract

    Touch targets are ≥44px on mobile

Differentiation

    This section could NOT be copy-pasted to a different business

    The visual treatment reflects the specific niche

    At least one detail makes this section memorable

    No default Tailwind patterns visible (no "looks like a tutorial")

Profile-specific enhancements

Precision — Details that communicate trust

    Subtle grid lines or alignment markers as decorative elements

    Data-driven visual elements (small charts, metric displays)

    Clean dividers between content blocks

    Muted icon containers with thin borders

    Minimal badge/tag system for credentials

Warmth — Details that communicate care

    Organic shapes as section decorations (blobs, waves)

    Warm-toned overlays on image containers

    Hand-drawn or illustrated icon style (CSS/SVG, not a library)

    Rounded, soft containers with generous padding

    Testimonials with emphasis on human names and faces

Authority — Details that communicate strength

    Bold geometric decorations (angled lines, thick borders)

    High-contrast stat displays (large numbers, dark backgrounds)

    Full-bleed image sections that command attention

    Thick accent borders on key elements

    Badge/certification displays with visual weight

Energy — Details that communicate excitement

    Gradient accents on borders and underlines

    Animated background elements (subtle CSS patterns)

    Overlapping layers creating visual energy

    Color-rich icon treatments

    Dynamic card layouts (varied sizes, slight rotation on hover)

Anti-patterns (things to actively remove)

| Found this                                      | Replace with                                                            |
|-------------------------------------------------|-------------------------------------------------------------------------|
| text-center on body paragraphs                  | text-left (or text-center only on short impact text)                    |
| Same gap-6 on every grid                        | Varied gaps based on content relationship                               |
| rounded-lg on everything                        | Profile-appropriate radius scaled by element size                       |
| shadow-md everywhere                            | Layered shadow system (sm/md/lg for different depths)                   |
| max-w-7xl mx-auto on every section              | Vary container widths: narrow for text, wide for grids, full for impact |
| Identical card components for all content types | Different card variants for services vs testimonials vs team            |
| bg-gray-50 alternating sections                 | Profile-appropriate surface colors with texture variation               |
| Stock gradient from-blue-500 to-purple-600      | Profile-derived gradients using design tokens                           |

Edit protocol

This skill modifies existing files. Follow these rules:

    Surgical edits only. Change the specific lines that need enhancement. Do not rewrite entire components.

    Preserve data bindings. Never break the connection between components and src/data/ files.

    Preserve accessibility. Never remove ARIA labels, alt text, semantic HTML, or keyboard navigation.

    Test after each section. The page must remain functional after every edit.

    Document changes. For each modified file, note what changed and why in the enhancement log.

Output

After completing all enhancements, produce ux-polish-log-[business-slug].md with:

## Enhancement summary  
- Sections enhanced: [count]  
- Files modified: [count]  
- AI-tells eliminated: [count]  
- Profile-specific details added: [count]  
  
## Changes by section  
### [Section name]  
- **File:** `src/components/sections/[Name].astro`  
- **Changes:** [specific changes made]  
- **Rationale:** [why this change elevates the section]  
  
## Remaining recommendations  
- [Any enhancements that require images or client assets]  

Rules

    This is the differentiator. If the output of this skill looks like it could have been built by any AI or template, the skill failed. Every enhancement must push toward "clearly crafted by humans."
    Profile is personality. Every enhancement decision filters through the visual profile. A Warmth landing and an Authority landing that received the same enhancements means this skill was applied lazily.
    Craft over cleverness. Subtle refinements compound into premium feel. One flashy animation surrounded by mediocrity is worse than ten subtle details applied consistently.
    Never break what works. The base landing is structurally sound. Enhancements add quality without removing functionality. If an enhancement breaks the build, revert it.
    The 3-second test. Screenshot the page. Show it to someone for 3 seconds. If they say "Tailwind template" or "AI-generated," the enhancements aren't enough. If they say "that looks professional," the skill succeeded.
    Design database wins ties. When choosing between enhancement approaches, consult the design database for the active niche. Industry-specific guidance overrides generic best practices.
	**Rule: Structure before skin.** If the hero is wrong (centered text when it should be split-layout), no amount of shadow tweaks, spacing refinements, or micro-interactions will fix it. Restructure first, polish second.  
	**Rule: Polish is not differentiation.** Two landings with identical structure but different shadows and spacing still look the same. If after your enhancements the layout skeleton is unchanged, the skill has only applied cosmetics. True polish includes verifying and enforcing the layout variant.  
	**Anti-pattern: cosmetic-only pass.** If your enhancement log contains only CSS changes (shadows, spacing, border-radius, hover effects) and zero structural changes (hero type, grid layout, section order, CTA format), the pass was superficial. Review structural validation again.