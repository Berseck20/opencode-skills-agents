# UX Guidelines — design-database

> Reglas de experiencia de usuario para landing pages de negocios locales US.
> Toda decisión UX debe validarse contra este archivo.
> No inventar patrones. Usar solo los definidos aquí.

---

## 1. Principios fundamentales

Toda landing page de negocio local existe para **una sola cosa**: convertir visitantes en leads (llamada, formulario, dirección).

| Principio | Significado práctico |
|-----------|---------------------|
| **Claridad instantánea** | El usuario entiende qué hace el negocio y dónde opera en < 3 segundos |
| **Fricción mínima** | Cada scroll debe acercar al usuario a la acción, nunca alejarlo |
| **Confianza antes de venta** | Social proof y credenciales antes de pedir datos |
| **Mobile-first real** | 70%+ del tráfico local es mobile. Diseñar para pulgar, no para mouse |
| **Velocidad = UX** | Si tarda > 3s en cargar, el usuario se fue. Performance es diseño |

---

## 2. Jerarquía de información

### 2.1 Orden de prioridad del contenido

El usuario de un negocio local necesita responder estas preguntas en este orden:

| Prioridad | Pregunta del usuario | Sección que responde |
|-----------|---------------------|---------------------|
| 1 | "¿Qué hacen?" | Hero headline + subheadline |
| 2 | "¿Sirven mi zona?" | Hero badge / service area |
| 3 | "¿Son confiables?" | Social proof (reviews, badges, years) |
| 4 | "¿Qué servicios específicos?" | Services grid/list |
| 5 | "¿Cómo es su trabajo?" | Gallery / before-after / process |
| 6 | "¿Por qué ellos y no otro?" | Differentiators / USPs |
| 7 | "¿Cuánto cuesta?" (si aplica) | Pricing / free estimate CTA |
| 8 | "¿Cómo los contacto?" | Contact section / footer |

**Regla:** Nunca poner la sección de servicios antes del social proof si el negocio tiene ≥ 10 reviews.

### 2.2 Densidad de información por viewport

| Zona | Desktop | Mobile | Regla |
|------|---------|--------|-------|
| Above the fold | Headline + CTA + 1 trust signal | Headline + CTA | Máximo 3 elementos de decisión |
| Primer scroll | Social proof + service overview | Social proof | No abrumar, 1 idea por pantalla |
| Mid-page | Servicios + gallery/process | Servicios colapsados | Permitir escaneo rápido |
| Lower page | Differentiators + testimonials | Testimonials | Refuerzo de confianza |
| Final | Contact + map + footer | Contact + CTA sticky | Cerrar con acción |

---

## 3. Patrones de interacción

### 3.1 CTAs — Reglas de uso

| Tipo de CTA | Formato | Cuándo usar | Cuándo NO usar |
|-------------|---------|-------------|----------------|
| **Primary** | Botón sólido, color primario | Hero, final de sección de servicios, contact | No más de 3 en toda la landing |
| **Secondary** | Botón outline o ghost | Junto a primary como alternativa | Solo si hay 2 acciones válidas |
| **Inline** | Link con arrow o underline | Dentro de párrafos, cards | No usar como acción principal |
| **Sticky mobile** | Barra fija bottom | Mobile, siempre visible después de hero | No en desktop |
| **Float** | Botón flotante (phone/WhatsApp) | Negocios con atención telefónica directa | No combinar con sticky bar |

**Reglas de CTA:**

1. **Máximo 3 CTAs primarios** en toda la landing (hero + mid + contact)
2. **Nunca 2 CTAs primarios visibles simultáneamente** en el mismo viewport
3. **Texto del CTA:** acción concreta, no genérico
   - ✅ "Get Free Estimate" / "Call Now — (555) 123-4567" / "Schedule Service"
   - ❌ "Click Here" / "Submit" / "Learn More" (como primario)
4. **CTA debe incluir contexto:** si es teléfono, mostrar el número. Si es form, indicar qué recibirá.
5. **Variación obligatoria:** Los 3 CTAs primarios deben tener texto diferente entre sí
6. **Mobile sticky:** Aparece después de pasar el hero (scroll > 100vh). Desaparece al llegar a la sección de contacto final.

### 3.2 Formularios

