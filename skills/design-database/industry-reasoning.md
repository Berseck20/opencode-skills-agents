# Industry Reasoning — design-database

> Lógica de razonamiento por industria para landing pages de negocios locales US.
> Define cómo adaptar diseño, contenido y UX según el nicho específico.
> No inventar lógica. Usar solo las reglas definidas aquí.

---

## 1. Modelo de razonamiento

Cada nicho tiene un **perfil de decisión del cliente** que determina cómo debe construirse la landing.

### 1.1 Variables de decisión

| Variable | Pregunta que responde | Valores posibles |
|----------|----------------------|------------------|
| `urgency` | ¿El cliente necesita el servicio ya? | `immediate` / `planned` / `mixed` |
| `trust_weight` | ¿Cuánto influye la confianza en la decisión? | `critical` / `high` / `moderate` |
| `price_sensitivity` | ¿El precio es factor decisivo? | `high` / `moderate` / `low` |
| `visual_proof` | ¿El cliente necesita ver resultados antes de contratar? | `essential` / `helpful` / `minimal` |
| `decision_maker` | ¿Quién toma la decisión? | `homeowner` / `business` / `individual` / `family` |
| `repeat_service` | ¿Es servicio recurrente o one-time? | `recurring` / `one-time` / `both` |
| `comparison_behavior` | ¿El cliente compara múltiples proveedores? | `heavy` / `moderate` / `light` |
| `emotional_weight` | ¿La decisión tiene carga emocional? | `high` / `moderate` / `low` |

### 1.2 Cómo impactan las variables en el diseño

| Variable | Valor alto/critical | Impacto en landing |
|----------|--------------------|--------------------|
| `urgency: immediate` | — | Phone CTA prominente, sticky CTA, "Available 24/7" badge, minimal scroll to contact |
| `trust_weight: critical` | — | Reviews above fold, licencias visibles, years in business, garantías |
| `price_sensitivity: high` | — | "Free Estimate" CTA, no mostrar precios altos, enfatizar valor |
| `visual_proof: essential` | — | Gallery grande, before/after, portfolio section obligatoria |
| `comparison_behavior: heavy` | — | Differentiators section, "Why Choose Us", comparison table |
| `emotional_weight: high` | — | Tone cálido, testimonials emocionales, fotos de personas reales |

---

## 2. Perfiles de industria

### 2.1 HOME SERVICES — Exterior

**Nichos:** Landscaping, Lawn Care, Tree Service, Fencing, Paving, Pressure Washing, Pool Service, Irrigation

| Variable | Valor |
|----------|-------|
| `urgency` | `mixed` (seasonal planned + storm/emergency) |
| `trust_weight` | `high` |
| `price_sensitivity` | `high` |
| `visual_proof` | `essential` |
| `decision_maker` | `homeowner` |
| `repeat_service` | `both` |
| `comparison_behavior` | `heavy` |
| `emotional_weight` | `moderate` |

**Reglas de diseño:**
- Gallery/portfolio es **obligatoria** — mínimo 6 imágenes o 3 before/after
- Mostrar seasonal services (spring cleanup, fall prep, snow removal) según época
- CTA principal: "Get Free Estimate" o "Request Quote"
- Trust signals obligatorios: years in business, insured/licensed, local reviews
- Service area map o lista de cities served
- Tone: profesional pero accesible, no corporativo

**Secciones recomendadas (orden):**
1. Hero con resultado visual (jardín terminado, not crew working)
2. Trust bar (reviews + years + insured)
3. Services grid (4-6 principales)
4. Before/After gallery
5. Process (3-4 steps)
6. Testimonials
7. Service area
8. Contact + form

**Variaciones por sub-nicho:**

