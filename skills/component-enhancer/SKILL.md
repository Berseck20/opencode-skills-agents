---  
name: component-enhancer  
description: Performs targeted component-level refinements on every Astro component — advanced CSS techniques, layout polish, responsive edge cases, and profile-specific micro-details that elevate individual components from template-grade to agency-grade.  
compatibility: opencode  
metadata:  
  domain: rebuild  
  agent: rebuild-landing  
---  
  
## What I do  
  
- Audit each Astro component for CSS quality, responsive behavior, and visual polish  
- Apply advanced CSS techniques (clamp, container queries, logical properties, custom properties)  
- Fix responsive edge cases and breakpoint inconsistencies  
- Add profile-specific component-level details (decorative elements, borders, shadows, transitions)  
- Ensure component isolation — every component is self-contained and portable  
  
## When to use me  
  
Use this skill as the third and final step in the `rebuild-landing` workflow, after `ux-polish` has completed the section-level pass. This skill zooms into individual components.  
  
Requires:  
- Astro project already enhanced by `ux-polish`  
- Active visual profile assignment  
- Design database access  
  
## Component audit protocol  
  
For each `.astro` file in `src/components/`, evaluate:  
  
### 1. CSS quality check  

| Issue                      | Detection                                  | Fix                                                      |
|----------------------------|--------------------------------------------|----------------------------------------------------------|
| Magic numbers              | Hardcoded px values with no design token   | Replace with var(--spacing-*), clamp(), or token         |
| Media query inconsistency  | Breakpoints don't match Tailwind config    | Standardize to Tailwind breakpoints or container queries |
| Redundant properties       | Overridden properties in cascade           | Remove duplicates, simplify specificity                  |
| Missing logical properties | margin-left instead of margin-inline-start | Convert to logical properties for RTL readiness          |
| Hardcoded colors           | #hex or rgb() outside design tokens        | Replace with var(--color-*)                              |
| Font-size without scale    | Arbitrary text-[17px]                      | Use type scale or clamp() for fluid typography           |

2. Responsive audit

Test each component at these widths:

320px  — Small phone (iPhone SE)  
375px  — Standard phone  
428px  — Large phone  
768px  — Tablet portrait  
1024px — Tablet landscape / small laptop  
1280px — Desktop  
1440px — Large desktop  
1920px — Full HD  

Check for:

    Text overflow or truncation
    Image aspect ratio distortion
    Touch target size (≥44×44px on mobile)
    Grid/flex wrapping behavior
    Spacing collapse at small widths
    Content reflow between breakpoints (no layout jumps)

3. Fluid typography
Replace static font sizes with fluid scales:

/* Before — jumps between breakpoints */  
.heading {  
  font-size: 1.5rem;  
}  
@media (min-width: 768px) {  
  .heading { font-size: 2.5rem; }  
}  
  
/* After — smooth scaling */  
.heading {  
  font-size: clamp(1.5rem, 1rem + 2vw, 2.5rem);  
}  

Standard fluid scale for the system:

--text-fluid-sm: clamp(0.875rem, 0.8rem + 0.25vw, 1rem);  
--text-fluid-base: clamp(1rem, 0.9rem + 0.35vw, 1.125rem);  
--text-fluid-lg: clamp(1.25rem, 1rem + 1vw, 1.75rem);  
--text-fluid-xl: clamp(1.5rem, 1rem + 2vw, 2.5rem);  
--text-fluid-2xl: clamp(2rem, 1.25rem + 3vw, 3.5rem);  
--text-fluid-3xl: clamp(2.5rem, 1.5rem + 4vw, 4.5rem);  

4. Container queries (where appropriate)
For components that live in different layout contexts:

.card-container {  
  container-type: inline-size;  
  container-name: card;  
}  
  
@container card (min-width: 400px) {  
  .card-content {  
    flex-direction: row;  
    gap: var(--spacing-4);  
  }  
}  
  
@container card (max-width: 399px) {  
  .card-content {  
    flex-direction: column;  
    gap: var(--spacing-2);  
  }  
}  

Use container queries for:
    Cards that appear in grids AND standalone
    Sidebar content that changes width
    Components reused across different sections

5. Advanced hover/focus states
Elevate interaction states beyond basic color change:

/* Service card — Precision profile */  
.service-card {  
  position: relative;  
  overflow: hidden;  
  transition: transform 200ms ease-out, box-shadow 200ms ease-out;  
}  
.service-card::before {  
  content: '';  
  position: absolute;  
  top: 0;  
  left: 0;  
  right: 0;  
  height: 2px;  
  background: var(--color-primary);  
  transform: scaleX(0);  
  transition: transform 300ms ease-out;  
}  
.service-card:hover {  
  transform: translateY(-2px);  
  box-shadow: var(--shadow-elevated);  
}  
.service-card:hover::before {  
  transform: scaleX(1);  
}  
  
