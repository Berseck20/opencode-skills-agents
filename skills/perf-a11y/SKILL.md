---  
name: perf-a11y  
description: Performs a comprehensive performance and accessibility audit on the built Astro landing page. Validates WCAG 2.1 AA compliance, Core Web Vitals optimization, semantic HTML, keyboard navigation, screen reader compatibility, and loading performance. Produces a prioritized fix list with exact code changes.  
compatibility: opencode  
metadata:  
  domain: qa  
  agent: error-finder  
---  
  
## What I do  
  
- Audit the complete page for WCAG 2.1 AA accessibility compliance  
- Analyze performance bottlenecks affecting Core Web Vitals (LCP, CLS, INP)  
- Validate semantic HTML structure for screen readers and assistive tech  
- Check keyboard navigation flow and focus management  
- Verify color contrast ratios across all text/background combinations  
- Audit loading strategy (critical CSS, font loading, image optimization, script deferral)  
- Produce a prioritized fix list with exact code for every issue  
  
## When to use me  
  
Use this skill as the second step in the `error-finder` workflow, after `code-audit` has completed. Code-audit catches broken code; this skill catches invisible barriers and slowness.  
  
Requires:  
- Complete Astro project (post-rebuild)  
- `audit-report-[business-slug].md` (from code-audit)  
- Active visual profile and design tokens  
  
## Accessibility audit  
  
### A. Semantic structure  

| Check              | Requirement                                       | How to verify                                            |
|--------------------|---------------------------------------------------|----------------------------------------------------------|
| Heading hierarchy  | h1 → h2 → h3, no skipped levels                   | Read all headings in order — must form a logical outline |
| Landmark regions   | <header>, <nav>, <main>, <footer> present         | One <main>, at least one <nav>                           |
| Section labeling   | Every <section> has aria-labelledby or aria-label | Screen reader must announce section purpose              |
| List usage         | Related items use <ul>/<ol>, not <div> chains     | Services, features, nav links = lists                    |
| Table usage        | Tabular data uses <table> with <th> and scope     | If data is comparative, it belongs in a table            |
| Language attribute | <html lang="en"> present                          | Must match page content language                         |
| Page title         | <title> is descriptive and unique                 | Not "Home" or "Landing Page"                             |

B. Keyboard navigation

Test the complete keyboard flow:
Tab → first focusable element  
Tab → through all interactive elements in visual order  
Shift+Tab → reverse navigation  
Enter → activates buttons and links  
Space → activates buttons, toggles checkboxes  
Escape → closes modals, dropdowns, menus  

| Check                | Requirement                                                   |
|----------------------|---------------------------------------------------------------|
| Tab order            | Matches visual layout order — no jumps                        |
| Focus visibility     | Every focused element has a visible indicator                 |
| Focus trap           | Modals trap focus inside; escape releases                     |
| Skip link            | First tab stop is "Skip to main content"                      |
| No tab traps         | User can tab through entire page without getting stuck        |
| Interactive elements | All clickable elements are <a> or <button>, not <div onclick> |
| Custom controls      | Custom components (accordion, tabs) follow WAI-ARIA patterns  |

C. Color contrast

Verify every text/background combination:

| Standard         | Ratio required | Applies to                    |
|------------------|----------------|-------------------------------|
| AA Normal text   | ≥ 4.5:1        | Body text, paragraphs, labels |
| AA Large text    | ≥ 3:1          | Headings ≥18pt or ≥14pt bold  |
| AA UI components | ≥ 3:1          | Borders, icons, form controls |
| AAA Normal text  | ≥ 7:1          | Target for critical content   |

Check these common failures:

- Light gray text on white background  
- Placeholder text contrast  
- Disabled state contrast (still needs 3:1 against background)  
- Text over gradient backgrounds (check darkest AND lightest point)  
- Text over image placeholders  
- CTA button text against button background  
- Link text vs surrounding text (must be distinguishable without color alone)  

Contrast calculation formula:

L1 = lighter relative luminance  
L2 = darker relative luminance  
Ratio = (L1 + 0.05) / (L2 + 0.05)  
For each design token combination in the palette, compute and record the ratio.

D. Images and media

