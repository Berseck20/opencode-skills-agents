# styles.md — Concrete Style Library for Landing Pages

Reference library of CSS/Tailwind styles, tokens, and implementation patterns for Astro landing pages. Every value is copy-paste ready. No abstractions — only concrete code.

---

## 1. Style Profiles

Each profile is a complete visual DNA. The agent MUST pick ONE profile per landing and apply it consistently. Never mix profiles.

### 1.1 Clean Minimal (Swiss)
```
--bg: #FFFFFF
--fg: #000000
--muted: #F5F1E8
--accent: single saturated color per project
--radius: 0px
--shadow: none
--border: none or 1px solid #E5E5E5
--font-body: sans-serif (geometric)
--font-display: same family, weight contrast
--spacing-scale: 4px base (4,8,12,16,24,32,48,64,96)
--transition: 200-250ms ease-out
```
Tailwind: `bg-white text-black font-sans tracking-tight`
Cards: NO cards. Use spacing and alignment for grouping.
Hover: color shift only, no scale, no shadow.

### 1.2 Glassmorphism
```
--bg: vibrant gradient or image
--surface: rgba(255,255,255,0.1) to rgba(255,255,255,0.3)
--blur: backdrop-blur-[15px]
--border: 1px solid rgba(255,255,255,0.2)
--radius: 12-16px
--shadow: 0 8px 32px rgba(0,0,0,0.1)
--font-body: sans-serif, light weight
--transition: 300ms ease-out
```
Tailwind: `backdrop-blur-xl bg-white/10 border border-white/20 rounded-2xl`
Requires: vibrant background behind glass elements. Without it, glass is invisible.

### 1.3 Brutalist
```
--bg: #FFFFFF or #000000
--fg: inverse of bg
--accent: #FF0000, #0000FF, or #FFFF00 (primaries only)
--radius: 0px (strict)
--shadow: none
--border: 2-4px solid black
--font-body: system-ui or monospace
--font-display: same, 700-900 weight
--transition: none (instant state changes)
```
Tailwind: `border-2 border-black font-mono uppercase tracking-wide`
Buttons: `border-2 border-black shadow-[4px_4px_0px_0px_black] active:translate-x-[2px] active:translate-y-[2px] active:shadow-none`
Zero smooth transitions. Everything snaps.

### 1.4 Dark Cinematic
```
--bg-deep: #020203
--bg-base: #050506
--bg-elevated: #0a0a0c
--surface: rgba(255,255,255,0.05)
--fg: #EDEDEF
--fg-muted: #8A8F98
--accent: #5E6AD2 (or project-specific)
--accent-glow: rgba(94,106,210,0.2)
--border: rgba(255,255,255,0.08)
--radius: 16px
--shadow: multi-layer (ambient + diffuse + accent)
```
Tailwind: `bg-[#050506] text-[#EDEDEF] border border-white/[0.08] rounded-2xl`
NEVER use pure #000000 (causes OLED smearing). Minimum #050506.
Background: LinearGradient from #0a0a0f (top) to #020203 (bottom) + animated blur blobs.

### 1.5 Vibrant Block
```
--bg: alternating solid color blocks per section
--fg: white or black (max contrast against block)
--accent: neon/vivid (Green #39FF14, Purple #BF00FF, Pink #FF1493, Cyan #00FFFF)
--radius: 8-16px
--shadow: none (color does the work)
--border: none
--font-display: 32px+ bold
--section-gap: 48px+
--transition: 200-300ms
```
Tailwind: `bg-[#FF1493] text-white text-4xl font-bold`
Each section: different background color. Scroll-snap optional.

### 1.6 Neumorphism (Soft UI)
```
--bg: #E8E8E8 (light) or similar pastel
--surface: same as bg
--shadow-light: -5px -5px 15px rgba(255,255,255,0.8)
--shadow-dark: 5px 5px 15px rgba(0,0,0,0.1)
--radius: 12-16px
--border: none
--font-body: sans-serif, medium weight
--transition: 150ms ease-out
```
Tailwind: `bg-[#E8E8E8] rounded-2xl shadow-[-5px_-5px_15px_rgba(255,255,255,0.8),5px_5px_15px_rgba(0,0,0,0.1)]`
Press state: inset shadows (inner shadow swap).

