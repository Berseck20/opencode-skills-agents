---  
name: code-audit  
description: Performs a full automated code audit on the built Astro project — detects broken markup, invalid CSS, runtime errors, missing assets, data binding failures, and visual inconsistencies that would break or degrade the landing page in production.  
compatibility: opencode  
metadata:  
  domain: qa  
  agent: error-finder  
---  
  
## What I do  
  
- Scan every file in the Astro project for syntax errors, broken references, and invalid code  
- Detect HTML/CSS issues that cause visual breakage or layout shifts  
- Validate data bindings between components and data files  
- Check asset references (images, fonts, icons) for missing or broken paths  
- Identify build-breaking errors before deployment  
- Flag visual inconsistencies that degrade perceived quality  
  
## When to use me  
  
Use this skill as the first step in the `error-finder` agent workflow. Run it on the project after `rebuild-landing` has completed all enhancements.  
  
Requires:  
- Complete Astro project (post-rebuild)  
- All data files in `src/data/`  
- All component files in `src/components/`  
  
## Audit categories  
  
### 1. Build integrity  
  
Scan for errors that prevent the project from building:  
  

Priority: CRITICAL — page will not deploy if these exist

| Check                | What to look for                                       |
|----------------------|--------------------------------------------------------|
| Import resolution    | Every import resolves to an existing file              |
| Component references | Every <Component /> has a matching .astro or .tsx file |
| Data file parsing    | Every .json / .ts data file is valid and parseable     |
| Astro frontmatter    | No syntax errors in --- blocks                         |
| TypeScript errors    | No type errors in .ts data files or utilities          |
| Config validity      | astro.config.mjs and tailwind.config.mjs are valid     |
| Package dependencies | Every imported package exists in package.json          |

2. HTML validity
Priority: HIGH — broken HTML causes rendering issues  

| Check                       | What to look for                                             |
|-----------------------------|--------------------------------------------------------------|
| Unclosed tags               | Every opening tag has a matching close (or is self-closing)  |
| Nesting rules               | No <p> inside <p>, no block elements inside inline           |
| Duplicate IDs               | Every id attribute is unique across the page                 |
| Missing required attributes | <img> has alt, width, height; <a> has href                   |
| Empty elements              | No empty <a>, <button>, or heading tags                      |
| Deprecated elements         | No <center>, <font>, <marquee>                               |
| Form structure              | Every <input> has associated <label>                         |
| Semantic structure          | Single <main>, logical heading hierarchy (no skipped levels) |

3. CSS validity
Priority: HIGH — broken CSS causes visual breakage  

| Check                       | What to look for                                                       |
|-----------------------------|------------------------------------------------------------------------|
| Undefined custom properties | Every var(--*) references a defined property                           |
| Invalid values              | No width: autopx, no color: undefined                                  |
| Specificity conflicts       | No !important overriding design tokens                                 |
| Orphaned styles             | Classes defined but never used in markup                               |
| Missing fallbacks           | Custom properties have fallback values for older browsers              |
| Z-index chaos               | Z-index values follow a defined scale, no z-[9999]                     |
| Print styles                | No critical content hidden by default in print                         |
| Tailwind conflicts          | No conflicting utility classes on same element (text-left text-center) |

4. Asset integrity
Priority: HIGH — missing assets cause visual holes  

| Check              | What to look for                                              |
|--------------------|---------------------------------------------------------------|
| Image paths        | Every src attribute resolves to an existing file or valid URL |
| Font loading       | Every @font-face or Google Fonts import resolves              |
| Icon references    | Every SVG icon referenced exists inline or as a file          |
| Favicon            | favicon.ico or favicon.svg exists in public/                  |
| OG image           | Open Graph image path is valid                                |
| Placeholder images | Gradient placeholders render (valid CSS syntax)               |

5. Data binding validation
Priority: CRITICAL — broken bindings cause empty or broken sections  

