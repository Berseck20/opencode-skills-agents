---  
name: astro-builder  
description: Takes the landing architecture blueprint and structured data files to produce a complete, production-ready Astro + React + Tailwind landing page. Generates project scaffolding, Tailwind config, layouts, pages, and every component with proper hydration, responsive behavior, and accessibility.  
compatibility: opencode  
metadata:  
  domain: builder  
  agent: landing-base-builder  
---  
  
## What I do  
  
- Scaffold a complete Astro project with React and Tailwind CSS integration  
- Generate the Tailwind configuration from design tokens defined in the architecture  
- Build every component specified in the architecture blueprint  
- Wire all components to the structured data files from `data-extractor`  
- Apply proper hydration directives per component specification  
- Implement responsive behavior at every breakpoint  
- Set up SEO metadata, schema markup, and Open Graph tags  
- Produce code that runs on first `npm install && npm run dev` — no manual fixes needed  
  
## When to use me  
Use this skill as the final step in the `landing-base-builder` agent workflow, after:  
1. `landing-architecture` has produced the blueprint (including the header block with Pattern ID, Layout Variant ID, and Variation Axes)  
2. `visual-system` has been loaded as the active design rule  
3. `data-extractor` has created all `src/data/*.ts` files  
Never start building without all three prerequisites complete.  
  
### Pre-build checklist  
Before writing any code, extract from the architecture blueprint:  
- **Layout Variant ID** (e.g., `W-story`, `A-impact`, `P-split`) → determines hero structure, grid strategy, and section dividers  
- **CTA formats** → each CTA instance uses a different format (button, sticky-bar, inline-link, etc.)  
- **Section count** → build exactly this many sections, no more  
- **Variation Axes choices** → apply these structural decisions throughout  
  
If any of these are missing from the architecture, STOP and request a complete blueprint. Do not assume defaults.  
  
Never start building without all three prerequisites complete.  
  
## Hero implementation by layout variant  
The hero is NOT a single template with swapped content. Each layout variant defines a different hero structure:

| Variant pattern     | HTML structure                                   | Key difference                              |
|---------------------|--------------------------------------------------|---------------------------------------------|
| *-clean, *-minimal  | Single centered column, text only, CTA below     | No image, maximum whitespace                |
| *-split, *-grid     | CSS Grid 2-col (text left, image/visual right)   | Asymmetric columns (60/40 or 50/50)         |
| *-story, *-personal | Full-width image with overlay text container     | Image is background, text has scrim/overlay |
| *-impact, *-bold    | Full-bleed dark section, oversized H1, stats row | Typography-driven, no hero image            |
| *-showcase*          | Video embed or image carousel as hero background | Media-first, text is secondary              |
| *-data*              | Split with KPI cards alongside headline          | Data-forward, dashboard aesthetic           |
| *-dynamic*           | Animated gradient or parallax background         | Motion-first, text floats over animation    |

Rule: Read the variant ID from the architecture. Build the matching hero structure. Do not default to "centered text + button" for every landing.



## Project scaffolding  
  
### Directory structure  
  

project-root/
├── astro.config.mjs
├── tailwind.config.mjs
├── tsconfig.json
├── package.json
├── public/
│ ├── favicon.svg
│ └── fonts/ # Only if self-hosting fonts
├── src/
│ ├── components/
│ │ ├── sections/ # Full page sections (Hero, Services, etc.)
│ │ ├── ui/ # Reusable UI primitives (Button, Card, Badge, etc.)
│ │ └── layout/ # Nav, Footer, Container
│ ├── data/ # Already created by data-extractor
│ ├── layouts/
│ │ └── Layout.astro # Base HTML layout
│ ├── pages/
│ │ └── index.astro # Landing page
│ └── styles/
│ └── global.css # Tailwind directives + custom properties
└── research-[slug].md # Read-only research document

  
### `package.json`  
  