| Regla | Especificación |
|-------|---------------|
| Campos máximos | 4 (name, phone, email, message) |
| Campos visibles sin scroll | 3 |
| Campos requeridos | Solo name + phone O name + email |
| Label position | Above field (no floating labels en mobile) |
| Botón submit | Full width en mobile, ≥ 200px en desktop |
| Feedback de envío | Inline success message, no redirect ni modal |
| Autofill | Habilitar autocomplete en todos los campos |
| Input size mobile | min-height: 48px (touch target) |

**Nunca pedir:**
- Dirección completa (salvo mudanzas o servicios a domicilio obligatorio)
- Fecha de nacimiento
- Más de 1 dropdown/select
- CAPTCHA visible (usar honeypot o reCAPTCHA v3)

### 3.3 Navegación

| Tipo de landing | Nav recomendada |
|-----------------|-----------------|
| Single-page landing (< 6 secciones) | Sin nav bar. Scroll natural. Opcional: anchor dots laterales. |
| Landing extendida (6+ secciones) | Nav fija minimal: logo + 3-4 anchors + CTA button |
| Multi-location | Nav con selector de ubicación |

**Reglas de nav:**
- Mobile: hamburger SOLO si hay 4+ items. Si hay 3, mostrar inline.
- Logo siempre clickeable → scroll to top
- Nav CTA (si existe) es el único botón en la nav → color primario
- Nav se oculta al scroll-down, aparece al scroll-up (hide-on-scroll pattern)
- Transparente sobre hero, sólida después del hero

### 3.4 Scroll behavior

| Patrón | Uso | Implementación |
|--------|-----|----------------|
| **Smooth scroll** | Anchor links | `scroll-behavior: smooth` + offset para nav fija |
| **Reveal on scroll** | Secciones, cards | `IntersectionObserver` con `opacity 0→1` + `translateY(20px→0)` |
| **Parallax sutil** | Hero background only | `transform: translateZ` o `background-attachment: fixed`. Solo desktop. |
| **Stagger** | Grids de servicios, cards | Delay 50-100ms entre items. Máximo 4 items stagger. |
| **Sticky sections** | Comparativas, features | Solo desktop. Mobile → stack normal. |

**Reglas de animación:**
- Duración: 300-500ms (nunca > 800ms)
- Easing: `ease-out` o `cubic-bezier(0.25, 0.46, 0.45, 0.94)`
- `prefers-reduced-motion: reduce` → desactivar TODAS las animaciones
- Nunca animar layout properties (width, height, top, left) → solo `transform` y `opacity`
- No bounce effects
- No animaciones en texto body

---

## 4. Patrones de confianza (Trust Patterns)

### 4.1 Jerarquía de trust signals

Ordenados por impacto en conversión para negocios locales:

| Nivel | Signal | Ubicación recomendada | Formato |
|-------|--------|----------------------|---------|
| 1 (máximo) | Google reviews con rating | Hero o justo debajo | Stars + "4.8 ★ (127 reviews)" |
| 2 | Testimonios con nombre + foto | Mid-page, sección dedicada | Quote + nombre + ciudad |
| 3 | Years in business | Hero badge o about section | "Serving [city] since 2005" |
| 4 | Licencias / seguros | Service area o footer | Badge icons |
| 5 | Before/After photos | Gallery section | Slider o side-by-side |
| 6 | Logos de asociaciones | Footer o trust bar | Grayscale, small |
| 7 | "Featured in" / press | Trust bar | Logo strip |

**Reglas:**
- Mostrar **mínimo 2 trust signals** above the fold o en el primer scroll
- **Nunca fabricar** reviews ni números. Si no hay data → omitir, no inventar.
- **Reviews reales:** Siempre con fuente ("Google", "Yelp"). Nunca testimonios sin atribución.
- **Before/After:** Solo si el negocio tiene material real. No usar stock photos como B/A.

### 4.2 Social proof patterns

| Patrón | Componente visual | Cuándo usar |
|--------|-------------------|-------------|
| **Review carousel** | Cards con quote + stars + name | ≥ 3 reviews disponibles |
| **Review highlight** | 1 review grande + rating summary | 1-2 reviews fuertes |
| **Stats bar** | 3-4 números en row (years, projects, rating, clients) | Negocio establecido (5+ years) |
| **Logo strip** | Logos grayscale en row | Negocio B2B o con partnerships |
| **Trust badges** | Icons + texto corto en row/grid | Licencias, seguros, certificaciones |
| **Video testimonial** | Thumbnail + play button | Solo si hay video real |