| Sub-nicho | Diferenciador clave | Ajuste |
|-----------|--------------------|---------| 
| Landscaping | Diseño creativo, transformación | Gallery hero, emphasis en diseño |
| Lawn Care | Mantenimiento, confiabilidad | Recurring service plans, trust en consistencia |
| Tree Service | Seguridad, emergencia | Emergency badge, insurance prominente, certified arborist |
| Pressure Washing | Resultado inmediato, satisfacción visual | Before/after hero, video si posible |
| Pool Service | Estacionalidad, técnico | Seasonal pricing, certifications, chemical safety |

---

### 2.2 HOME SERVICES — Interior/Trades

**Nichos:** Plumbing, HVAC, Electrical, Painting, Flooring, Remodeling, Handyman, Appliance Repair

| Variable | Valor |
|----------|-------|
| `urgency` | `immediate` (plumbing/HVAC emergency) a `planned` (remodeling) |
| `trust_weight` | `critical` |
| `price_sensitivity` | `moderate` a `high` |
| `visual_proof` | `helpful` a `essential` (remodeling) |
| `decision_maker` | `homeowner` |
| `repeat_service` | `both` |
| `comparison_behavior` | `heavy` |
| `emotional_weight` | `moderate` (stress por emergencia o inversión grande) |

**Reglas de diseño:**
- **Servicios de emergencia** (plumbing, HVAC, electrical): Phone CTA gigante, "24/7 Emergency Service", response time prominente
- **Servicios planificados** (remodeling, flooring): Gallery, process section, financing info
- Licencias y seguros son **críticos** — mostrar siempre above fold
- BBB rating si existe
- Warranties/guarantees section

**Variaciones por sub-nicho:**

| Sub-nicho | `urgency` | Ajuste principal |
|-----------|-----------|-----------------|
| Plumbing | `immediate` | 24/7 badge, phone first, "Same-Day Service", emergency pricing transparency |
| HVAC | `mixed` | Seasonal (AC summer, heating winter), maintenance plans, financing |
| Electrical | `mixed` | Safety-first messaging, licensed electrician badge, code compliance |
| Painting | `planned` | Color consultation CTA, gallery essential, room visualizer if possible |
| Remodeling | `planned` | Portfolio hero, process steps, financing, timeline expectations |
| Handyman | `mixed` | Service list amplia, "No Job Too Small", flat rate messaging |

---

### 2.3 CONSTRUCTION & ROOFING

**Nichos:** Roofing, General Contractor, Concrete, Masonry, Siding, Windows, Gutters

| Variable | Valor |
|----------|-------|
| `urgency` | `mixed` (storm damage = immediate, new roof = planned) |
| `trust_weight` | `critical` |
| `price_sensitivity` | `moderate` (inversión grande → valor > precio) |
| `visual_proof` | `essential` |
| `decision_maker` | `homeowner` |
| `repeat_service` | `one-time` |
| `comparison_behavior` | `heavy` |
| `emotional_weight` | `high` (inversión significativa, miedo a scams) |

**Reglas de diseño:**
- Financing options prominentes (inversiones $5K-$50K+)
- Manufacturer certifications (GAF, Owens Corning, etc.)
- Warranty details section
- Insurance claim assistance messaging (storm damage)
- Project timeline/process es obligatoria
- "Free Inspection" como CTA principal
- Galería con proyectos completados — photos reales obligatorias

**Secciones recomendadas:**
1. Hero con proyecto completado
2. Trust bar (licensed + insured + certified + years)
3. "Why Choose Us" con differentiators
4. Services
5. Gallery/Portfolio
6. Process (inspection → quote → work → cleanup)
7. Financing info
8. Testimonials
9. Service area
10. Contact

---

### 2.4 AUTOMOTIVE

**Nichos:** Auto Repair, Auto Body, Towing, Oil Change, Tire Shop, Car Wash, Detailing

| Variable | Valor |
|----------|-------|
| `urgency` | `immediate` (towing, breakdown) a `planned` (detailing, oil change) |
| `trust_weight` | `critical` (confianza en mecánico) |
| `price_sensitivity` | `high` |
| `visual_proof` | `helpful` |
| `decision_maker` | `individual` |
| `repeat_service` | `recurring` |
| `comparison_behavior` | `moderate` |
| `emotional_weight` | `moderate` (stress por carro roto + miedo a ser estafado) |