```json  
{  
  "name": "[business-slug]-landing",  
  "type": "module",  
  "version": "1.0.0",  
  "scripts": {  
    "dev": "astro dev",  
    "build": "astro build",  
    "preview": "astro preview"  
  },  
  "dependencies": {  
    "astro": "^5.x",  
    "@astrojs/react": "^4.x",  
    "@astrojs/tailwind": "^6.x",  
    "react": "^19.x",  
    "react-dom": "^19.x"  
  },  
  "devDependencies": {  
    "@types/react": "^19.x",  
    "@types/react-dom": "^19.x",  
    "tailwindcss": "^4.x",  
    "typescript": "^5.x"  
  }  
}```  
Rule: Use current stable versions at time of generation. No pinned patch versions — use caret ranges.

astro.config.mjs

```import { defineConfig } from 'astro/config'  
import react from '@astrojs/react'  
import tailwind from '@astrojs/tailwind'  
  
export default defineConfig({  
  integrations: [react(), tailwind()],  
  output: 'static',  
})```  

tsconfig.json

```{  
  "extends": "astro/tsconfigs/strict",  
  "compilerOptions": {  
    "jsx": "react-jsx",  
    "baseUrl": ".",  
    "paths": {  
      "@/*": ["src/*"],  
      "@components/*": ["src/components/*"],  
      "@data/*": ["src/data/*"],  
      "@layouts/*": ["src/layouts/*"]  
    }  
  }  
}```  

Tailwind configuration

Generate tailwind.config.mjs from the architecture's design tokens:

```/** @type {import('tailwindcss').Config} */  
export default {  
  content: ['./src/**/*.{astro,html,js,jsx,ts,tsx}'],  
  theme: {  
    extend: {  
      colors: {  
        // ALL color tokens from architecture — no unnamed values  
        primary: {  
          DEFAULT: '[token]',  
          light: '[token]',  
          dark: '[token]',  
        },  
        secondary: '[token]',  
        accent: '[token]',  
        background: '[token]',  
        surface: {  
          DEFAULT: '[token]',  
          dark: '[token]',  
        },  
        'text-primary': '[token]',  
        'text-secondary': '[token]',  
        'text-on-primary': '[token]',  
        'text-on-dark': '[token]',  
        border: '[token]',  
      },  
      fontFamily: {  
        heading: ['[heading font]', 'sans-serif'],  
        body: ['[body font]', 'sans-serif'],  
      },  
      fontSize: {  
        // Complete type scale with line-height and letter-spacing  
        h1: ['[size]', { lineHeight: '[lh]', letterSpacing: '[ls]' }],  
        h2: ['[size]', { lineHeight: '[lh]', letterSpacing: '[ls]' }],  
        h3: ['[size]', { lineHeight: '[lh]', letterSpacing: '[ls]' }],  
        body: ['[size]', { lineHeight: '[lh]' }],  
        'body-sm': ['[size]', { lineHeight: '[lh]' }],  
        label: ['[size]', { lineHeight: '[lh]', letterSpacing: '[ls]' }],  
        caption: ['[size]', { lineHeight: '[lh]' }],  
      },  
      borderRadius: {  
        sm: '[token]',  
        md: '[token]',  
        lg: '[token]',  
      },  
      boxShadow: {  
        sm: '[token]',  
        md: '[token]',  
        lg: '[token]',  
      },  
    },  
  },  
  plugins: [],  
}```  
Rule: Every value is a token from the architecture. If a value isn't in the architecture, it doesn't go in the config.

Global styles
src/styles/global.css

```
@tailwind base;  
@tailwind components;  
@tailwind utilities;  
  
@layer base {  
  /* Google Fonts import — URL from architecture typography tokens */  
  @import url('[google-fonts-url]');  
  
  html {  
    scroll-behavior: smooth;  
    -webkit-font-smoothing: antialiased;  
    -moz-osx-font-smoothing: grayscale;  
  }  
  
  body {  
    @apply bg-background text-text-primary font-body text-body;  
  }  
  
  h1, h2, h3, h4, h5, h6 {  
    @apply font-heading;  
  }  
  
  /* Reduced motion */  
  @media (prefers-reduced-motion: reduce) {  
    *, *::before, *::after {  
      animation-duration: 0.01ms !important;  
      animation-iteration-count: 1 !important;  
      transition-duration: 0.01ms !important;  
      scroll-behavior: auto !important;  
    }  
  }  
}```  

Base layout
src/layouts/Layout.astro

