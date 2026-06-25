---  
name: visual-system  
description: Permanent design rule that governs every visual decision in the landing page. Enforces visual profile consistency across colors, typography, spacing, radii, shadows, animations, and component styling. All skills that produce or evaluate visual output must comply with this system.  
compatibility: opencode  
metadata:  
  domain: builder  
  agent: landing-base-builder  
---  
  
## What I do  
  
- Enforce visual consistency across every component, section, and page element  
- Translate design tokens from the landing architecture into Tailwind configuration and CSS custom properties  
- Define strict rules for color usage, typography application, spacing rhythm, border radii, shadows, and animations per visual profile  
- Provide component-level styling constraints that prevent generic or inconsistent output  
- Act as the single source of truth for "how things look" — overriding any default, assumption, or shortcut  
  
## When to use me  
  
This is a **permanent rule**, not a sequential skill. It is active during the entire build process and must be referenced before writing any visual code.  
  
Load this skill when:  
- Creating or modifying any component  
- Writing Tailwind config  
- Applying colors, fonts, spacing, or shadows  
- Adding animations or transitions  
- Making any decision about how something looks  
  
## Visual profiles  
  
Every landing page is assigned ONE profile by the `niche-reasoning` skill. The profile dictates the entire visual language.  
  
### Precision  
- **Personality:** clinical, trustworthy, structured, professional  
- **Niches:** medical, dental, legal, financial, accounting, insurance, tech, consulting  
- **Rules:**  
  - Border radius: 4–8px. Never rounded-full on containers. Pills only on small badges.  
  - Shadows: subtle, 0–4px blur, low opacity (0.05–0.1). No colored shadows.  
  - Typography: thin sans-serif or modern serif for headings. Clean sans-serif for body. No decorative fonts.  
  - Spacing: generous, structured. Sections feel airy, not cramped.  
  - Colors: muted, desaturated. Primary color used sparingly — accents, CTAs, key highlights. Large surfaces stay neutral.  
  - Animations: minimal. Fade-in on scroll (200–300ms). No bouncing, sliding, or attention-seeking motion.  
  - Layout: grid-aligned, symmetrical. Asymmetry only when intentional and subtle.  
  - Icons: line-style, consistent stroke width. No filled/emoji-style icons.  
  - Images: high-quality, professional. No stock photo clichés (handshake, pointing at screen).  
  
### Warmth  
- **Personality:** friendly, approachable, caring, personal  
- **Niches:** family services, childcare, pet care, home services, cleaning, senior care, tutoring, bakery  
- **Rules:**  
  - Border radius: 12–20px. Rounded shapes are encouraged. Cards and containers feel soft.  
  - Shadows: medium, warm-toned (slight warm color in shadow, not pure black). Soft, diffused.  
  - Typography: rounded sans-serif or humanist fonts for headings. Friendly body font. Weight contrast between heading (bold) and body (regular).  
  - Spacing: comfortable, not too tight. Elements have room to breathe but page doesn't feel empty.  
  - Colors: warm palette. Earth tones, soft oranges, warm greens, gentle blues. Avoid cold grays — use warm grays (stone, zinc with warm undertone).  
  - Animations: gentle. Ease-in-out curves, 300–400ms. Subtle scale on hover (1.02–1.03). No sharp or mechanical motion.  
  - Layout: slightly organic. Asymmetric grids acceptable. Overlapping elements for depth. Cards can have slight rotation or offset.  
  - Icons: filled or duotone. Rounded corners on icon containers. Friendly expressions.  
  - Images: real people, candid shots. Warm color grading. Avoid sterile or clinical imagery.  
  
### Authority  
- **Personality:** strong, reliable, bold, no-nonsense  
- **Niches:** construction, roofing, industrial, B2B, manufacturing, engineering, heavy equipment  
- **Rules:**  
  - Border radius: 0–6px. Sharp corners communicate strength. Rounded edges feel weak in this context.  
  - Shadows: strong, dramatic. Higher offset, higher blur. Can use dark, high-opacity shadows.  
  - Typography: bold sans-serif for headings (700–900 weight). Uppercase for labels and section markers. Wide letter-spacing on uppercase text.  
  - Spacing: tight headers, generous sections. Content blocks feel dense and packed with value. Sections have strong vertical padding.  
  - Colors: dark backgrounds dominant. High contrast. Primary color is bold and saturated. Accent color is bright against dark. No pastels.  
  - Animations: sharp, confident. Short duration (150–250ms). No ease-in-out — use ease-out for snappy feel. Transform-based (scale, translate), not opacity-only.  
  - Layout: strong grid lines. Full-width sections. Geometric dividers (angled, not curved). Overlapping elements for depth and power.  
  - Icons: solid fill, geometric. Bold stroke weight if using line icons. Can use icon backgrounds (circles, squares).  
  - Images: dramatic angles, high contrast. Machinery, finished projects, team in action. No soft focus.  
  