**Reglas de diseño:**
- ASE certification, dealer-level equipment badges
- Transparent pricing o "Free Diagnostic" CTA
- Common services list con precios (si los tienen)
- "Check Engine Light?" messaging directo
- Fleet services si aplica (B2B angle)
- Loyalty/maintenance plans para recurring

**Variaciones:**

| Sub-nicho | Ajuste |
|-----------|--------|
| Towing | Phone CTA máximo, response time "20 min or less", coverage map, 24/7 |
| Auto Repair | Trust-heavy, ASE badges, "Honest Mechanic" messaging, warranty on parts |
| Detailing | Visual-heavy gallery, packages/pricing table, before/after |
| Car Wash | Membership/plans, location map, simple pricing grid |

---

### 2.5 FOOD & RESTAURANT

**Nichos:** Restaurant, Bakery, Café, Catering, Food Truck, Bar, Pizza

| Variable | Valor |
|----------|-------|
| `urgency` | `immediate` (tengo hambre) a `planned` (catering) |
| `trust_weight` | `moderate` |
| `price_sensitivity` | `moderate` |
| `visual_proof` | `essential` (food photography) |
| `decision_maker` | `individual` / `family` |
| `repeat_service` | `recurring` |
| `comparison_behavior` | `light` |
| `emotional_weight` | `high` (experiencia, antojo, celebraciones) |

**Reglas de diseño:**
- **Food photography es TODO** — sin buenas fotos, la landing no funciona
- Menú visible o linkeable (no PDF descargable, inline o link a menu page)
- Hours + location above fold o primer scroll
- Online ordering / reservation CTA prominente
- Ambiance photos (interior, patio, bar)
- Tone: cálido, invitante, sensorial
- Warm Organic profile casi siempre

**Secciones recomendadas:**
1. Hero con food photography hero o ambiance
2. Quick info bar (hours + address + phone)
3. Featured menu items / specialties
4. Gallery (food + ambiance)
5. About / story
6. Reviews
7. Catering/events (si aplica)
8. Location + map + hours
9. Footer con social links

**Diferencias clave:**
| Sub-nicho | Ajuste |
|-----------|--------|
| Fine dining | Dark Cinematic profile, reservation-first CTA, wine list/tasting |
| Fast casual | Clean Corporate o Modern Starter, online ordering CTA, menu pricing |
| Bakery/Café | Warm Organic, specialties showcase, seasonal items |
| Catering | Process section, packages, event types served, inquiry form |
| Food Truck | Location schedule, social feed, "Find Us Today" con map |

---

### 2.6 HEALTH & WELLNESS

**Nichos:** Dental, Chiropractic, Physical Therapy, Med Spa, Dermatology, Veterinary, Optometry

| Variable | Valor |
|----------|-------|
| `urgency` | `planned` (chequeos) a `immediate` (dolor, emergencia dental) |
| `trust_weight` | `critical` |
| `price_sensitivity` | `moderate` (salud > precio, pero insurance matters) |
| `visual_proof` | `helpful` (before/after en dental cosmético, medspa) |
| `decision_maker` | `individual` / `family` |
| `repeat_service` | `recurring` |
| `comparison_behavior` | `heavy` |
| `emotional_weight` | `high` (miedo, dolor, vanidad, salud de mascotas) |

**Reglas de diseño:**
- Doctor/team bios con credenciales — obligatorio
- "New Patient" CTA específico (no genérico "Contact Us")
- Insurance accepted list o "We accept most insurances"
- HIPAA compliance note si hay forms
- Tone: profesional + empático, nunca cold
- Office photos reales (instalaciones limpias, modernas)
- Patient reviews con condiciones tratadas (sin violar privacidad)

