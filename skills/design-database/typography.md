# Typography System — design-database

> Reference tipográfica completa para landing pages de negocios locales US.
> Cada combinación es una pareja heading + body testeada en producción.
> No inventar parejas. Usar solo las definidas aquí.

---

## 1. Roles tipográficos

Toda landing usa exactamente **3 roles**:

| Rol | Uso | Peso típico | Ejemplo de tag |
|-----|-----|-------------|----------------|
| `heading` | H1, H2, hero titles, section titles | 700–900 | `<h1>`, `<h2>` |
| `body` | Párrafos, descripciones, bullets, cards | 400–500 | `<p>`, `<li>` |
| `accent` | CTAs, badges, labels, nav links, small caps | 500–700 | `<button>`, `<span>` |

**Regla:** `accent` hereda la familia de `heading` salvo que la pareja lo especifique.

---

## 2. Scale tipográfica

### 2.1 Desktop scale (min-width: 1024px)

| Token | Size | Line-height | Letter-spacing | Uso |
|-------|------|-------------|----------------|-----|
| `text-hero` | 3.5rem–4.5rem (56–72px) | 1.05–1.1 | -0.02em | H1 hero only |
| `text-h2` | 2rem–2.5rem (32–40px) | 1.15–1.2 | -0.015em | Section titles |
| `text-h3` | 1.5rem–1.75rem (24–28px) | 1.2–1.25 | -0.01em | Subsection, card titles |
| `text-h4` | 1.125rem–1.25rem (18–20px) | 1.3 | 0 | Small headings |
| `text-body` | 1rem–1.125rem (16–18px) | 1.6–1.7 | 0 | Paragraphs |
| `text-small` | 0.875rem (14px) | 1.5 | 0.01em | Captions, labels |
| `text-micro` | 0.75rem (12px) | 1.4 | 0.02em | Legal, disclaimers |

### 2.2 Mobile scale (max-width: 767px)

| Token | Size | Line-height | Nota |
|-------|------|-------------|------|
| `text-hero` | 2.25rem–2.75rem (36–44px) | 1.1 | Reducir ~35% de desktop |
| `text-h2` | 1.5rem–1.75rem (24–28px) | 1.2 | — |
| `text-h3` | 1.25rem–1.375rem (20–22px) | 1.25 | — |
| `text-body` | 1rem (16px) | 1.6 | Nunca menor a 16px |
| `text-small` | 0.875rem (14px) | 1.5 | — |

### 2.3 Tablet scale (768px–1023px)

Interpolar entre mobile y desktop. No crear breakpoint separado salvo que el diseño lo requiera.

---

## 3. Parejas tipográficas por Visual Profile

### 3.1 BOLD INDUSTRIAL

Personalidad: fuerte, directo, sin vueltas. Headings pesados, body neutro.

| Pareja ID | Heading | Body | Accent | Feeling |
|-----------|---------|------|--------|---------|
| `BI-01` | **Oswald** (700, 800) | Inter (400, 500) | Oswald (600) | Clásico industrial, máximo contraste |
| `BI-02` | **Bebas Neue** (400) | Source Sans 3 (400, 600) | Source Sans 3 (700) | Condensado agresivo, limpio |
| `BI-03` | **Barlow Condensed** (700, 800) | Barlow (400, 500) | Barlow Condensed (600) | Familia unificada, compacto |
| `BI-04` | **Teko** (600, 700) | Work Sans (400, 500) | Teko (500) | Técnico, maquinaria pesada |
| `BI-05` | **Anton** (400) | Roboto (400, 500) | Roboto (700) | Ultra bold display, neutro body |
| `BI-06` | **Archivo Black** (400) | Archivo (400, 500) | Archivo (600) | Mismo sistema, peso extremo en heading |

**Reglas Bold Industrial:**
- Hero heading: siempre uppercase o small-caps
- letter-spacing en headings: -0.02em a -0.03em
- Body max-width: 65ch
- Nunca usar italic en headings
- CTA buttons: uppercase, letter-spacing 0.05em–0.1em

### 3.2 CLEAN CORPORATE

Personalidad: profesional, confiable, pulido. Geometría clara.