### Energy  
- **Personality:** vibrant, dynamic, exciting, youthful  
- **Niches:** fitness, entertainment, food/restaurant, nightlife, sports, events, music  
- **Rules:**  
  - Border radius: 8–16px. Mixed radii acceptable — some sharp, some rounded, creating visual variety.  
  - Shadows: colored shadows encouraged. Layer multiple shadows for depth. Glow effects on hover for CTAs.  
  - Typography: expressive headings — variable weight, large size differences between H1 and body. Display fonts for hero. Can mix serif and sans-serif if intentional.  
  - Spacing: dynamic. Tighter in content-rich areas, wider for impact sections. Rhythm creates energy.  
  - Colors: vibrant, saturated. Gradients encouraged (but max 2 colors per gradient). Complementary or triadic color schemes. Dark mode preferred for maximum color pop.  
  - Animations: energetic, noticeable. 200–350ms. Scale, rotate, and color transitions. Parallax on scroll. Staggered animations for lists. Still respect `prefers-reduced-motion`.  
  - Layout: asymmetric, dynamic. Overlapping layers, diagonal sections, non-standard grids. Break the grid intentionally — but maintain alignment within sections.  
  - Icons: filled with color. Can use gradients on icons. Animated icons on hover acceptable.  
  - Images: high energy, motion blur, action shots. Saturated color grading. Full-bleed images.  
  
## Tailwind configuration enforcement  
  
The `tailwind.config.*` file must reflect the design tokens from `landing-architecture`:  
  
```javascript  
// Structure — values come from architecture tokens  
module.exports = {  
  theme: {  
    extend: {  
      colors: {  
        primary: { DEFAULT, light, dark },  
        secondary: { DEFAULT },  
        accent: { DEFAULT },  
        surface: { DEFAULT, dark },  
        // Map ALL color tokens — no unnamed hex values in components  
      },  
      fontFamily: {  
        heading: ['[heading font]', ...fallback],  
        body: ['[body font]', ...fallback],  
      },  
      fontSize: {  
        // Map complete type scale with [size, { lineHeight, letterSpacing }]  
      },  
      borderRadius: {  
        // Profile-specific values  
      },  
      boxShadow: {  
        // Profile-specific values  
      },  
      spacing: {  
        // Custom spacing tokens if needed beyond Tailwind defaults  
      },  
    },  
  },  
}``` 