**Variaciones:**
| Sub-nicho | Ajuste |
|-----------|--------|
| Dental | Emergency dental badge, "Accepting New Patients", smile gallery, cosmetic vs general split |
| Chiropractic | Pain-point messaging, "First Visit Free", conditions treated list |
| Med Spa | Before/after essential, treatment menu, Dark Cinematic o Warm Organic |
| Veterinary | Pet-friendly tone, emergency hours, species served, Warm Organic profile |

---

### 2.7 BEAUTY & PERSONAL CARE

**Nichos:** Hair Salon, Barbershop, Nail Salon, Lash/Brow Studio, Tattoo Studio, Spa

| Variable | Valor |
|----------|-------|
| `urgency` | `planned` |
| `trust_weight` | `high` |
| `price_sensitivity` | `moderate` |
| `visual_proof` | `essential` (portfolio del artista) |
| `decision_maker` | `individual` |
| `repeat_service` | `recurring` |
| `comparison_behavior` | `moderate` |
| `emotional_weight` | `high` (autoestima, confianza, expresión personal) |

**Reglas de diseño:**
- Portfolio/gallery es la sección más importante
- Booking CTA (online scheduling si lo tienen)
- Stylist/artist profiles con portfolio individual
- Service menu con precios (estándar en esta industria)
- Instagram integration o feed visual
- Ambiance/interior photos importan mucho

**Variaciones:**
| Sub-nicho | Profile | Ajuste |
|-----------|---------|--------|
| Hair Salon | Modern Starter | Stylist showcase, color transformations gallery |
| Barbershop | Bold Industrial o Dark Cinematic | Masculine aesthetic, walk-ins welcome, services simple |
| Nail Salon | Modern Starter o Warm Organic | Gallery-first, seasonal designs, loyalty program |
| Tattoo Studio | Dark Cinematic | Artist portfolios individual, custom vs flash, aftercare info |
| Spa/Massage | Warm Organic | Tranquil imagery, packages, gift certificates CTA |

---

### 2.8 PROFESSIONAL SERVICES

**Nichos:** Law Firm, Accounting, Insurance, Financial Advisor, Consulting, Real Estate Agent

| Variable | Valor |
|----------|-------|
| `urgency` | `mixed` (accidente legal = immediate, taxes = seasonal, insurance = planned) |
| `trust_weight` | `critical` |
| `price_sensitivity` | `low` a `moderate` |
| `visual_proof` | `minimal` |
| `decision_maker` | `individual` / `business` |
| `repeat_service` | `both` |
| `comparison_behavior` | `heavy` |
| `emotional_weight` | `high` (legal stress, financial anxiety) |

**Reglas de diseño:**
- Credenciales y experiencia son el contenido principal
- "Free Consultation" CTA estándar
- Practice areas / services con descripciones completas
- Case results / success metrics si es legal
- Professional headshots obligatorias
- Tone: authoritative pero accesible, nunca casual
- Clean Corporate profile siempre

**Variaciones:**
| Sub-nicho | Ajuste |
|-----------|--------|
| Personal Injury | Urgency high, "No Win No Fee", case results, 24/7 availability |
| Criminal Defense | "Immediate Help", phone prominente, confidentiality emphasis |
| Family Law | Empathetic tone, "Compassionate Representation" |
| CPA/Accounting | Seasonal (tax season), service packages, industries served |
| Real Estate | Listings integration, market stats, area expertise, Modern Starter profile |
| Insurance | Quote tool/CTA, carriers represented, coverage types grid |

---

### 2.9 FITNESS & RECREATION

**Nichos:** Gym, CrossFit, Yoga Studio, Martial Arts, Dance Studio, Personal Trainer, Sports Facility