| Pareja ID | Heading | Body | Accent | Feeling |
|-----------|---------|------|--------|---------|
| `CC-01` | **Montserrat** (600, 700) | Open Sans (400, 500) | Montserrat (600) | Estándar corporativo, siempre funciona |
| `CC-02` | **Poppins** (600, 700) | Inter (400, 500) | Poppins (500) | Moderno-friendly, geometría suave |
| `CC-03` | **Raleway** (600, 700) | Lato (400) | Raleway (500) | Elegante-corporativo, ligero |
| `CC-04` | **DM Sans** (500, 700) | DM Sans (400) | DM Sans (600) | Minimalista single-family |
| `CC-05` | **Plus Jakarta Sans** (600, 700) | Plus Jakarta Sans (400, 500) | Plus Jakarta Sans (600) | Tech-forward, SaaS feel |
| `CC-06` | **Outfit** (600, 700) | Source Sans 3 (400) | Outfit (500) | Limpio geométrico, accesible |

**Reglas Clean Corporate:**
- Hero heading: sentence case o title case, nunca full uppercase
- letter-spacing: 0 a -0.01em
- Body line-height: 1.65–1.75 (más aire)
- Peso máximo heading: 700 (no usar 800–900)
- CTA buttons: sentence case, border-radius ≥ 6px

### 3.3 WARM ORGANIC

Personalidad: humano, cercano, artesanal. Serif o humanist sans en headings.

| Pareja ID | Heading | Body | Accent | Feeling |
|-----------|---------|------|--------|---------|
| `WO-01` | **Playfair Display** (700, 800) | Source Sans 3 (400) | Source Sans 3 (600) | Clásico editorial, confianza |
| `WO-02` | **Lora** (600, 700) | Nunito (400, 500) | Nunito (600) | Cálido literario, accesible |
| `WO-03` | **Merriweather** (700, 900) | Merriweather Sans (400) | Merriweather Sans (700) | Robusto serif, periodístico |
| `WO-04` | **Cormorant Garamond** (600, 700) | Proza Libre (400, 500) | Proza Libre (600) | Refinado, boutique |
| `WO-05` | **Bitter** (600, 700) | Karla (400, 500) | Karla (600) | Slab approachable, friendly |
| `WO-06` | **Libre Baskerville** (700) | Libre Franklin (400, 500) | Libre Franklin (600) | Editorial clásico US |

**Reglas Warm Organic:**
- Hero heading: title case o sentence case
- Permitido italic en H1 si la pareja lo soporta
- letter-spacing headings: 0 a 0.01em (no negativo)
- Body line-height: 1.7–1.8 (máximo aire)
- CTA buttons: sentence case, pueden tener border-radius ≥ 8px o full-round

### 3.4 MODERN STARTER

Personalidad: fresco, joven, accesible. Sans-serif geométrica.

| Pareja ID | Heading | Body | Accent | Feeling |
|-----------|---------|------|--------|---------|
| `MS-01` | **Space Grotesk** (500, 700) | Inter (400) | Space Grotesk (600) | Tech-minimal, startupero |
| `MS-02` | **Sora** (600, 700) | Sora (400) | Sora (500) | Single family, ultra clean |
| `MS-03` | **Urbanist** (600, 700) | Urbanist (400) | Urbanist (500) | Geométrico suave, app-like |
| `MS-04` | **Albert Sans** (600, 700) | Albert Sans (400) | Albert Sans (600) | Neutral moderno |
| `MS-05` | **General Sans** (600, 700) | General Sans (400, 500) | General Sans (600) | Variable, trend 2024 |
| `MS-06` | **Figtree** (600, 700) | Figtree (400, 500) | Figtree (600) | Friendly geometric, Google native |

**Reglas Modern Starter:**
- Hero heading: sentence case
- letter-spacing: 0 a -0.01em
- Peso heading: 600–700 (no ultra bold)
- Body text-body: 1rem (16px), no más
- CTA buttons: sentence case, pill shape (border-radius: 9999px) o medium radius (8px)

### 3.5 DARK CINEMATIC

Personalidad: premium, dramático, visual-first. Contraste extremo.

| Pareja ID | Heading | Body | Accent | Feeling |
|-----------|---------|------|--------|---------|
| `DC-01` | **Clash Display** (600, 700) | Inter (400) | Clash Display (500) | Luxury-editorial, moda |
| `DC-02` | **Cabinet Grotesk** (700, 800) | Satoshi (400, 500) | Cabinet Grotesk (600) | Premium brand, alto impacto |
| `DC-03` | **Syne** (700, 800) | Work Sans (400) | Syne (600) | Artístico bold, galería |
| `DC-04` | **Unbounded** (600, 700) | DM Sans (400) | Unbounded (500) | Futurista, rounded display |
| `DC-05` | **Familjen Grotesk** (600, 700) | Inter (400) | Familjen Grotesk (500) | Sofisticado minimalista |