| Check             | Requirement                                                   |
|-------------------|---------------------------------------------------------------|
| Alt text          | Every <img> has meaningful alt (not "image", "photo", "icon") |
| Decorative images | Purely decorative images use alt="" and role="presentation"   |
| SVG accessibility | Inline SVGs have role="img" and <title> or aria-label         |
| Icon buttons      | Icon-only buttons have aria-label describing the action       |
| Complex images    | Charts/infographics have text alternative or aria-describedby |
| Image of text     | No images containing text (use real text)                     |

E. Forms
| Check           | Requirement                                                           |
|-----------------|-----------------------------------------------------------------------|
| Labels          | Every input has visible <label> with matching for/id                  |
| Error messages  | Errors announced via aria-live="polite" or aria-describedby           |
| Required fields | Marked with aria-required="true", not just visual asterisk            |
| Input types     | Correct type attribute (email, tel, url) for mobile keyboards         |
| Autocomplete    | Common fields have autocomplete attribute (name, email, tel, address) |
| Submit feedback | Form submission state communicated to screen readers                  |

F. Motion and animation

| Check                | Requirement                                                              |
|----------------------|--------------------------------------------------------------------------|
| Reduced motion       | @media (prefers-reduced-motion: reduce) disables non-essential animation |
| Auto-playing content | No auto-playing carousels or videos without pause control                |
| Flashing content     | No content flashes more than 3 times per second                          |
| Parallax             | Disabled under reduced motion preference                                 |

Required implementation:
css
Copy
@media (prefers-reduced-motion: reduce) {  
  *,  
  *::before,  
  *::after {  
    animation-duration: 0.01ms !important;  
    animation-iteration-count: 1 !important;  
    transition-duration: 0.01ms !important;  
    scroll-behavior: auto !important;  
  }  
}  

Performance audit
A. Core Web Vitals targets

| Metric                          | Good    | Needs improvement | Poor    |
|---------------------------------|---------|-------------------|---------|
| LCP (Largest Contentful Paint)  | ≤ 2.5s  | ≤ 4.0s            | > 4.0s  |
| CLS (Cumulative Layout Shift)   | ≤ 0.1   | ≤ 0.25            | > 0.25  |
| INP (Interaction to Next Paint) | ≤ 200ms | ≤ 500ms           | > 500ms |

B. LCP optimization

| Check                     | What to look for                                               |
|---------------------------|----------------------------------------------------------------|
| Hero image loading        | Hero image uses loading="eager" and fetchpriority="high"       |
| Font loading              | Primary font uses <link rel="preload"> with font-display: swap |
| Critical CSS              | Above-fold styles are inlined or loaded first                  |
| Render-blocking resources | No render-blocking JS or CSS in <head> without defer/async     |
| Server response           | No unnecessary redirects in asset loading                      |
| Image format              | Hero image is WebP with JPEG fallback                          |
| Image sizing              | Hero image srcset includes correct breakpoint sizes            |

C. CLS prevention

| Check              | What to look for                                      |
|--------------------|-------------------------------------------------------|
| Image dimensions   | Every <img> has explicit width and height attributes  |
| Font swap flash    | Font loading doesn't cause visible text reflow        |
| Dynamic content    | No content injected above existing content after load |
| Ad/embed space     | Third-party embeds (maps, forms) have reserved space  |
| Aspect ratio boxes | Image containers use aspect-ratio CSS property        |
| Web font metrics   | size-adjust and ascent-override on fallback font      |

D. Loading strategy

Verify the loading waterfall:
1. Critical CSS (inlined in <head>)  
2. Primary font (preloaded)  
3. Hero image (eager, high priority)  
4. Page JS (deferred)  
5. Below-fold images (lazy)  
6. Third-party scripts (async, after load)  
7. Analytics (after everything else)  

| Resource type     | Loading strategy                                    |
|-------------------|-----------------------------------------------------|
| Fonts             | <link rel="preload" as="font" crossorigin>          |
| Hero image        | <img loading="eager" fetchpriority="high">          |
| Below-fold images | <img loading="lazy">                                |
| CSS               | Critical inlined, rest async                        |
| JS                | defer on all scripts, no async on dependent scripts |
| Third-party       | Load after DOMContentLoaded or on interaction       |
| Google Maps embed | Load on scroll into view or on click                |

E. Asset optimization

