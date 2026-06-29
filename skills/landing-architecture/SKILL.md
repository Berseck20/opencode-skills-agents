---  
name: landing-architecture  
description: Transforms the research document and niche classification into a complete landing page blueprint — section order, layout specifications, component definitions, responsive behavior, and implementation-ready design tokens. The builder reads this plan and implements without making design decisions.  
compatibility: opencode  
metadata:  
  domain: builder  
  agent: landing-base-builder  
---  
  
## What I do  
  
- Define the exact section order and layout for the landing page based on niche, conversion framework, and design database patterns  
- Specify every component with its variant, props, content mapping, and responsive behavior  
- Generate implementation-ready design tokens (colors, spacing, radii, shadows, typography scale)  
- Map content strategy decisions to concrete page architecture  
- Produce a blueprint so precise that the builder agent makes zero design decisions — only implementation decisions  
  
## When to use me  
  
Use this skill as the first step in the `landing-base-builder` agent workflow. It requires the completed research document (`research-[business-slug].md`) produced by the `research-seo-agent`.  
  
Never run without the research document. If it doesn't exist, STOP.  
  
## Input requirements  
  
Read and extract from `research-[business-slug].md`:  
  
- Niche classification (primary, sub-niche, tier, urgency)  
- Visual profile (Precision, Warmth, Authority, Energy) — includes **Layout Variant ID** (e.g., `W-story`, `A-impact`, `P-split`, `E-dynamic`)  
- Design database matches (palette, style, typography, landing pattern, UX guidelines)  
- Message hierarchy (H1, H2s, supporting copy)  
- Conversion framework (PAS, AIDA, BAB, hybrid)  
- CTA strategy (primary, secondary, micro)  
- Objection map with placements  
- Social proof selections (testimonials, trust signals, stats)  
- Tone calibration (formality, technical, emotional scales)  
- All extracted business data (services, location, reviews, team, hours, etc.)  
  
**Every field marked `[NOT FOUND]` in the research document means that section is conditional — plan it but flag it for conditional rendering.**  
  

## Layout variant resolution  
  
The Layout Variant ID from the research document (section 15) is the **structural DNA** of this landing page. It determines:  
  
1. **Hero structure** — Not a cosmetic choice. The variant dictates the hero's HTML skeleton:  
   - `*-story` → Full-width image background with content overlay, long-form headline area  
   - `*-split` → 2-column asymmetric layout (content | visual), NO full-width image  
   - `*-impact` → Typography-driven dark hero, minimal imagery, maximum whitespace  
   - `*-showcase` → Product/service gallery hero with carousel or grid, content below  
   - `*-minimal` → Clean single-column, thin hero band, content-dense below fold  
   - `*-bold` → Oversized typography, strong geometric shapes, high-contrast blocks  
  
2. **Section disposition** — Each variant implies a different rhythm:  
   - `*-story` → Long scroll, editorial rhythm, generous whitespace between sections  
   - `*-split` → Alternating 2-column sections, compact vertical  
   - `*-impact` → Short page, few powerful sections, strong visual anchors  
   - `*-showcase` → Gallery-heavy, multiple visual sections, minimal text blocks  
   - `*-minimal` → Dense information, thin spacing, utility-focused  
   - `*-bold` → Asymmetric sections, oversized elements, unconventional grid breaks  
  
3. **Page length control** — The variant constrains total section count:  
   - `*-impact` and `*-minimal` → MAX 7 sections (including nav/footer)  
   - `*-story` → MAX 10 sections  
   - `*-split` and `*-bold` → MAX 9 sections  
   - `*-showcase` → MAX 8 sections  
  
**Rule:** If the data supports more sections than the variant allows, MERGE sections (e.g., combine About + Team into one section) rather than exceeding the limit. If the data supports fewer, do NOT pad with filler sections.  
  
**Rule:** The variant prefix letter maps to the visual profile:  
- `W-` = Warmth, `P-` = Precision, `A-` = Authority, `E-` = Energy  
- If the research says profile=Warmth and variant=`W-story`, the hero MUST follow the `*-story` structure with Warmth visual tokens. No mixing.