### 1.7 Aurora / Gradient Flow
```
--bg: animated mesh gradient (2-3 color stops)
--surface: rgba(255,255,255,0.15) with backdrop-blur
--fg: #FFFFFF
--accent: complementary pair (blue-orange, purple-yellow)
--radius: 16-24px
--shadow: colored shadow matching gradient
--transition: 300ms ease-out
--gradient-animation: 8-12s infinite loop
```
Background CSS:
```css
background: conic-gradient(from 45deg, #5227FF, #7cff67, #5227FF);
background-size: 200% 200%;
animation: aurora-shift 10s ease infinite;
@keyframes aurora-shift {
  0%, 100% { background-position: 0% 50%; }
  50% { background-position: 100% 50%; }
}
```

### 1.8 Retro-Futurism / Synthwave
```
--bg: #1A1A2E or #000000
--fg: #FFFFFF
--accent: #FF006E (hot pink), #00FFFF (cyan), #0080FF (neon blue)
--radius: 0px
--border: 1px solid accent color
--shadow: 0 0 10px accent-color, 0 0 20px accent-color (glow)
--font-body: monospace
--font-display: sans-serif, 700+
```
Glow text: `text-shadow: 0 0 10px #FF006E, 0 0 20px #FF006E, 0 0 40px #FF006E;`
CRT scanlines overlay:
```css
.scanlines::after {
  content: '';
  position: absolute;
  inset: 0;
  background: repeating-linear-gradient(
    0deg,
    transparent,
    transparent 2px,
    rgba(0,0,0,0.1) 2px,
    rgba(0,0,0,0.1) 4px
  );
  pointer-events: none;
}
```

---

## 2. Typography Systems

### 2.1 Font Selection Rules

**BANNED fonts** (AI-tell, overused in generated pages):
Fraunces · Newsreader · Lora · Crimson · Crimson Pro · Crimson Text · Playfair Display · Cormorant · Cormorant Garamond · Syne · IBM Plex Mono · IBM Plex Sans · IBM Plex Serif · Space Mono · Space Grotesk · Inter · DM Sans · DM Serif Display · DM Serif Text · Outfit · Plus Jakarta Sans · Instrument Sans · Instrument Serif

**BANNED aesthetic lanes** (saturated AI patterns):
- Editorial-typographic: display serif italic + mono labels + ruled separators + monochromatic restraint
- Every-section-kicker: repeated tiny uppercase tracked labels above every heading

**Selection procedure:**
1. Write 3 concrete brand-voice words (physical-object words, not "modern" or "elegant")
2. List 3 reflex fonts → reject if in banned list
3. Browse real catalogs (Google Fonts, Pangram Pangram, Future Fonts, Velvetyne, Klim, ABC Dinamo)
4. Cross-check: if final pick = original reflex, restart

### 2.2 Type Scale (fluid clamp)

```css
--text-xs: clamp(0.75rem, 0.7rem + 0.25vw, 0.875rem);    /* 12-14px */
--text-sm: clamp(0.875rem, 0.8rem + 0.35vw, 1rem);        /* 14-16px */
--text-base: clamp(1rem, 0.95rem + 0.25vw, 1.125rem);     /* 16-18px */
--text-lg: clamp(1.125rem, 1rem + 0.5vw, 1.25rem);        /* 18-20px */
--text-xl: clamp(1.25rem, 1rem + 1vw, 1.5rem);            /* 20-24px */
--text-2xl: clamp(1.5rem, 1.2rem + 1.5vw, 2rem);          /* 24-32px */
--text-3xl: clamp(1.875rem, 1.5rem + 2vw, 2.5rem);        /* 30-40px */
--text-4xl: clamp(2.25rem, 1.5rem + 3vw, 3rem);           /* 36-48px */
--text-5xl: clamp(3rem, 2rem + 4vw, 4rem);                /* 48-64px */
--text-hero: clamp(3.5rem, 2rem + 6vw, 6rem);             /* 56-96px */
```