```---  
import '@/styles/global.css'  
import { seo } from '@data/seo'  
  
interface Props {  
  title?: string  
  description?: string  
}  
  
const {   
  title = seo.title,   
  description = seo.description   
} = Astro.props  

---  
  
<!doctype html>  
<html lang="en">  
  <head>  
    <meta charset="UTF-8" />  
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />  
    <meta name="description" content={description} />  
    <link rel="canonical" href={seo.canonical} />  
  
    <!-- Open Graph -->  
    <meta property="og:title" content={seo.openGraph.title} />  
    <meta property="og:description" content={seo.openGraph.description} />  
    <meta property="og:type" content={seo.openGraph.type} />  
    <meta property="og:locale" content={seo.openGraph.locale} />  
    <meta property="og:site_name" content={seo.openGraph.siteName} />  
    {seo.openGraph.image && <meta property="og:image" content={seo.openGraph.image} />}  
  
    <!-- Fonts preload -->  
    <link rel="preconnect" href="https://fonts.googleapis.com" />  
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />  
  
    <!-- Schema.org JSON-LD -->  
    <script type="application/ld+json" set:html={JSON.stringify(seo.schema.localBusiness)} />  
    {seo.schema.faq && (  
      <script type="application/ld+json" set:html={JSON.stringify(seo.schema.faq)} />  
    )}  
  
    <link rel="icon" type="image/svg+xml" href="/favicon.svg" />  
    <title>{title}</title>  
  </head>  
  <body>  
    <slot />  
  </body>  
</html>```

Component building rules

Astro vs React decision

| Scenario                            | Technology               | Reason                                |
|-------------------------------------|--------------------------|---------------------------------------|
| Static section with no interaction  | .astro component         | Zero JS, best performance             |
| Section with hover CSS effects only | .astro component         | CSS handles it, no JS needed          |
| Mobile navigation menu              | .tsx React component     | Requires state for open/close         |
| Form with validation                | .tsx React component     | Requires state and event handling     |
| Carousel / slider                   | .tsx React component     | Requires state for active slide       |
| Scroll-triggered animations         | .astro + inline <script> | IntersectionObserver, no React needed |
| Everything else                     | .astro component         | Default to static                     |

Component template — Astro section

```
---  
// src/components/sections/Services.astro  
import { services } from '@data/services'  
import ServiceCard from '@components/ui/ServiceCard.astro'  
---  
  
{services.length > 0 && (  
  <section id="services" class="py-section bg-surface">  
    <div class="max-w-container mx-auto px-container">  
      <h2 class="font-heading text-h2 font-semibold text-text-primary mb-stack">  
        {/* H2 text from content strategy */}  
      </h2>  
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-component">  
        {services.map((service) => (  
          <ServiceCard service={service} />  
        ))}  
      </div>  
    </div>  
  </section>  
)}```  

Component template — React interactive

```// src/components/layout/MobileNav.tsx  
import { useState } from 'react'  
import { navigation, cta } from '@data/navigation'  
  
export default function MobileNav() {  
  const [isOpen, setIsOpen] = useState(false)  
  
  const visibleItems = navigation.filter((item) => item.isVisible)  
  
  return (  
    <div className="md:hidden">  
      <button  
        onClick={() => setIsOpen(!isOpen)}  
        aria-expanded={isOpen}  
        aria-controls="mobile-menu"  
        aria-label={isOpen ? 'Close menu' : 'Open menu'}  
        className="p-2 text-text-primary"  
      >  
        {/* Hamburger icon — SVG inline, not an icon library */}  
      </button>  
  
      {isOpen && (  
        <div  
          id="mobile-menu"  
          role="navigation"  
          aria-label="Mobile navigation"  
          className="fixed inset-0 z-50 bg-surface"  
        >  
          {/* Navigation items + CTA */}  
        </div>  
      )}  
    </div>  
  )  
}```  

Hydration directives

Apply exactly as specified in the architecture:

<!-- Needed immediately — navigation -->  
<MobileNav client:load />  
  
<!-- Only when visible — below fold interactive -->  
<ContactForm client:visible />  
  
<!-- When browser is idle — non-critical -->  
<MapEmbed client:idle />  
  
<!-- Static sections — NO directive, NO React -->  
<HeroSection />  
<ServicesSection />  
<TestimonialsSection />  
Rule: If a component has no hydration directive in the architecture, it must be an Astro component. Do not wrap static content in React.
Conditional rendering