---

## 5. UX por dispositivo

### 5.1 Mobile (< 768px)

| Elemento | Regla |
|----------|-------|
| Touch targets | Mínimo 44x44px (WCAG) / idealmente 48x48px |
| Tap spacing | Mínimo 8px entre targets |
| Phone numbers | Siempre `tel:` link, tap-to-call |
| Maps | Embed estático con link a Google Maps, no iframe interactivo |
| Images | `loading="lazy"` excepto hero. Aspect-ratio fijo para evitar CLS. |
| Horizontal scroll | PROHIBIDO excepto en carousels explícitos |
| Text input | `font-size: 16px` mínimo para evitar zoom en iOS |
| Modals | Evitar. Si es necesario, full-screen con close visible. |
| Tables | Reflow a cards o scroll horizontal con indicador visual |
| Sticky CTA | `position: fixed; bottom: 0` con `z-index` alto + safe-area-inset |

### 5.2 Desktop (≥ 1024px)

| Elemento | Regla |
|----------|-------|
| Max-width contenido | 1200px–1400px centrado |
| Hero height | 80vh–100vh, nunca > 100vh |
| Grid columns | Máximo 4 para servicios. 3 para testimonials. 2 para features. |
| Hover states | Obligatorios en todos los elementos interactivos |
| White space | Más generoso que mobile. Sections padding: 80px–120px vertical |
| Sidebar | No usar en landing pages. Full-width sections only. |

### 5.3 Tablet (768px–1023px)

| Elemento | Regla |
|----------|-------|
| Grid | 2 columns donde desktop usa 3-4. 1 column donde desktop usa 2. |
| Nav | Puede ser inline (3 items) o hamburger (4+) |
| Hero | Similar a desktop pero text-hero reducido |
| Touch targets | Mismas reglas que mobile |

---

## 6. Patrones de contenido visual

### 6.1 Imágenes

| Tipo | Uso | Reglas |
|------|-----|--------|
| Hero image/video | Background o split con texto | Alta resolución. Representar el servicio o resultado. Nunca genérica. |
| Service images | Cards o secciones de servicio | Mostrar el trabajo real o equipo real. Stock solo como último recurso. |
| Team photos | About section | Reales. Si no hay, omitir sección. No usar stock people. |
| Before/After | Gallery | Mismo ángulo, misma iluminación. Label claro "Before" / "After". |
| Icons | Services grid, features, process | Consistentes en estilo. Un solo set (outline O filled, no mezclar). |
| Background patterns | Secciones alternas | Sutiles. Opacity < 10%. No distraer del contenido. |

**Regla de stock photos:**
- Si se usa stock: nunca personas mirando a cámara con sonrisa forzada
- Preferir: herramientas, texturas, materiales, resultados de trabajo, ambientes
- Nunca más de 2 stock photos visibles simultáneamente
- Siempre optimizar: WebP, srcset, sizes

### 6.2 Iconografía

| Regla | Especificación |
|-------|---------------|
| Estilo consistente | Todo el set debe ser del mismo estilo (line, filled, duotone) |
| Tamaño en servicios | 32-48px con contenedor de 64-80px |
| Color | Usar color primario o neutro. Nunca multicolor por icon. |
| Cantidad por row | 3-4 en desktop, 2 en mobile (grid) o 1 (list) |
| Fuente recomendada | Heroicons, Lucide, Phosphor, Tabler. No mezclar sets. |
| Decorativo vs funcional | Los decorativos llevan `aria-hidden="true"`. Los funcionales llevan `aria-label`. |

---

## 7. Patrones anti-UX (evitar siempre)