Ratio between steps: ≥1.25. Flat scales (1.1× apart) read as uncommitted.

### 2.3 Line Height Rules

| Context | line-height |
|---------|------------|
| Hero/display text | 0.9–1.1 |
| Headings | 1.1–1.25 |
| Body text | 1.5–1.7 |
| Light text on dark bg | add 0.05–0.1 to normal value |
| Tight headlines (brutalist) | leading-none (1.0) |

### 2.4 Font Pairing Patterns

| Pattern | Display | Body | Labels |
|---------|---------|------|--------|
| Dual serif+sans | Distinctive serif | Neutral sans | Mono (optional) |
| Single family | Heavy weight (700-900) | Regular weight (400) | Light weight (300) |
| Mono+sans | Mono for headings | Sans for body | Mono smaller |
| Slab+geometric | Slab serif display | Geometric sans | — |

Two families minimum ONLY when the voice needs it. A single well-chosen family with weight/size contrast is stronger than a timid pair.

---

## 3. Spacing System

### 3.1 Scale (4px base)

```css
--space-1: 0.25rem;   /* 4px */
--space-2: 0.5rem;    /* 8px */
--space-3: 0.75rem;   /* 12px */
--space-4: 1rem;      /* 16px */
--space-6: 1.5rem;    /* 24px */
--space-8: 2rem;      /* 32px */
--space-12: 3rem;     /* 48px */
--space-16: 4rem;     /* 64px */
--space-24: 6rem;     /* 96px */
--space-32: 8rem;     /* 128px */
```

Prefer 4pt base over 8pt — 8pt is too coarse (need 12px between 8 and 16).

### 3.2 Fluid Spacing (clamp)

```css
--section-gap: clamp(3rem, 2rem + 4vw, 6rem);
--container-pad: clamp(1rem, 0.5rem + 2vw, 2rem);
--content-gap: clamp(1.5rem, 1rem + 2vw, 3rem);
```

### 3.3 Rhythm Rules

- **Tight grouping**: 8-12px between related siblings
- **Generous separation**: 48-96px between distinct sections
- **Varied spacing**: NOT every row needs the same gap
- Use `gap` instead of margins (eliminates margin collapse)
- Container: `max-width: 1200px; margin: 0 auto; padding: 0 clamp(1rem, 5vw, 2rem);`

---

## 4. Shadow System

### 4.1 Elevation Scale

```css
/* Subtle (cards, inputs) */
--shadow-sm: 0 1px 2px rgba(0,0,0,0.05);

/* Medium (dropdowns, popovers) */
--shadow-md: 0 4px 6px -1px rgba(0,0,0,0.1), 0 2px 4px -2px rgba(0,0,0,0.1);

/* Large (modals, dialogs) */
--shadow-lg: 0 10px 15px -3px rgba(0,0,0,0.1), 0 4px 6px -4px rgba(0,0,0,0.1);

/* XL (floating elements) */
--shadow-xl: 0 20px 25px -5px rgba(0,0,0,0.1), 0 8px 10px -6px rgba(0,0,0,0.1);

/* Brutalist hard offset */
--shadow-brutal: 4px 4px 0px 0px #000000;
--shadow-brutal-sm: 2px 2px 0px 0px #000000;

/* Colored accent shadow */
--shadow-accent: 0 4px 14px rgba(var(--accent-rgb), 0.25);

/* Neon glow */
--shadow-glow: 0 0 10px var(--accent), 0 0 20px var(--accent);
```

### 4.2 Shadow Rules

- Shadows should be subtle and serve hierarchy, not decoration
- Dark mode: use rgba(0,0,0,0.3-0.5) or colored shadows, never white shadows
- Brutalist: hard offset only, no blur
- Glassmorphism: no shadow, use border + backdrop-blur instead

---

## 5. Border & Radius System