| Check                 | What to look for                                             |
|-----------------------|--------------------------------------------------------------|
| Data file imports     | Components that import data files reference existing exports |
| Array iterations      | Every .map() / {#each} has data to iterate                   |
| Conditional rendering | {#if} / ternary conditions reference existing properties     |
| String interpolation  | Template literals reference defined variables                |
| Null/undefined guards | Dynamic content handles missing data gracefully              |
| Type mismatches       | Data shapes match component expectations                     |

For each data binding, trace the chain:
data file → export → import → destructure → render  
If any link is broken, flag it.

6. Visual consistency
Priority: MEDIUM — doesn't break the page but degrades quality  

| Check                  | What to look for                                                 |
|------------------------|------------------------------------------------------------------|
| Spacing inconsistency  | Same component type uses different spacing in different sections |
| Color misuse           | Colors outside the design token palette                          |
| Typography drift       | Font sizes/weights not in the type scale                         |
| Border radius mismatch | Same component type with different radius values                 |
| Shadow inconsistency   | Multiple shadow definitions for same depth level                 |
| Alignment issues       | Elements that should align visually but don't                    |
| Icon size variation    | Same icon set with inconsistent sizing                           |
| Button variants        | Same button role with different styling                          |

7. Responsive breakage
Priority: HIGH — mobile users see broken layouts  

| Check                      | What to look for                                                           |
|----------------------------|----------------------------------------------------------------------------|
| Horizontal overflow        | Content wider than viewport at any breakpoint                              |
| Text overflow              | Text that overflows its container without overflow-hidden or text-ellipsis |
| Image overflow             | Images without max-width: 100%                                             |
| Fixed widths               | Elements with w-[600px] that break on mobile                               |
| Missing responsive classes | Desktop-only layouts without mobile alternatives                           |
| Touch target size          | Interactive elements < 44×44px on mobile                                   |
| Viewport meta              | <meta name="viewport"> is present and correct                              |
| Font size minimum          | No text smaller than 14px on mobile                                        |

8. Link and navigation
Priority: HIGH — broken links lose customers  

| Check           | What to look for                                                  |
|-----------------|-------------------------------------------------------------------|
| Dead links      | href pointing to non-existent pages or anchors                    |
| Anchor targets  | Every href="#id" has a matching id on the page                    |
| External links  | External links have target="_blank" and rel="noopener noreferrer" |
| Phone links     | tel: links have valid phone number format                         |
| Email links     | mailto: links have valid email format                             |
| CTA links       | Every CTA button has a functional destination                     |
| Skip navigation | Skip-to-main-content link exists and works                        |

Severity classification
Every issue gets a severity:

| Severity    | Definition                                       | Action                     |
|-------------|--------------------------------------------------|----------------------------|
| 🔴 CRITICAL | Page won't build or section is completely broken | Must fix before deployment |
| 🟠 HIGH     | Visible breakage on common devices/browsers      | Must fix before delivery   |
| 🟡 MEDIUM   | Visual inconsistency or quality degradation      | Should fix                 |
| 🔵 LOW      | Minor improvement opportunity                    | Nice to have               |

Scan protocol

Phase 1 — Static analysis
Read every file without running the project:
    Parse all .astro files for HTML/CSS/JS errors
    Validate all data files for JSON/TS syntax
    Trace all imports and references
    Check all asset paths

Phase 2 — Cross-reference
Check relationships between files:
    Map every component → data file dependency
    Map every component → component dependency
    Verify every route → page → layout chain
    Validate config files against project structure

Phase 3 — Visual inspection
Review rendered output logic:
    Check responsive class coverage per component
    Verify spacing/color/typography consistency
    Validate interaction states exist (hover, focus, active)
    Check section transitions and flow

Output format
Write audit-report-[business-slug].md:

## Audit summary  
- Files scanned: [count]  
- Issues found: [count]  
  - 🔴 Critical: [count]  
  - 🟠 High: [count]  
  - 🟡 Medium: [count]  
  - 🔵 Low: [count]  
  
## Critical issues  
### [ISSUE-001] [Short description]  
- **Severity:** 🔴 CRITICAL  
- **File:** `[path]`  
- **Line:** [number]  
- **Issue:** [Detailed description of what's wrong]  
- **Impact:** [What breaks if not fixed]  
- **Fix:** [Exact code change needed]  
  
## High issues  
### [ISSUE-002] ...  
[same format]  
  
## Medium issues  
[same format]  
  
## Low issues  
[same format]  
  
## Files with zero issues  
- [list of clean files]  

Rules
    Every issue has a fix. Do not flag problems without providing the exact code change to resolve them. An audit that says "fix this" without showing how is useless.
    Severity is objective. CRITICAL means the build fails or a section is blank. Don't inflate severity for minor issues.
    Trace, don't assume. Before flagging a broken import, verify the file doesn't exist. Before flagging unused CSS, verify no dynamic class application.
    Zero false positives. Every flagged issue must be reproducible. If you're not 100% certain it's a real issue, don't include it.
    Data bindings are sacred. The most common post-enhancement bug is a broken data binding. Check every single one, every property, every array.
    Mobile is not optional. If something works on desktop but breaks at 375px, it's a HIGH issue. Most visitors to local business sites are on phones.