## Section planning  
  
### Section order  
Define the exact sequence of sections following this process:  
  
1. **Select the landing pattern** from `design-database/landing-patterns.md` using the niche mapping table. The pattern ID (Emergency Response, Trust Builder, Portfolio Showcase, etc.) defines the base section sequence and section catalog codes (H1-H8, SP1-SP7, CTA1-CTA8).  
2. **Apply variation axes** from `landing-patterns.md` → Variation Axes section. For each axis (hero style, social proof format, CTA rhythm, visual density, content depth), select the variant that matches the research data. Two landings in the same niche MUST differ in at least 2 variation axes.  
3. **Adjust by conversion framework:** PAS puts problem-oriented content early. AIDA front-loads attention-grabbers. BAB leads with current state.  
4. **Adjust by urgency level:** Emergency niches put phone/CTA within first viewport. Planned niches can afford a longer trust-building sequence.  
5. **Trim by available data:** Sections without data get flagged as conditional, not removed. If testimonials are `[NOT FOUND]`, the testimonials section exists in the plan but renders only if data is provided later.  
6. **Enforce length rule:** The final section count = mandatory sections + conditional sections WITH data. Never add filler sections to "complete" a layout. A 6-section landing is valid.  
  
**Output the selected pattern ID and variation axis choices at the top of the Section Plan.**  
  
### Standard section catalog  
  
For each section in the plan, specify:  
  

[Section Name]

    Position: [number in sequence]

    Purpose: [what this section does in the conversion flow]

    Background: [color token — e.g., bg-primary, bg-surface, bg-dark]

    Layout: [grid/flex specification, columns, alignment]

    Components: [list of components with variants]

    Content mapping: [which research data fields populate this section]

    Conditional: [yes/no — if yes, what data must exist to render]

    Responsive behavior: [how layout changes at mobile/tablet/desktop]

    CTA: [which CTA level appears here, if any]
 
  
### CTA variation rule  
Reference `design-database/ux-guidelines.md` → CTA Rules. Apply:  
- Maximum 3 CTA instances per landing (primary + secondary + micro)  
- Each CTA instance MUST use a different format from this list: button, sticky bar, inline text link, floating badge, form-embedded, phone-tap  
- Never repeat the same CTA format twice in the same landing  
- CTA placement follows the pattern's CTA rhythm axis, not a fixed position


### Mandatory sections (every landing)  
  
1. **Navigation** — sticky, transparent-to-solid on scroll, mobile hamburger menu  
2. **Hero** — Structure determined by Layout Variant ID (see Layout variant resolution above). The hero is NOT "a big section with a headline and button" — its HTML skeleton, column count, image placement, and content hierarchy are all dictated by the variant. Includes primary CTA in the format assigned by content-seo.  
3. **Services/Features** — core offerings with descriptions  
4. **CTA Section** — dedicated conversion section. Each CTA instance across the entire page must use a DIFFERENT format from this list: `button`, `sticky-bar`, `inline-link`, `floating-badge`, `form-embedded`, `phone-tap`, `text-banner`. The dedicated CTA section uses the highest-impact format not yet used elsewhere on the page. 
5. **Footer** — NAP info, links, legal  
  
### Conditional sections (data-dependent)  
  
6. **Social Proof / Testimonials** — only if reviews exist  
7. **Trust Bar** — only if certifications, licenses, or awards exist  
8. **Stats Counter** — only if quantifiable metrics exist  
9. **Team / About** — only if team or founder data exists  
10. **Service Area / Map** — only if location + service area data exists  
11. **FAQ** — only if common questions can be derived from niche  
12. **Gallery / Portfolio** — only if work samples or image inventory exists  
13. **Process / How It Works** — only if the business has a defined process  
14. **Pricing** — only if pricing data exists and is meant to be public  
  
## Design tokens  
Generate a complete token set derived from these specific design database files:  
- **Colors:** `design-database/palettes.md` → select palette by niche, extract all 16 semantic roles  
- **Typography:** `design-database/typography.md` → select pairing by visual profile ID (BI-XX, CC-XX, etc.), extract scale  
- **Spacing/Shape/Animation:** `design-database/styles.md` → select style profile, extract spacing system, shadow set, border radii, animation tokens  
- **Do NOT invent values.** Every token must trace to a specific value in these files.  
  