Follow the contract established by data-extractor:

```---  
import { testimonials } from '@data/testimonials'  
import { team } from '@data/team'  
import { stats } from '@data/stats'  
import { faq } from '@data/faq'  
---  
  
<!-- Only renders if data exists -->  
{testimonials.length > 0 && <TestimonialsSection />}  
{team.length > 0 && <TeamSection />}  
{stats.length > 0 && <StatsSection />}  
{faq.length > 0 && <FAQSection />}```  
Rule: Never render empty sections. Never show placeholder text. If data is null or array is empty, the section does not exist in the DOM.

Scroll animations

Implement with IntersectionObserver, not a library:

```<!-- In Layout.astro, before closing </body> -->  
<script>  
  const observer = new IntersectionObserver(  
    (entries) => {  
      entries.forEach((entry) => {  
        if (entry.isIntersecting) {  
          entry.target.classList.add('revealed')  
          observer.unobserve(entry.target)  
        }  
      })  
    },  
    { threshold: 0.1, rootMargin: '0px 0px -50px 0px' }  
  )  
  
  document.querySelectorAll('[data-reveal]').forEach((el) => {  
    observer.observe(el)  
  })  
</script>```  

```/* In global.css */  
[data-reveal] {  
  opacity: 0;  
  transform: translateY(20px);  
  transition: opacity 0.4s ease-out, transform 0.4s ease-out;  
}  
  
[data-reveal].revealed {  
  opacity: 1;  
  transform: translateY(0);  
}  
  
@media (prefers-reduced-motion: reduce) {  
  [data-reveal] {  
    opacity: 1;  
    transform: none;  
    transition: none;  
  }  
}```  

Usage in sections:

```<section data-reveal>  
  <!-- Content fades in on scroll -->  
</section>```  

Accessibility requirements

Every component must implement:

| Requirement                 | Implementation                                                             |
|-----------------------------|----------------------------------------------------------------------------|
| Single                      | Only in Hero section                                                       |
| Heading hierarchy           | No skipped levels (h1 → h2 → h3)                                           |
| Alt text on images          | Descriptive, from data files                                               |
| ARIA labels on icon buttons | aria-label="[action]"                                                      |
| Focus-visible styles        | focus-visible:ring-2 focus-visible:ring-primary focus-visible:outline-none |
| Skip to content link        | First element in <body>, visually hidden until focused                     |
| Keyboard navigation         | All interactive elements reachable via Tab                                 |
| Form labels                 | Every input has an associated <label>                                      |
| Landmark roles              | <nav>, <main>, <footer> — semantic HTML                                    |
| Language attribute          | <html lang="en">                                                           |

Skip to content
```
<!-- First element in body -->  
<a  
  href="#main-content"  
  class="sr-only focus:not-sr-only focus:fixed focus:top-4 focus:left-4 focus:z-[100] focus:px-4 focus:py-2 focus:bg-primary focus:text-text-on-primary focus:rounded-md"  
>  
  Skip to main content  
</a>
  
<!-- On main content wrapper -->  
<main id="main-content">  
  <slot />  
</main> ``` 

Image handling

Since images are not yet generated at build time:

```<!-- Use placeholder with exact dimensions and aspect ratio -->  
<div  
  class="aspect-video bg-surface rounded-md overflow-hidden"  
  role="img"  
  aria-label="[description from data]"  
>  
  <!-- Image placeholder — replaced by image-strategy skill later -->  
  <div class="w-full h-full bg-gradient-to-br from-surface to-surface-dark flex items-center justify-center">  
    <span class="text-text-secondary text-sm">[Image: {description}]</span>  
  </div>  
</div>```  
Rule: Set explicit width and height or use aspect-* classes on every image container to prevent layout shift. Never leave images unsized.

Page assembly
src/pages/index.astro