| Variable | Valor |
|----------|-------|
| `urgency` | `planned` (New Year, summer prep) |
| `trust_weight` | `moderate` |
| `price_sensitivity` | `high` (memberships son commoditized) |
| `visual_proof` | `helpful` (facility, transformations) |
| `decision_maker` | `individual` |
| `repeat_service` | `recurring` |
| `comparison_behavior` | `heavy` (muchas opciones) |
| `emotional_weight` | `high` (motivación, inseguridad, aspiración) |

**Reglas de diseño:**
- "Free Trial" o "First Class Free" CTA obligatorio
- Class schedule visible o linkeable
- Membership/pricing tiers
- Facility photos reales
- Trainer/instructor bios
- Community feel — group photos, events
- Transformation stories (con permiso)

**Variaciones:**
| Sub-nicho | Profile | Ajuste |
|-----------|---------|--------|
| Gym/CrossFit | Bold Industrial | Intensity imagery, WODs, community focus, results |
| Yoga/Pilates | Warm Organic | Serene imagery, class types, instructor certs, mindfulness tone |
| Martial Arts | Bold Industrial | Discipline showcase, belt system, kids programs, trial class |
| Dance Studio | Modern Starter | Performance gallery, class calendar, recital info, age groups |
| Personal Trainer | Dark Cinematic o Bold Industrial | Transformation gallery, credentials, program types |

---

### 2.10 HOME & LIFESTYLE SERVICES

**Nichos:** Cleaning, Moving, Junk Removal, Locksmith, Pest Control, Interior Design, Organizing

| Variable | Valor |
|----------|-------|
| `urgency` | `mixed` (locksmith = immediate, cleaning = planned) |
| `trust_weight` | `high` (strangers entering your home) |
| `price_sensitivity` | `high` |
| `visual_proof` | `helpful` |
| `decision_maker` | `homeowner` |
| `repeat_service` | `both` |
| `comparison_behavior` | `heavy` |
| `emotional_weight` | `moderate` |

**Reglas de diseño:**
- Background checks / bonded & insured prominente
- Pricing transparency (flat rate, hourly, packages)
- "Book Online" CTA si tienen scheduling
- Satisfaction guarantee badge
- Service checklist (qué incluye vs qué no)
- Before/after para cleaning, organizing, junk removal

**Variaciones:**
| Sub-nicho | Ajuste |
|-----------|--------|
| Cleaning | Recurring plan pricing, checklist, eco-friendly badge if applicable |
| Moving | Quote calculator CTA, service area, packing services, insurance info |
| Locksmith | 24/7 emergency, response time, "On My Way" urgency, phone CTA max |
| Pest Control | Pest types treated, eco/pet-safe badge, recurring plans, seasonal pests |
| Junk Removal | Pricing transparency, items accepted list, donation/recycling messaging |

---

### 2.11 EDUCATION & CHILDCARE

**Nichos:** Tutoring, Daycare, Preschool, Music Lessons, Driving School, Trade School

| Variable | Valor |
|----------|-------|
| `urgency` | `planned` |
| `trust_weight` | `critical` (children involved) |
| `price_sensitivity` | `moderate` |
| `visual_proof` | `helpful` |
| `decision_maker` | `family` |
| `repeat_service` | `recurring` |
| `comparison_behavior` | `heavy` |
| `emotional_weight` | `high` (child safety, future, development) |

**Reglas de diseño:**
- Safety and credentials FIRST (licenses, certifications, background checks)
- Staff bios with qualifications
- Programs/curriculum overview
- Age groups served clearly
- Facility photos (bright, clean, safe-looking)
- Parent testimonials
- "Schedule a Tour" CTA for childcare/preschool
- Tone: warm, professional, reassuring

---

### 2.12 EVENTS & ENTERTAINMENT

**Nichos:** DJ, Photography, Videography, Event Planning, Florist, Photo Booth, Venue