### Color tokens  
  

colors:
primary: [from palette]
primary-light: [computed — 15% lighter]
primary-dark: [computed — 15% darker]
secondary: [from palette]
accent: [from palette]
background: [from palette — main page bg]
surface: [from palette — card/component bg]
surface-dark: [from palette — dark section bg]
text-primary: [from palette — main body text]
text-secondary: [from palette — secondary/muted text]
text-on-primary: [computed — contrast against primary]
text-on-dark: [computed — contrast against surface-dark]
border: [from palette or computed — subtle border color]
success: [contextual]
error: [contextual]

  
**Every text/background pair must pass WCAG 2.1 AA.** Calculate and verify. If a palette color fails contrast, adjust it and log the adjustment.  
  
### Typography tokens  
  

typography:
font-heading: [from typography match — Google Font name]
font-body: [from typography match — Google Font name]
font-mono: [if needed — default to "JetBrains Mono"]
scale:
h1: [size, weight, line-height, letter-spacing, mobile-size]
h2: [size, weight, line-height, letter-spacing, mobile-size]
h3: [size, weight, line-height, letter-spacing, mobile-size]
body: [size, weight, line-height]
body-sm: [size, weight, line-height]
label: [size, weight, letter-spacing, text-transform]
caption: [size, weight, line-height]
google-fonts-url: [complete import URL with all weights needed]

  
### Spacing tokens  
  

spacing:
section-y: [vertical padding for sections — desktop]
section-y-mobile: [vertical padding for sections — mobile]
container-max: [max-width for content container]
container-padding: [horizontal padding]
component-gap: [gap between components in a grid]
stack-gap: [gap between stacked elements]

  
### Shape tokens  
  

shape:
radius-sm: [from visual profile]
radius-md: [from visual profile]
radius-lg: [from visual profile]
radius-full: [9999px — for pills/circles]
shadow-sm: [from visual profile]
shadow-md: [from visual profile]
shadow-lg: [from visual profile]

  
### Animation tokens  
  

animation:
duration-fast: [from visual profile]
duration-normal: [from visual profile]
easing: [from visual profile]
scroll-reveal: [type — fade-up, fade-in, slide-up, none]
hover-scale: [1.02-1.05 based on profile]
reduced-motion: [always true — respect prefers-reduced-motion]

  
## Component specifications  
  
For every component used in the section plan, define:  
  

[Component Name]

    Type: [static | interactive]

    Hydration: [none | client:visible | client:load | client:idle]

    Props:

        [prop name]: [type] — [source field from research data]

    Variants: [list visual variants if multiple contexts]

    States: [default, hover, focus, active, disabled — as applicable]

    Responsive:

        Mobile (< 640px): [layout change]

        Tablet (640-1024px): [layout change]

        Desktop (> 1024px): [default layout]

    Accessibility:

        [ARIA labels, roles, keyboard behavior as needed]

  


### Hydration rules  

| Component type              | Hydration directive    | Reason                         |
|-----------------------------|------------------------|--------------------------------|
| Static text, images, cards  | None (Astro component) | No JS needed                   |
| Navigation with mobile menu | client:load            | Needed immediately for UX      |
| Scroll-triggered animations | client:visible         | Only when in viewport          |
| Contact forms               | client:idle            | Not critical path              |
| Maps / embeds               | client:visible         | Heavy, defer until visible     |
| Carousels / sliders         | client:visible         | Interactive but not above fold |

Dark/light section rhythm
Plan alternating background colors to create visual rhythm:

Nav:        transparent → bg-surface (on scroll)  
Hero:       bg-primary or bg-dark (high impact)  
Section 2:  bg-background (light)  
Section 3:  bg-surface (subtle contrast)  
Section 4:  bg-dark (visual break)  
Section 5:  bg-background (light)  
...  
CTA:        bg-primary (maximum contrast)  
Footer:     bg-dark  