```---  
import Layout from '@layouts/Layout.astro'  
// Import all sections in architecture order  
import Navigation from '@components/layout/Navigation.astro'  
import Hero from '@components/sections/Hero.astro'  
// ... all sections from architecture  
import Footer from '@components/layout/Footer.astro'  
  
// Import data for conditional checks  
import { testimonials } from '@data/testimonials'  
import { team } from '@data/team'  
import { stats } from '@data/stats'  
import { faq } from '@data/faq'  
---  
  
<Layout>  
  <Navigation />  
  <main id="main-content">  
    <Hero />  
    <!-- Sections in exact architecture order -->  
    <!-- Conditional sections wrapped in data checks -->  
    {testimonials.length > 0 && <Testimonials />}  
    {team.length > 0 && <Team />}  
    {stats.length > 0 && <Stats />}  
    {faq.length > 0 && <FAQ />}  
  </main>  
  <Footer />  
</Layout>```

## CTA format implementation  
Each CTA in the architecture specifies a format. Implement each format differently:  
  
### `button`  
Standard `<button>` or `<a>` styled as primary button. Already covered by ui/Button component.  
  
### `sticky-bar`  
Fixed-position bar at viewport bottom. Contains CTA text + phone number. Visible after scrolling past hero. Hide on scroll-up, show on scroll-down. Requires React component with `client:load`.  
```astro  
<!-- StickyBar.tsx — client:load -->``` 

###inline-link

Styled <a> tag within paragraph text. Uses accent color, underline on hover. No component needed — just a CSS class.

###floating-badge

Small fixed circle/pill in bottom-right corner. Contains phone icon or short text. Always visible. Requires React with client:load.


###form-embedded

Inline <form> with 2-3 fields (name, phone/email, submit). Styled as a card within the section. Requires React with client:idle.


###phone-tap

Large tap-to-call block. Full-width on mobile, styled as accent background with phone icon + number. Uses <a href="tel:">. Pure Astro component.


###text-banner

Full-width colored strip between sections. Background uses bg-primary or bg-accent. Contains one line of copy + CTA link. Pure Astro component.

Rule: If the architecture says "Format: sticky-bar", build a sticky bar. Do not substitute with a regular button.


Build validation

Before considering the build complete, verify:

    npm install completes without errors
    npm run dev starts without errors
    No TypeScript errors in any file
    All imports resolve (no missing modules)
    All data files are imported and used
    Conditional sections render only when data exists
    Tailwind config reflects architecture tokens exactly
    No default Tailwind colors in any component
    No arbitrary values [#hex] or [Xpx] in components
    Single <h1> on the page
    All interactive elements have ARIA labels
    prefers-reduced-motion handled
    Skip-to-content link present
    Schema JSON-LD renders in <head>
    Google Fonts loaded with correct weights only
    No unused components or imports
    Every React component has an explicit hydration directive

## Anti-patterns  
**Anti-pattern: hero monoculture.** If you build 5 landings and all heroes are "centered H1 + subtitle + button", the implementation has failed. Check the variant ID and build the corresponding structure.  
**Anti-pattern: CTA uniformity.** If every CTA on the page is a `<button class="bg-primary ...">`, the CTA strategy has been ignored. Each CTA instance must look and behave differently per its assigned format.  
**Anti-pattern: section copy-paste.** Sections with different purposes (services vs testimonials vs FAQ) should NOT share the same container → heading → grid → cards skeleton. Each section type has its own layout logic.

Rules

    Architecture is the blueprint. Build exactly what it specifies. Do not add sections, components, or features not in the plan.
    Data files are the single source. Components read from src/data/. No hardcoded strings in components — ever.
    Astro by default, React by necessity. If a component doesn't need client-side state, it's .astro. Period.
    Visual system compliance. Every class must reference a token. The visual-system skill is active — violations will be caught.
    Works on first run. The project must npm install && npm run dev without any manual intervention. Missing deps, broken imports, or type errors mean the build failed.
    Accessibility is not optional. Every requirement in the accessibility table is mandatory. Missing ARIA labels, skipped heading levels, or no skip-to-content link are critical defects.
    No external dependencies beyond the stack. No icon libraries (use inline SVG). No animation libraries (use CSS + IntersectionObserver). No CSS frameworks beyond Tailwind. No utility libraries.
    Images are placeholders. This skill does not generate or source images. It creates properly sized, properly labeled containers that the image strategy will fill later.
    Anti-pattern: god component. If a component file exceeds 150 lines, it should be split into smaller composable parts.
    Anti-pattern: prop drilling. Data files are imported directly by each component. Do not pass business data through 3 levels of props.