| Anti-patrón | Por qué es malo | Qué hacer en su lugar |
|-------------|-----------------|----------------------|
| **Popup/modal al entrar** | Interrumpe, aumenta bounce | Inline CTA o sticky bar después de scroll |
| **Auto-play video con sonido** | Molesto, accesibilidad | Thumbnail + play button. Muted autoplay máximo. |
| **Carousel auto-rotate** | Usuarios no leen a tiempo | Carousel manual o grid estático |
| **Parallax agresivo** | Motion sickness, performance | Parallax sutil solo en hero background |
| **Text over busy image sin overlay** | Ilegible | Overlay gradient o solid con opacity |
| **Infinite scroll** | No tiene sentido en landing | Secciones finitas con footer claro |
| **Hamburger menu en desktop** | Oculta navegación sin razón | Nav inline con items visibles |
| **Accordion para todo** | Oculta contenido que debe verse | Acordeón solo para FAQ (6+ items) |
| **Multiple fonts (3+)** | Caos visual, performance | Máximo 2 familias (heading + body) |
| **Click here links** | No descriptivo, accesibilidad | Link text = destino ("View our services") |
| **Full-page loading screen** | Sensación de lentitud | Progressive loading, skeleton screens |
| **Slider como hero** | Baja conversión, lento | Hero estático con 1 mensaje fuerte |
| **Social media feed embed** | Lento, distrae, saca al usuario del sitio | Screenshots curados o testimonials directos |
| **Background music** | No. | No. |
| **Countdown timers falsos** | Destruye confianza | Si hay promo real, usar fecha real |

---

## 8. Secciones: guías de implementación UX

### 8.1 Hero section

| Aspecto | Guideline |
|---------|-----------|
| Tiempo de comprensión | < 3 segundos para entender qué + dónde |
| Elementos obligatorios | H1 + subheadline + 1 CTA primario |
| Elementos opcionales | Trust badge, phone number, hero image |
| Background | Imagen real del negocio/trabajo con overlay O color sólido/gradient |
| CTA en hero | 1 primario. Máximo 1 secundario al lado. |
| Mobile hero | CTA debe estar visible sin scroll (above fold) |

### 8.2 Services section

| Aspecto | Guideline |
|---------|-----------|
| Cantidad de servicios | Mostrar 3-8. Si hay más, agrupar o priorizar los principales. |
| Formato preferido | Cards en grid (3-4 cols desktop, 1-2 mobile) |
| Contenido por card | Icon/image + título + 1-2 líneas descripción + optional link |
| Expandir detalle | Link "Learn more" a anchor o sección expandida. No modal. |
| Orden | Servicio principal primero. Orden por popularidad o revenue. |

### 8.3 Testimonials section

| Aspecto | Guideline |
|---------|-----------|
| Cantidad | 3-6 visibles. Si hay más, carousel manual. |
| Contenido mínimo | Quote + nombre + ciudad/ubicación |
| Contenido ideal | Quote + nombre + ciudad + rating + fuente (Google/Yelp) |
| Foto del reviewer | Solo si es real. No usar avatars genéricos. |
| Longitud del quote | 2-4 líneas. Truncar con "..." si es muy largo. |
| Layout | Cards en row (desktop) o carousel (mobile) |

### 8.4 FAQ section

| Aspecto | Guideline |
|---------|-----------|
| Cuándo incluir | Si hay ≥ 4 preguntas relevantes para el nicho |
| Formato | Accordion (expandible) |
| Cantidad | 4-8 preguntas. No más de 10. |
| Schema markup | Obligatorio: `FAQPage` structured data |
| Default state | Todo cerrado. O solo el primero abierto. |
| Contenido | Preguntas reales del nicho, no relleno genérico |

### 8.5 Contact section

| Aspecto | Guideline |
|---------|-----------|
| Ubicación | Última sección antes del footer |
| Elementos | Form + phone + address + hours + map |
| Map | Embed estático o thumbnail con link a Google Maps |
| Phone | Click-to-call (`tel:` link) visible y grande |
| Hours | Solo si el negocio las tiene definidas |
| Form | Ver reglas de formularios (sección 3.2) |

### 8.6 Footer

| Aspecto | Guideline |
|---------|-----------|
| Contenido mínimo | Business name + address + phone + © year |
| Contenido recomendado | + service area + nav links + social icons + license info |
| Social icons | Solo redes donde el negocio tiene presencia real |
| Legal | Privacy policy link si hay formulario |
| Diseño | Fondo oscuro o contrastante con el body |
| CTA en footer | Opcional último CTA, puede ser banner o inline |

---

## 9. Performance como UX