/* Focus-visible for keyboard users */  
.service-card:focus-visible {  
  outline: 2px solid var(--color-primary);  
  outline-offset: 2px;  
}  

6. Profile-specific component details
Precision

/* Thin top accent on cards */  
border-top: 2px solid var(--color-primary);  
  
/* Subtle grid pattern background */  
background-image:   
  linear-gradient(rgba(0,0,0,0.03) 1px, transparent 1px),  
  linear-gradient(90deg, rgba(0,0,0,0.03) 1px, transparent 1px);  
background-size: 20px 20px;  
  
/* Monospace for data elements */  
.data-value { font-family: var(--font-mono); font-variant-numeric: tabular-nums; }  

Warmth

/* Soft organic border */  
border-radius: 1rem 0.25rem 1rem 0.25rem;  
  
/* Warm shadow with color */  
box-shadow: 0 4px 16px rgba(var(--color-primary-rgb), 0.08);  
  
/* Handwritten underline effect on headings */  
.heading-accent {  
  background-image: url("data:image/svg+xml,..."); /* wavy line SVG */  
  background-position: bottom;  
  background-repeat: no-repeat;  
  padding-bottom: 0.25em;  
}  

Authority

/* Bold left border accent */  
border-left: 4px solid var(--color-primary);  
  
/* Dark overlay on hover */  
.card-overlay {  
  background: linear-gradient(to top, rgba(0,0,0,0.7) 0%, transparent 100%);  
}  
  
/* Strong geometric decoration */  
.section-accent::after {  
  content: '';  
  display: block;  
  width: 3rem;  
  height: 3px;  
  background: var(--color-primary);  
  margin-top: var(--spacing-4);  
}  

Energy

/* Gradient border effect */  
border: 2px solid transparent;  
background-clip: padding-box;  
background-image: linear-gradient(var(--color-background), var(--color-background)),  
                  linear-gradient(135deg, var(--color-primary), var(--color-accent));  
background-origin: border-box;  
  
/* Rotation on hover */  
.icon-container:hover {  
  transform: rotate(5deg) scale(1.05);  
}  
  
/* Animated gradient accent */  
@keyframes gradient-shift {  
  0% { background-position: 0% 50%; }  
  100% { background-position: 100% 50%; }  
}  
.accent-bar {  
  background: linear-gradient(90deg, var(--color-primary), var(--color-accent), var(--color-primary));  
  background-size: 200% 100%;  
  animation: gradient-shift 3s ease infinite;  
  height: 3px;  
}  

Component-level checklist
For EACH component file, verify:
    Zero hardcoded colors — all use design tokens
    Zero magic number spacing — all use spacing scale or clamp
    Fluid typography where text size changes across breakpoints
    Hover state differs from default and communicates interactivity
    Focus-visible state is visible and on-brand
    Component renders correctly at 320px and 1920px
    No horizontal scroll at any breakpoint
    Touch targets ≥44px on viewports ≤768px
    At least one profile-specific detail that makes it non-generic
    Transitions use ease-out and ≤300ms (no sluggish animations)
    No !important unless overriding third-party styles

Edit protocol
    One component at a time. Complete all enhancements for a component before moving to the next.
    Preserve structure. Do not change HTML semantics or data bindings.
    Test at 320px and 1440px minimum after each edit.
    Log every change with file path, line, and rationale.

Output
Write component-log-[business-slug].md with:

## Component enhancement summary  
- Components audited: [count]  
- Components modified: [count]  
- CSS issues fixed: [count]  
- Responsive fixes: [count]  
- Profile details added: [count]  
  
## Changes by component  
### [ComponentName].astro  
- **File:** `src/components/[path]/[Name].astro`  
- **Changes:** [list of specific changes]  
- **Profile detail:** [what was added to make it niche-specific]  

Rules

    Tokens, not values. Every color, spacing, and font-size must reference the design system. Zero exceptions.
    Fluid over breakpoints. Prefer clamp() over media queries for typography and spacing. Media queries only for layout changes.
    Isolation is sacred. A component must work if dropped into a different section. No dependencies on parent styles outside the design system.
    Profile is visible. Someone reviewing a single component should be able to guess the visual profile from its CSS. If all profiles look the same at component level, this skill failed.
    Performance budget. No animation that triggers layout or paint on scroll. Transitions on transform and opacity only. No box-shadow transitions on mobile.
    Never remove accessibility. If a component has ARIA attributes, semantic HTML, or keyboard handlers, they stay. Enhancements are visual only.