Rules:

    Never place two identical backgrounds adjacent

    Dark sections need text-on-dark colors applied to all children

    The hero and final CTA should be the highest visual impact sections

    Light/dark alternation creates scroll momentum

Responsive strategy
Breakpoints

mobile:  < 640px  
tablet:  640px - 1024px  
desktop: > 1024px  

Global responsive rules

    Grid columns: 1 (mobile) → 2 (tablet) → 3-4 (desktop)

    Section padding: section-y-mobile below 640px, section-y above

    Typography: use mobile sizes from type scale below 640px

    Images: object-cover with defined aspect ratios per context

    Navigation: horizontal links (desktop) → hamburger menu (mobile/tablet)

    Cards: stack vertically on mobile, grid on tablet+

    Hero: single column centered on mobile, split layout on desktop (if applicable)

## Output format  
Return the complete architecture as a structured Markdown document.  
  
**Header block (mandatory):**  
  
Pattern: [pattern ID from landing-patterns.md]  
Style Profile: [profile ID from styles.md]  
Palette: [palette ID from palettes.md]  
Typography Pairing: [pairing ID from typography.md]  
Variation Axes: [axis1: choice, axis2: choice, ...]  
Section Count: [number]  
  
  
# Landing Architecture: [Business Name]    
    
## Design Tokens    
### Colors    
### Typography    
### Spacing    
### Shape    
### Animation    
    
## Section Plan    
### 1. Navigation    
### 2. Hero    
### 3. [Section Name]    
...    
### N. Footer    
    
## Component Specifications    
### [Component Name]    
...    
    
## Responsive Strategy    
    
## Dark/Light Rhythm Map    
    
## Conditional Sections Summary    
| Section | Required Data | Status |  

Rules

    **Zero ambiguity.** If the builder has to guess a color, spacing value, font size, or layout decision, this plan has failed.
    **Design database values are final.** Do not override palette, typography, or pattern decisions from the database unless there's a documented contrast failure.
    **Conditional ≠ deleted.** Sections with [NOT FOUND] data are planned with conditional rendering, not removed from the architecture.
    **Every token must be used.** Do not define tokens that no section references. Do not reference values that aren't in the token set.
    **Contrast is non-negotiable.** Every text/background pair must pass WCAG 2.1 AA (4.5:1 for normal text, 3:1 for large text). Calculate it. If it fails, adjust the token and document the change.
    **Hydration is intentional.** Every React component must have an explicit hydration directive with a documented reason. Default is no hydration (static Astro).
    **Mobile is not an afterthought.** Every section spec must include mobile behavior. "Same but smaller" is not a responsive strategy.
    **Section count is data-driven.** A business with 3 services, no reviews, and no team photos gets a 6-section page. A business with 12 services, 50 reviews, and team bios gets a 12-section page. Do not pad or cut.
    **Anti-pattern: token soup.** If you have more than 20 color tokens, you're overcomplicating it. Simplify.
    **Anti-pattern: component explosion.** A card is a card. Do not create ServiceCard, FeatureCard, BenefitCard, OfferingCard as separate components if they share 90% of their structure. Use variants.
	**Anti-pattern: ignoring layout variant.** If the architecture produces a centered-text hero when the variant says `*-split`, the entire architecture is invalid. The variant is structural law, not a suggestion.  
	**Anti-pattern: uniform CTA formats.** If every CTA in the plan is `button`, the CTA strategy has failed. Minimum 3 distinct formats across the page.  
	**Anti-pattern: page length inflation.** If the variant says MAX 7 sections and the plan has 11, you've ignored the variant's constraints. Merge or cut — never exceed.  
	**Layout variant is non-negotiable.** It cannot be overridden by niche, data availability, or personal preference. It CAN be adjusted within its structural rules (e.g., `*-split` can be 60/40 or 70/30 column split, but it MUST be a split).
	**Anti-pattern: structural cloning.** If two landings in the same niche share the same pattern + same hero variant + same CTA rhythm, the second one has failed. Vary at least 2 axes.  
	**Anti-pattern: length padding.** A landing with 14 sections where 6 have thin or fabricated content is worse than a landing with 8 dense sections. Cut ruthlessly.