### 5.1 Radius Scale

```css
--radius-none: 0px;        /* Brutalist, editorial */
--radius-sm: 4px;          /* Subtle rounding */
--radius-md: 8px;          /* Standard components */
--radius-lg: 12px;         /* Cards, inputs */
--radius-xl: 16px;         /* Prominent cards */
--radius-2xl: 24px;        /* Hero sections, large cards */
--radius-full: 9999px;     /* Pills, avatars, FABs */
```

### 5.2 Border Patterns

```css
/* Hairline separator */
border-bottom: 1px solid rgba(0,0,0,0.1);

/* Structural divider */
border-bottom: 1px solid #000;

/* Heavy section divider */
border-bottom: 4px solid #000;

/* Glass border */
border: 1px solid rgba(255,255,255,0.2);

/* Input focus */
border-bottom: 2px solid var(--accent);

/* Brutalist thick */
border: 2px solid #000;
```

---

## 6. Animation & Motion

### 6.1 Timing Reference

| Duration | Use Case |
|----------|----------|
| 100-150ms | Instant feedback: button press, toggle, color change |
| 200-300ms | State changes: menu open, tooltip, hover |
| 300-500ms | Layout changes: accordion, modal, drawer |
| 500-800ms | Entrance animations: hero reveal, page load |

### 6.2 Easing Curves

```css
/* USE THESE — natural deceleration */
--ease-out-quart: cubic-bezier(0.25, 1, 0.5, 1);
--ease-out-quint: cubic-bezier(0.22, 1, 0.36, 1);
--ease-out-expo: cubic-bezier(0.16, 1, 0.3, 1);

/* AVOID — feel dated */
/* bounce, elastic, overshoot easings */
```

### 6.3 Entrance Animations (CSS-only, Astro-compatible)

**Fade + Rise (scroll-triggered via IntersectionObserver):**
```css
.reveal {
  opacity: 0;
  transform: translateY(40px);
  transition: opacity 0.6s var(--ease-out-quart), transform 0.6s var(--ease-out-quart);
}
.reveal.visible {
  opacity: 1;
  transform: translateY(0);
}
```

**Staggered children:**
```css
.stagger > * {
  opacity: 0;
  transform: translateY(20px);
  transition: opacity 0.5s var(--ease-out-quart), transform 0.5s var(--ease-out-quart);
}
.stagger.visible > *:nth-child(1) { transition-delay: 0ms; }
.stagger.visible > *:nth-child(2) { transition-delay: 50ms; }
.stagger.visible > *:nth-child(3) { transition-delay: 100ms; }
.stagger.visible > *:nth-child(4) { transition-delay: 150ms; }
/* Cap total stagger: 10 items × 50ms = 500ms max */
.stagger.visible > * { opacity: 1; transform: translateY(0); }
```

**Scale entrance:**
```css
.scale-in {
  opacity: 0;
  transform: scale(0.95);
  transition: opacity 0.5s var(--ease-out-quart), transform 0.5s var(--ease-out-quart);
}
.scale-in.visible {
  opacity: 1;
  transform: scale(1);
}
```

**IntersectionObserver script (Astro inline):**
```html
<script>
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.classList.add('visible');
        observer.unobserve(entry.target);
      }
    });
  }, { threshold: 0.1, rootMargin: '-50px' });

  document.querySelectorAll('.reveal, .stagger, .scale-in').forEach(el => {
    observer.observe(el);
  });
</script>
```

### 6.4 Text Animations (CSS-only adaptations)

**Blur text reveal:**
```css
.blur-reveal {
  opacity: 0;
  filter: blur(10px);
  transition: opacity 0.8s ease-out, filter 0.8s ease-out;
}
.blur-reveal.visible {
  opacity: 1;
  filter: blur(0px);
}
```