| Asset             | Max size target          | Format             |
|-------------------|--------------------------|--------------------|
| Total page weight | ≤ 500KB (without images) | —                  |
| HTML document     | ≤ 50KB                   | Gzipped            |
| CSS total         | ≤ 50KB                   | Minified + Gzipped |
| JS total          | ≤ 100KB                  | Minified + Gzipped |
| Hero image        | ≤ 200KB                  | WebP               |
| Card images       | ≤ 80KB each              | WebP               |
| Fonts             | ≤ 50KB per font file     | WOFF2              |
| Favicon           | ≤ 5KB                    | SVG or ICO         |

F. Meta and SEO performance

| Check            | Requirement                                                          |
|------------------|----------------------------------------------------------------------|
| Meta description | Present, 150-160 characters                                          |
| Open Graph tags  | og:title, og:description, og:image, og:url                           |
| Canonical URL    | <link rel="canonical"> present                                       |
| Robots           | No accidental noindex                                                |
| Structured data  | LocalBusiness JSON-LD is valid                                       |
| Sitemap          | Referenced or exists                                                 |
| Mobile viewport  | <meta name="viewport" content="width=device-width, initial-scale=1"> |

Severity classification

| Severity   | Accessibility                                                                | Performance                                       |
|------------|------------------------------------------------------------------------------|---------------------------------------------------|
| 🔴 CRITICAL | Entire section inaccessible to screen readers; keyboard trap; no alt on hero | LCP > 4s; render-blocking resource; CLS > 0.25    |
| 🟠 HIGH     | Missing form labels; contrast failure on body text; no skip link             | LCP > 2.5s; unsized images; no lazy loading       |
| 🟡 MEDIUM   | Missing aria-label on section; decorative image with alt text                | Page weight over budget; unoptimized font loading |
| 🔵 LOW      | AAA contrast not met; minor heading order preference                         | Minor optimization opportunity                    |

Output format
Write perf-a11y-report-[business-slug].md:

## Audit summary  
- Accessibility issues: [count]  
  - 🔴 Critical: [count]  
  - 🟠 High: [count]  
  - 🟡 Medium: [count]  
  - 🔵 Low: [count]  
- Performance issues: [count]  
  - 🔴 Critical: [count]  
  - 🟠 High: [count]  
  - 🟡 Medium: [count]  
  - 🔵 Low: [count]  
- Estimated Lighthouse scores:  
  - Performance: [X]/100  
  - Accessibility: [X]/100  
  - Best Practices: [X]/100  
  - SEO: [X]/100  
  
## Accessibility issues  
  
### [A11Y-001] [Short description]  
- **Severity:** 🔴 CRITICAL  
- **Category:** [Semantic | Keyboard | Contrast | Images | Forms | Motion]  
- **File:** `[path]`  
- **Line:** [number]  
- **WCAG criterion:** [e.g., 1.1.1 Non-text Content]  
- **Issue:** [What's wrong]  
- **Impact:** [Who is affected and how]  
- **Fix:**  
```[language]  
[exact code change]``` 

Performance issues
[PERF-001] [Short description]

    Severity: 🟠 HIGH

    Category: [LCP | CLS | INP | Loading | Assets | Meta]

    File: [path]

    Line: [number]

    Metric impact: [Which Core Web Vital is affected]

    Issue: [What's wrong]

    Fix:

[exact code change]  

WCAG 2.1 AA compliance checklist

    1.1.1 Non-text Content

    1.3.1 Info and Relationships

    1.4.3 Contrast (Minimum)

    2.1.1 Keyboard

    2.4.1 Bypass Blocks

    2.4.7 Focus Visible

    3.3.2 Labels or Instructions

    4.1.2 Name, Role, Value
    [... complete relevant criteria]

  
## Rules  
  
1. **Every issue has a WCAG criterion or Web Vital reference.** No vague "improve accessibility." Cite the specific standard being violated.  
2. **Every fix is deployable code.** The developer copies the fix, pastes it, and the issue is resolved. No "consider adding" — provide the exact code.  
3. **Contrast is math, not opinion.** Calculate actual ratios. Don't say "looks low" — say "ratio is 3.2:1, needs 4.5:1."  
4. **Performance is measurable.** Cite file sizes, loading order, and specific metrics. No "could be faster."  
5. **Accessibility is not optional.** ADA lawsuits against local businesses are real. Every CRITICAL and HIGH a11y issue is a legal risk, not a nice-to-have.  
6. **Test the real experience.** Don't just check for `aria-label` existence — verify it makes sense when read aloud. "Click here" is not accessible even with perfect markup.