Rules

    No arbitrary values in components. Every [#hex], [14px], [0.5rem] in a component is a violation. Values must come from Tailwind config or CSS custom properties.

    No default Tailwind colors. gray-500, blue-600, red-400 — all banned. Use only the semantic tokens defined in config (primary, secondary, accent, surface, etc.).

    Font classes only. Use font-heading and font-body — never font-sans, font-serif, or inline font-family.

    Consistent radius. If the profile says 4–8px, every rounded-* class must resolve to a value in that range. No rounded-full on containers in a Precision profile.

Color usage rules

Hierarchy

| Usage                         | Token                          | Frequency                             |
|-------------------------------|--------------------------------|---------------------------------------|
| Page background               | bg-background                  | Large surfaces                        |
| Card/component background     | bg-surface                     | Medium surfaces                       |
| Dark sections                 | bg-surface-dark                | Alternating sections                  |
| Primary actions (CTA buttons) | bg-primary                     | Sparse — CTAs and key highlights only |
| Secondary actions             | bg-secondary or border-primary | Supporting elements                   |
| Accent/highlight              | accent                         | Badges, tags, small highlights        |
| Body text                     | text-primary                   | All main content                      |
| Secondary text                | text-secondary                 | Captions, labels, muted content       |

Rules

    Primary color is scarce. The more you use it, the less impact it has. CTAs and 1-2 key highlights per section maximum.

    Dark sections invert the palette. All text in dark sections uses text-on-dark. All backgrounds use surface-dark. Do not just add text-white — use the token.

    Never use raw hex or RGB in components. Always reference a Tailwind token or CSS variable.

    Gradients follow the profile. Precision: no gradients. Warmth: subtle warm gradients. Authority: dark-to-darker. Energy: vibrant two-color gradients.

    Contrast is tested, not assumed. Every text/background pair must meet WCAG 2.1 AA. If the architecture logged a contrast adjustment, implement it exactly.

Typography usage rules

Heading hierarchy

| Element | Font         | Weight          | Size source        | Additional                   |
|---------|--------------|-----------------|--------------------|------------------------------|
| H1      | font-heading | Bold/Black      | text-h1 token      | Only ONE per page            |
| H2      | font-heading | Semibold/Bold   | text-h2 token      | Section headers              |
| H3      | font-heading | Medium/Semibold | text-h3 token      | Subsection headers           |
| Body    | font-body    | Regular         | text-body token    | All prose content            |
| Label   | font-body    | Medium          | text-label token   | May be uppercase per profile |
| Caption | font-body    | Regular         | text-caption token | Muted color                  |

Rules

    Headings are always font-heading. No mixing heading font into body or body font into headings.

    Weight creates hierarchy, not just size. An H2 and H3 at similar sizes are differentiated by weight.

    Line height is set per token. Do not use Tailwind's default leading-* unless it matches the token value.

    Letter spacing follows the profile. Precision may use tighter tracking on headings. Authority uses wide tracking on uppercase labels. Do not apply letter-spacing arbitrarily.

    Google Fonts are loaded with only required weights. Do not import 100–900. Import only the weights used in the type scale.

Spacing rules
Vertical rhythm

    Sections are separated by the section-y token — consistent across the entire page

    Within sections, elements follow the stack-gap and component-gap tokens

    Headlines and their supporting text: stack-gap (tighter)

    Cards in a grid: component-gap

    Never mix spacing tokens arbitrarily — pick the right one for the relationship

Rules

    Consistency over creativity. If section padding is py-20, every section gets py-20 (unless mobile override).

    Component internal spacing is proportional. Card padding should relate to card gap. If gap is gap-6, internal padding is p-6 or p-8 — not p-2.

    Mobile spacing reduces proportionally. Don't just halve everything. Use the section-y-mobile token and scale internal spacing by ~60-75%.

    Whitespace is intentional. Empty space communicates premium. Cramped layouts communicate cheap. When in doubt, add more space.

Animation rules
Allowed animations

| Animation                   | Profiles       | Duration             | Easing      |
|-----------------------------|----------------|----------------------|-------------|
| Fade in on scroll           | All            | 200–400ms            | ease-out    |
| Slide up on scroll          | Warmth, Energy | 300–500ms            | ease-out    |
| Scale on hover              | All            | 150–250ms            | ease-in-out |
| Color transition on hover   | All            | 150–200ms            | ease        |
| Background color transition | All            | 200–300ms            | ease        |
| Staggered list reveal       | Energy         | 100ms delay per item | ease-out    |

Rules

    prefers-reduced-motion is mandatory. Every animation must have a @media (prefers-reduced-motion: reduce) override that disables or minimizes it.

    CSS over JS. If it can be done with CSS transitions/animations, do not use JS. IntersectionObserver for scroll triggers is the exception.

    No animation libraries. No Framer Motion, GSAP, or AOS. CSS transitions + IntersectionObserver cover 100% of needs for a landing page.

    One motion language per page. If sections fade in, ALL sections fade in. Don't mix fade-in, slide-left, zoom-in, and rotate across different sections.

    Maximum 3 animation types per page. Scroll reveal + hover effect + one accent animation. That's the budget.

Anti-patterns (violations to actively prevent)

| Anti-pattern                          | Why it's wrong                          | Fix                                                              |
|---------------------------------------|-----------------------------------------|------------------------------------------------------------------|
| Default Tailwind colors in components | Breaks the visual system, looks generic | Use only semantic tokens                                         |
| rounded-lg on everything              | Lazy, inconsistent with profile         | Use profile-specific radius tokens                               |
| shadow-md everywhere                  | No hierarchy, feels flat                | Use shadow scale from tokens (sm, md, lg for different contexts) |
| Inline styles                         | Unmaintainable, undetectable by audit   | Tailwind classes or CSS variables only                           |
| !important                            | Band-aid for specificity issues         | Fix the actual specificity conflict                              |
| Mixing font families                  | Breaks typography system                | Heading font for headings, body font for body. No exceptions.    |
| Animations without reduced-motion     | Accessibility violation                 | Always add reduced-motion override                               |
| Arbitrary values [24px]               | Means the token system is incomplete    | Add the value to the config                                      |

Compliance check

Before finalizing any component or section, verify:

    All colors reference semantic tokens, not raw values or default Tailwind

    Typography uses font-heading or font-body, correct weight, correct size token

    Spacing uses defined tokens, consistent across same-level elements

    Border radius matches visual profile range

    Shadows match visual profile intensity

    Animations respect the profile type and motion budget

    prefers-reduced-motion is handled on every animation

    Dark section text uses text-on-dark token

    No arbitrary values in Tailwind classes

    Responsive behavior follows the architecture's responsive strategy

Rules

    This system is law. No component ships without compliance. No "I'll fix it later."
    Tokens are the vocabulary. If a value isn't in the token set, either add it to the config or don't use it. There is no middle ground.
    Profile consistency is measurable. If you screenshot the page and can identify the visual profile in 3 seconds, the system is working. If it looks like "generic Tailwind site," it's not.
    The design database wins ties. If this system says one thing and the design database says another for a specific niche, the database wins.
    Visual system violations are Major defects. Any mismatch between declared profile and implemented values is flagged by the error-finder agent. Fix before shipping.