**Split text (per-character, requires JS):**
```html
<script>
  document.querySelectorAll('[data-split]').forEach(el => {
    const text = el.textContent;
    el.innerHTML = text.split('').map((char, i) =>
      `<span style="opacity:0;transform:translateY(40px);display:inline-block;transition:opacity 0.5s ${i * 0.03}s ease-out,transform 0.5s ${i * 0.03}s ease-out;">${char === ' ' ? '&nbsp;' : char}</span>`
    ).join('');
    const obs = new IntersectionObserver(([entry]) => {
      if (entry.isIntersecting) {
        el.querySelectorAll('span').forEach(s => {
          s.style.opacity = '1';
          s.style.transform = 'translateY(0)';
        });
        obs.unobserve(el);
      }
    }, { threshold: 0.1 });
    obs.observe(el);
  });
</script>
```

### 6.5 Background Effects (CSS-only)

**Animated gradient background:**
```css
.gradient-bg {
  background: linear-gradient(-45deg, #ee7752, #e73c7e, #23a6d5, #23d5ab);
  background-size: 400% 400%;
  animation: gradient-shift 15s ease infinite;
}
@keyframes gradient-shift {
  0% { background-position: 0% 50%; }
  50% { background-position: 100% 50%; }
  100% { background-position: 0% 50%; }
}
```

**Noise texture overlay:**
```css
.noise::after {
  content: '';
  position: absolute;
  inset: 0;
  opacity: 0.03;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)'/%3E%3C/svg%3E");
  pointer-events: none;
  z-index: 1;
}
```

**Dot grid pattern:**
```css
.dot-grid {
  background-image: radial-gradient(circle, rgba(0,0,0,0.1) 1px, transparent 1px);
  background-size: 16px 16px;
}
```

**Waves (pure CSS):**
```css
.wave-bg::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 80px;
  background: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 1440 120'%3E%3Cpath fill='%23ffffff' d='M0,64L48,58.7C96,53,192,43,288,48C384,53,480,75,576,80C672,85,768,75,864,64C960,53,1056,43,1152,42.7C1248,43,1344,53,1392,58.7L1440,64L1440,120L0,120Z'/%3E%3C/svg%3E") no-repeat bottom center;
  background-size: cover;
}
```

### 6.6 Micro-interactions

**Button hover:**
```css
/* Subtle lift */
.btn-hover { transition: transform 200ms var(--ease-out-quart), box-shadow 200ms var(--ease-out-quart); }
.btn-hover:hover { transform: translateY(-2px); box-shadow: var(--shadow-md); }

/* Scale */
.btn-scale { transition: transform 150ms var(--ease-out-quart); }
.btn-scale:hover { transform: scale(1.02); }
.btn-scale:active { transform: scale(0.98); }

/* Color shift */
.btn-shift { transition: background-color 200ms ease, color 200ms ease; }

/* Brutalist press */
.btn-brutal { transition: none; }
.btn-brutal:active { transform: translate(4px, 4px); box-shadow: none; }
```

**Card hover:**
```css
.card-lift {
  transition: transform 300ms var(--ease-out-quart), box-shadow 300ms var(--ease-out-quart);
}
.card-lift:hover {
  transform: translateY(-4px);
  box-shadow: var(--shadow-lg);
}
```

**Link underline animation:**
```css
.link-animate {
  position: relative;
  text-decoration: none;
}
.link-animate::after {
  content: '';
  position: absolute;
  bottom: -2px;
  left: 0;
  width: 0;
  height: 2px;
  background: currentColor;
  transition: width 300ms var(--ease-out-quart);
}
.link-animate:hover::after { width: 100%; }
```

### 6.7 Reduced Motion

```css
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
    scroll-behavior: auto !important;
  }
  .reveal, .stagger > *, .scale-in, .blur-reveal {
    opacity: 1 !important;
    transform: none !important;
    filter: none !important;
  }
}
```

---

## 7. Component Style Patterns

### 7.1 Button Variants