**Reglas Dark Cinematic:**
- Hero heading: uppercase O sentence case (decidir por nicho)
- letter-spacing uppercase: 0.05em–0.15em
- letter-spacing sentence: -0.02em
- Body color: nunca #FFFFFF puro → usar rgba(255,255,255,0.85) o gris claro
- Hero text-hero puede escalar a 5rem+ en desktop
- CTA: uppercase con letter-spacing o minimal con borde sutil

---

## 4. Mapping nicho → pareja recomendada

| Nicho | Profile | Parejas primarias | Fallback |
|-------|---------|-------------------|----------|
| Landscaping | Bold Industrial | BI-01, BI-03 | BI-06 |
| Lawn Care | Bold Industrial | BI-03, BI-06 | BI-01 |
| Tree Service | Bold Industrial | BI-04, BI-01 | BI-02 |
| Plumbing | Bold Industrial | BI-01, BI-05 | BI-03 |
| HVAC | Clean Corporate | CC-01, CC-06 | CC-02 |
| Electrical | Clean Corporate | CC-02, CC-05 | CC-01 |
| Roofing | Bold Industrial | BI-02, BI-04 | BI-01 |
| Pest Control | Clean Corporate | CC-01, CC-03 | CC-06 |
| Cleaning Service | Clean Corporate | CC-02, CC-04 | CC-06 |
| Restaurant | Warm Organic | WO-01, WO-04 | WO-06 |
| Bakery/Café | Warm Organic | WO-02, WO-05 | WO-04 |
| Salon/Barbershop | Modern Starter | MS-01, MS-03 | MS-06 |
| Spa/Wellness | Warm Organic | WO-04, WO-01 | WO-03 |
| Dental | Clean Corporate | CC-01, CC-02 | CC-05 |
| Chiropractic | Clean Corporate | CC-03, CC-06 | CC-02 |
| Veterinary | Warm Organic | WO-02, WO-05 | WO-06 |
| Law Firm | Clean Corporate | CC-01, CC-03 | CC-06 |
| Accounting | Clean Corporate | CC-04, CC-01 | CC-05 |
| Real Estate | Modern Starter | MS-01, MS-02 | MS-05 |
| Photography | Dark Cinematic | DC-01, DC-03 | DC-05 |
| Tattoo Studio | Dark Cinematic | DC-02, DC-03 | DC-04 |
| Nightclub/Bar | Dark Cinematic | DC-01, DC-04 | DC-02 |
| Gym/Fitness | Bold Industrial | BI-02, BI-05 | BI-01 |
| Yoga/Pilates | Warm Organic | WO-02, WO-04 | WO-06 |
| Auto Repair | Bold Industrial | BI-04, BI-01 | BI-06 |
| Towing | Bold Industrial | BI-05, BI-02 | BI-03 |
| Moving Company | Bold Industrial | BI-03, BI-06 | BI-01 |
| Insurance | Clean Corporate | CC-01, CC-06 | CC-03 |
| Florist | Warm Organic | WO-04, WO-02 | WO-01 |
| Pet Grooming | Modern Starter | MS-03, MS-06 | MS-02 |
| Tutoring | Modern Starter | MS-02, MS-04 | MS-06 |
| Daycare | Modern Starter | MS-06, MS-03 | MS-02 |

**Regla de selección:**
1. Buscar nicho exacto → usar pareja primaria (rotar entre las 2 listadas)
2. Si no hay match → buscar categoría padre (ej: "fence company" → construction → Bold Industrial)
3. Si el negocio tiene branding existente con fuentes propias → override con las del brand

---

## 5. Reglas de implementación

### 5.1 Google Fonts loading

```html
<!-- Siempre preconnect -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>

<!-- Cargar solo los pesos necesarios -->
<!-- Ejemplo para BI-01: Oswald 700,800 + Inter 400,500 -->
<link href="https://fonts.googleapis.com/css2?family=Oswald:wght@700;800&family=Inter:wght@400;500&display=swap" rel="stylesheet">
```

**Reglas de carga:**
- Máximo 2 familias por landing (heading + body)
- Máximo 4 pesos totales (2 heading + 2 body)
- Siempre `display=swap`
- Preconnect obligatorio

### 5.2 Fonts no disponibles en Google Fonts