| Variable | Valor |
|----------|-------|
| `urgency` | `planned` (date-driven) |
| `trust_weight` | `high` (can't redo a wedding) |
| `price_sensitivity` | `moderate` |
| `visual_proof` | `essential` (portfolio es todo) |
| `decision_maker` | `individual` / `family` |
| `repeat_service` | `one-time` |
| `comparison_behavior` | `heavy` |
| `emotional_weight` | `high` (once-in-a-lifetime events) |

**Reglas de diseño:**
- Portfolio gallery dominante — hero debe ser portfolio piece
- Event types served (weddings, corporate, quinceañera, etc.)
- Packages con pricing ranges (estándar en industria)
- Availability checker o "Check My Date" CTA
- Vendor partnerships / "Featured in" (The Knot, WeddingWire)
- Emotional storytelling allowed
- Dark Cinematic o Warm Organic profile

---

## 3. Lógica de temporada (Seasonal Reasoning)

| Temporada | Nichos afectados | Ajuste en landing |
|-----------|-----------------|-------------------|
| **Spring** (Mar-May) | Landscaping, HVAC, Pest Control, Cleaning | "Spring Special", seasonal service highlight, fresh imagery |
| **Summer** (Jun-Aug) | Pool, HVAC (AC), Lawn Care, Painting | AC emergency messaging, outdoor living focus |
| **Fall** (Sep-Nov) | Tree Service, HVAC (Heating), Roofing, Gutter | "Winterize" messaging, fall cleanup, heating prep |
| **Winter** (Dec-Feb) | Plumbing (frozen pipes), Snow Removal, HVAC | Emergency services prominence, "Don't Wait" urgency |
| **Tax Season** (Jan-Apr) | Accounting, Financial | Filing deadlines, tax prep packages |
| **Wedding Season** (May-Oct) | Photography, Florist, DJ, Venue, Catering | "Book Before It's Too Late", portfolio weddings |
| **Back to School** (Aug-Sep) | Tutoring, Daycare, Driving School | Enrollment CTAs, program schedules |
| **Holiday** (Nov-Dec) | Cleaning, Catering, Florist, Bakery | Holiday packages, gift certificates, party planning |

**Regla:** Si la landing se genera durante una temporada activa para el nicho, destacar el servicio estacional en el hero o primer scroll. Si no, usar messaging evergreen.

---

## 4. Lógica geográfica

| Factor | Impacto |
|--------|---------|
| **City size** | Metro area → más competencia → differentiators section critical. Small town → community focus, "locally owned" |
| **Climate** | Afecta servicios estacionales, imagery (nieve, sol, lluvia), y qué servicios destacar |
| **Demographics** | Median income afecta price_sensitivity. College town → younger audience → Modern Starter. Retirement community → accessibility focus |
| **Competition density** | Más competencia → más trust signals, comparison content, unique selling props |
| **Regional language** | "Pop" vs "Soda", "Yard" vs "Lawn" — usar terminología local |

**Regla:** El `research-seo-agent` debe proveer datos geográficos. Si no hay data → asumir suburban US defaults.

---

## 5. Matriz de decisión: Qué secciones incluir

| Sección | Cuándo es OBLIGATORIA | Cuándo es RECOMENDADA | Cuándo OMITIR |
|---------|----------------------|----------------------|---------------|
| Hero | Siempre | — | — |
| Trust bar | `trust_weight` = critical/high | — | — |
| Services | Siempre | — | — |
| Gallery/Portfolio | `visual_proof` = essential | `visual_proof` = helpful | `visual_proof` = minimal |
| Before/After | Home exterior, cleaning, detailing | Remodeling, painting | Professional services, legal |
| Process/How it Works | `comparison_behavior` = heavy | Siempre que haya ≥ 3 steps | Servicio obvio (car wash) |
| Pricing | Beauty, fitness, food | Cleaning, moving | Legal, medical, construction |
| Testimonials | Siempre si hay reviews | — | — |
| FAQ | Si hay ≥ 4 preguntas reales | — | Si hay < 4 |
| Team/About | Health, legal, education | General | No si el negocio no tiene equipo visible |
| Service Area | Service-at-location businesses | Storefront con delivery area | Pure storefront (restaurant, salon) |
| Financing | `price_sensitivity` + investment > $2K | Roofing, HVAC, remodeling | Low-cost services |
| Emergency badge | `urgency` = immediate | — | `urgency` = planned |
| Map | Storefront businesses | Service-area businesses | — |

---

## 6. Tone of voice por industria

| Categoría | Tone | Ejemplo de headline |
|-----------|------|-------------------|
| Home Services Exterior | Direct, confident, results-focused | "Transform Your Outdoor Space" |
| Home Services Trades | Reliable, urgent-capable, honest | "Fast, Honest Plumbing You Can Trust" |
| Construction | Solid, experienced, investment-worthy | "Built to Last — 25 Years of Excellence" |
| Automotive | Straight-talk, trustworthy, fair | "Honest Auto Repair — Fair Prices, Every Time" |
| Food & Restaurant | Warm, sensorial, inviting | "Handcrafted Flavors, Made Fresh Daily" |
| Health & Wellness | Professional, caring, reassuring | "Gentle Care for Your Whole Family" |
| Beauty | Aspirational, confident, personal | "Your Best Look Starts Here" |
| Professional Services | Authoritative, empathetic, experienced | "Experienced Advocates Fighting for You" |
| Fitness | Motivational, energetic, community | "Your Strongest Self Starts Today" |
| Education & Childcare | Nurturing, trustworthy, developmental | "Where Curious Minds Grow" |
| Events | Emotional, creative, memorable | "Capturing Moments That Last Forever" |

**Regla:** El tone NO debe contradecir el Visual Profile. Bold Industrial no usa language "gentle" y Warm Organic no usa language "aggressive".

---

## 7. Reglas de variación por industria

Para evitar que 2 landings del mismo nicho se vean iguales:

| Dimensión | Cómo rotar |
|-----------|-----------|
| Hero approach | Alternar entre resultado final (finished product) y acción en proceso (crew working) |
| Trust lead | Rotar qué trust signal va primero (reviews → years → certifications → awards) |
| Tone shade | Mismo tone base pero variar intensidad (confident vs bold, warm vs intimate) |
| CTA verb | Rotar verbo principal: Get / Request / Schedule / Call / Book / Claim |
| Section order | Mover gallery antes o después de services. Process antes o después de testimonials. |
| Headline formula | Alternar entre benefit-first ("Get a Beautiful Lawn") y identity-first ("Your Trusted Landscaper Since 2005") |
| Social proof type | Alternar entre review carousel, stats bar, single featured testimonial |

**Regla:** Registrar elecciones de la landing anterior del mismo nicho y variar ≥ 3 dimensiones.

---

## 8. Validación por industria

Antes de entregar, verificar:

- [ ] ¿El perfil de decisión del nicho está correctamente identificado?
- [ ] ¿Las secciones obligatorias para ese nicho están presentes?
- [ ] ¿El tone of voice corresponde a la categoría?
- [ ] ¿Los CTAs reflejan la `urgency` del nicho? (immediate → phone, planned → form/booking)
- [ ] ¿Los trust signals corresponden al `trust_weight`?
- [ ] ¿La visual proof está cubierta según el nivel requerido?
- [ ] ¿Se consideró la temporada actual para messaging?
- [ ] ¿Se variaron ≥ 3 dimensiones respecto a landing anterior del mismo nicho?
- [ ] ¿El tone no contradice el Visual Profile asignado?
- [ ] ¿La decisión de incluir/omitir pricing es correcta para el nicho?

---

## Completion

`industry-reasoning.md` es referencia exclusiva del skill `design-database`.
Define lógica de razonamiento por industria, perfiles de decisión y reglas de adaptación.
No contiene lógica de arquitectura de secciones, tipografía, paletas ni estilos CSS.
Cualquier decisión de adaptación por nicho debe validarse contra este archivo.