```css
/* Primary solid */
.btn-primary {
  padding: 0.75rem 1.5rem;
  font-weight: 600;
  border-radius: var(--radius-md);
  background: var(--accent);
  color: white;
  border: none;
  cursor: pointer;
  transition: opacity 200ms ease;
}
.btn-primary:hover { opacity: 0.9; }

/* Outline */
.btn-outline {
  padding: 0.75rem 1.5rem;
  font-weight: 600;
  border-radius: var(--radius-md);
  background: transparent;
  color: var(--accent);
  border: 2px solid var(--accent);
  cursor: pointer;
  transition: background 200ms ease, color 200ms ease;
}
.btn-outline:hover { background: var(--accent); color: white; }

/* Ghost */
.btn-ghost {
  padding: 0.75rem 1.5rem;
  font-weight: 500;
  background: transparent;
  color: var(--fg);
  border: none;
  cursor: pointer;
  transition: background 200ms ease;
}
.btn-ghost:hover { background: rgba(0,0,0,0.05); }

/* Pill */
.btn-pill { border-radius: 9999px; }
```

### 7.2 Input Styles

```css
/* Standard */
.input-standard {
  height: 48px;
  padding: 0 1rem;
  border: 1px solid var(--border);
  border-radius: var(--radius-md);
  font-size: 1rem;
  transition: border-color 200ms ease;
}
.input-standard:focus {
  outline: none;
  border-color: var(--accent);
  box-shadow: 0 0 0 3px rgba(var(--accent-rgb), 0.1);
}

/* Underline only */
.input-underline {
  height: 48px;
  padding: 0;
  border: none;
  border-bottom: 2px solid var(--border);
  border-radius: 0;
  background: transparent;
  font-size: 1rem;
  transition: border-color 200ms ease;
}
.input-underline:focus {
  outline: none;
  border-bottom-color: var(--accent);
}
```

### 7.3 Card Variants

```css
/* Elevated */
.card-elevated {
  background: var(--card-bg, white);
  border-radius: var(--radius-lg);
  padding: var(--space-6);
  box-shadow: var(--shadow-md);
}

/* Bordered */
.card-bordered {
  background: var(--card-bg, white);
  border-radius: var(--radius-lg);
  padding: var(--space-6);
  border: 1px solid var(--border);
}

/* Glass */
.card-glass {
  backdrop-filter: blur(15px);
  -webkit-backdrop-filter: blur(15px);
  background: rgba(255,255,255,0.1);
  border: 1px solid rgba(255,255,255,0.2);
  border-radius: var(--radius-xl);
  padding: var(--space-6);
}

/* Flat (no container, just spacing) */
/* Use gap + alignment instead of wrapping in a box */
```

---

## 8. Layout Utility Patterns

### 8.1 Container

```css
.container {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 clamp(1rem, 5vw, 2rem);
}

.container-narrow { max-width: 680px; }
.container-wide { max-width: 1440px; }
```

### 8.2 Section Spacing

```css
.section {
  padding: clamp(3rem, 2rem + 5vw, 6rem) 0;
}
.section-tight {
  padding: clamp(2rem, 1.5rem + 3vw, 4rem) 0;
}
.section-hero {
  min-height: 100vh;
  display: flex;
  align-items: center;
}
```

### 8.3 Auto-fit Grid

```css
.auto-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: var(--space-6);
}
```

### 8.4 Asymmetric Layouts

```css
/* 60/40 split */
.split-60-40 {
  display: grid;
  grid-template-columns: 3fr 2fr;
  gap: var(--space-8);
  align-items: center;
}

/* 40/60 split (reversed) */
.split-40-60 {
  display: grid;
  grid-template-columns: 2fr 3fr;
  gap: var(--space-8);
  align-items: center;
}

/* Bento grid */
.bento {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(200px, auto);
  gap: var(--space-4);
}
.bento > :first-child { grid-column: span 2; grid-row: span 2; }
```

---

## 9. Color Strategy Reference

### 9.1 Strategy Types

| Strategy | Description | When |
|----------|-------------|------|
| Monochromatic | Single hue + black/white | Editorial, luxury, minimal |
| Committed | One saturated accent on neutral base | SaaS, professional services |
| Full palette | 3-5 coordinated colors | Consumer brands, entertainment |
| Drenched | Single color dominates everything | Bold brand statements, hero sections |
| Complementary | Opposing hue pair | Energy, contrast, call-to-action |