Las siguientes fuentes requieren descarga/self-host:
- Clash Display → [Fontshare](https://www.fontshare.com/fonts/clash-display)
- Cabinet Grotesk → [Fontshare](https://www.fontshare.com/fonts/cabinet-grotesk)
- Satoshi → [Fontshare](https://www.fontshare.com/fonts/satoshi)
- General Sans → [Fontshare](https://www.fontshare.com/fonts/general-sans)

**Si se usa fuente Fontshare:**
```css
@font-face {
  font-family: 'Clash Display';
  src: url('/fonts/ClashDisplay-Variable.woff2') format('woff2');
  font-weight: 200 700;
  font-display: swap;
}
```

**Fallback obligatorio:** Si self-host no es viable, sustituir:
- Clash Display → Space Grotesk (Google)
- Cabinet Grotesk → DM Sans (Google)
- Satoshi → Inter (Google)
- General Sans → Albert Sans (Google)

### 5.3 CSS custom properties

```css
:root {
  /* Typography tokens */
  --font-heading: 'Oswald', sans-serif;
  --font-body: 'Inter', sans-serif;
  --font-accent: var(--font-heading);

  /* Scale tokens */
  --text-hero: clamp(2.25rem, 5vw + 1rem, 4.5rem);
  --text-h2: clamp(1.5rem, 3vw + 0.5rem, 2.5rem);
  --text-h3: clamp(1.25rem, 2vw + 0.5rem, 1.75rem);
  --text-body: clamp(1rem, 1vw + 0.5rem, 1.125rem);
  --text-small: 0.875rem;

  /* Line heights */
  --lh-heading: 1.1;
  --lh-body: 1.65;

  /* Letter spacing */
  --ls-heading: -0.02em;
  --ls-body: 0;
}
```

### 5.4 Tailwind config mapping

```js
// tailwind.config.mjs
export default {
  theme: {
    extend: {
      fontFamily: {
        heading: ['var(--font-heading)'],
        body: ['var(--font-body)'],
        accent: ['var(--font-accent)'],
      },
      fontSize: {
        hero: ['var(--text-hero)', { lineHeight: 'var(--lh-heading)' }],
        h2: ['var(--text-h2)', { lineHeight: 'var(--lh-heading)' }],
        h3: ['var(--text-h3)', { lineHeight: '1.25' }],
        body: ['var(--text-body)', { lineHeight: 'var(--lh-body)' }],
        small: ['var(--text-small)', { lineHeight: '1.5' }],
      },
    },
  },
};
```

---

## 6. Reglas anti-monotonía

Para evitar que dos landings del mismo nicho se vean iguales tipográficamente:

1. **Rotación obligatoria:** Si la landing anterior usó pareja primaria #1, la siguiente usa primaria #2 o fallback
2. **Variación de case:** Alternar entre uppercase hero y sentence case hero dentro del mismo profile
3. **Variación de peso:** Si la anterior usó 700, la siguiente puede usar 800 (si la pareja lo soporta)
4. **Scale shift:** Permitido ajustar text-hero ±0.25rem entre landings del mismo nicho
5. **Nunca repetir la misma pareja en landings consecutivas del mismo nicho**

---

## 7. Reglas de accesibilidad tipográfica

| Regla | Requisito | Verificación |
|-------|-----------|--------------|
| Tamaño mínimo body | 16px (1rem) | mobile y desktop |
| Contraste texto/fondo | WCAG AA mínimo (4.5:1 body, 3:1 large text) | Calcular con paleta asignada |
| Line-height mínimo body | 1.5 | WCAG 1.4.12 |
| Letter-spacing body | ≥ 0 | No negativo en body text |
| Word-spacing | ≥ 0 | No negativo |
| Max line length | 45–75ch | Usar max-width en párrafos |
| Font-size zoom | No break a 200% zoom | Test responsive |
| Heading hierarchy | H1 > H2 > H3, sin saltos | Semántico |

---

## 8. Validación

Antes de aplicar tipografía, verificar:

- [ ] ¿La pareja seleccionada corresponde al Visual Profile asignado?
- [ ] ¿Se cargaron solo 2 familias y ≤ 4 pesos?
- [ ] ¿Se usó `display=swap` y preconnect?
- [ ] ¿El hero cumple la escala definida (desktop y mobile)?
- [ ] ¿Body ≥ 16px en mobile?
- [ ] ¿Contraste AA verificado contra paleta?
- [ ] ¿No se repite pareja de landing anterior del mismo nicho?
- [ ] ¿Las reglas de case/spacing del profile se respetan?

---

## Completion

`typography.md` es referencia exclusiva del skill `design-database`.
Define parejas tipográficas, escalas y reglas.
No contiene lógica de arquitectura, layout ni contenido SEO.
Cualquier decisión tipográfica debe validarse contra este archivo.