| Métrica | Target | Impacto UX |
|---------|--------|-----------|
| LCP (Largest Contentful Paint) | < 2.5s | Percepción de velocidad |
| FID (First Input Delay) | < 100ms | Respuesta a interacción |
| CLS (Cumulative Layout Shift) | < 0.1 | Estabilidad visual |
| Total page weight | < 1.5MB | Carga en 3G |
| Hero image | < 200KB (WebP, optimizada) | First paint rápido |
| Fonts | < 100KB total | No flash de texto |

**Reglas de performance:**
- `loading="lazy"` en todas las imágenes excepto hero
- `fetchpriority="high"` en hero image
- Fonts: `display=swap` + preconnect
- No JavaScript blocking above the fold
- CSS crítico inline, resto deferred
- Imágenes: `srcset` + `sizes` obligatorio para hero y service images

---

## 10. Accesibilidad (a11y)

| Requisito | Implementación |
|-----------|---------------|
| Contraste | WCAG AA mínimo (4.5:1 texto normal, 3:1 texto grande) |
| Focus visible | `outline` o `ring` visible en todos los interactivos |
| Skip to content | Link oculto visualmente, visible con focus |
| Alt text | Descriptivo para informativas. `alt=""` para decorativas. |
| Heading order | H1 → H2 → H3 sin saltos |
| Form labels | `<label>` explícito vinculado con `for`. No solo placeholder. |
| Error messages | Inline, con `role="alert"`. Color + texto (no solo color). |
| `prefers-reduced-motion` | Respetar: desactivar animaciones |
| `prefers-color-scheme` | Opcional pero recomendado para dark/light |
| Keyboard nav | Tab order lógico. No tab traps. |
| ARIA | Solo cuando HTML semántico no alcanza. No ARIA soup. |
| Language | `<html lang="en">` obligatorio |
| Touch targets | ≥ 44x44px en mobile |

---

## 11. Reglas de variación entre landings

Para evitar que 2 landings del mismo nicho tengan la misma experiencia:

| Dimensión | Cómo variar |
|-----------|-------------|
| CTA copy | Rotar entre acción directa ("Call Now"), beneficio ("Get Free Estimate"), urgencia ("Same-Day Service") |
| CTA placement | Variar entre sticky bar vs float button vs inline-only |
| Trust signal lead | Alternar qué trust signal va primero (reviews vs years vs badges) |
| Service display | Alternar entre grid cards, icon list, tabbed sections |
| Testimonial layout | Alternar entre carousel, static grid, single featured |
| Form position | Alternar entre sección dedicada, sidebar (desktop), inline con hero |
| Hero style | Variar entre image-bg, split layout, solid color, video-bg |
| Section dividers | Alternar entre wave, angle, straight, none |
| Scroll animations | Alternar entre fade-up, fade-in, slide-from-side, none |
| Color weight | Variar si el color primario domina el hero o las secciones intermedias |

**Regla:** Documentar las elecciones de la landing anterior del mismo nicho y elegir al menos 4 variaciones de esta tabla para la siguiente.

---

## 12. Checklist de validación UX

Antes de entregar una landing, verificar:

- [ ] ¿El hero comunica qué + dónde en < 3 segundos?
- [ ] ¿Hay CTA visible above the fold en mobile?
- [ ] ¿Máximo 3 CTAs primarios en toda la landing?
- [ ] ¿Textos de CTA son diferentes entre sí?
- [ ] ¿Hay ≥ 2 trust signals en el primer scroll?
- [ ] ¿Formulario tiene ≤ 4 campos?
- [ ] ¿Touch targets ≥ 44px en mobile?
- [ ] ¿No hay horizontal scroll no intencional en mobile?
- [ ] ¿Phone numbers son `tel:` links?
- [ ] ¿No hay anti-patrones de la sección 7?
- [ ] ¿Heading hierarchy es H1 → H2 → H3 sin saltos?
- [ ] ¿Contraste cumple WCAG AA?
- [ ] ¿`prefers-reduced-motion` respetado?
- [ ] ¿LCP target < 2.5s?
- [ ] ¿Se variaron ≥ 4 dimensiones respecto a la landing anterior del mismo nicho?

---

## Completion

`ux-guidelines.md` es referencia exclusiva del skill `design-database`.
Define reglas de experiencia de usuario, patrones de interacción y accesibilidad.
No contiene lógica de arquitectura de secciones, tipografía ni paletas.
Cualquier decisión UX debe validarse contra este archivo.