### 9.2 Rules

- Name a real reference before picking. "Stripe purple restraint", "Liquid Death acid-green full palette".
- Palette IS voice. A calm brand ≠ a restless brand.
- When Committed or Drenched, don't hedge with neutrals. Commit.
- Don't converge across projects. Each landing differentiates from the last.
- When cultural-symbol palette is the obvious pull, reach past it.

---

## 10. Icon System

Library: **Phosphor Icons** (primary), Heroicons (fallback).
Import: `@phosphor-icons/react` or `phosphor-react`.

### 10.1 Size Standards

| Context | Size |
|---------|------|
| UI controls (nav, actions) | 20px |
| Feature anchors | 24-32px |
| Hero/decorative | 32-48px |

### 10.2 Style Rules

- Weight: `regular` (default). Never mix weights.
- Stroke: match to overall design weight (1.5px for refined, 2px for bold)
- Color: inherit from text color unless accent is intentional
- Touch targets: min 44×44px even if icon is smaller (expand with padding)
- Always pair icon with text label (standalone icons only for universal nav: back, close, menu)

---

## 11. Anti-Patterns (Hard Bans)

These produce "AI-generated" feeling. Never use:

1. **Monospace as lazy "technical" shorthand** when the brand isn't technical
2. **Large rounded-corner icons above every heading** — screams template
3. **All-caps body copy** — reserve caps for labels and headings only
4. **Zero imagery on image-led briefs** (restaurants, hotels, services) — colored blocks where photos belong = failure
5. **Identical card grids everywhere** — icon + heading + text, repeated endlessly
6. **Same structure for every section** — alternate layouts, break rhythm
7. **Fade-on-scroll for every section** — reserve scroll-triggered motion for moments that earn it
8. **Repeated tiny uppercase tracked labels above every section heading**
9. **Editorial-magazine aesthetics on non-editorial briefs** — display serif + italic + drop caps is ONE lane, not the default
10. **Timid palettes and average layouts** — safe = invisible
11. **Generic stock photo descriptions** — "Italian food" vs "handmade pasta on scratched wooden table"
12. **Bounce/elastic easing** — feels dated and tacky
13. **Pure black (#000000) on dark themes** — use #050506 minimum
14. **Cards inside cards** — use spacing and dividers for hierarchy within
15. **Hero metric layout as default** — big number + small label + stats + gradient = template fingerprint

---

## 12. Profile-to-Niche Mapping

Quick reference for which style profile fits which local business type. The agent should use this as a STARTING POINT, then differentiate within the profile.

| Business Type | Primary Profile | Alt Profile | Notes |
|---|---|---|---|
| Landscaping | Clean Minimal | Vibrant Block | Nature imagery essential |
| Plumbing / HVAC | Clean Minimal | — | Trust signals, no-nonsense |
| Restaurant / Café | Aurora, Glassmorphism | Dark Cinematic | Imagery MUST be present |
| Legal / Accounting | Clean Minimal | — | Conservative but not boring |
| Fitness / Gym | Vibrant Block | Dark Cinematic | Energy, bold type |
| Salon / Spa | Glassmorphism | Neumorphism | Soft, warm, inviting |
| Auto Repair | Brutalist | Dark Cinematic | Raw, honest, direct |
| Real Estate | Clean Minimal | Glassmorphism | Property imagery critical |
| Cleaning Service | Clean Minimal | Vibrant Block | Fresh, bright |
| Photography | Dark Cinematic | Brutalist | Work IS the design |
| Tech / IT Services | Dark Cinematic | Retro-Futurism | Differentiate from SaaS |
| Dental / Medical | Clean Minimal | Neumorphism | Trust, cleanliness |
| Construction | Brutalist | Clean Minimal | Materials, strength |
| Pet Services | Vibrant Block | Neumorphism | Playful, warm |

This table is a suggestion. The agent MUST verify against the specific business's brand voice and competitor landscape before committing.
