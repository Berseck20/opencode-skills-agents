# Landing Patterns — Design Database

> Read-only reference. Do not modify. Used by `niche-reasoning` and `landing-architecture`.

## How to use this file

1. Receive the niche classification and visual profile from `niche-reasoning`
2. Match to a primary pattern using the `Niche mapping` table below
3. Record: pattern name, section order, CTA strategy, signature element
4. Apply variation axes to avoid repetition between projects in the same niche
5. Adjust section count based on available data (`[NOT FOUND]` fields = skip section, do not leave empty)

---

## Anti-defaults — Mandatory awareness

Before selecting any pattern, internalize these. Every pattern below is designed to avoid them, but the builder must actively reject drift toward defaults during implementation.

| Anti-default | Description | Why it fails |
|---|---|---|
| Centered-everything | Every section centers heading + paragraph + button vertically stacked | Produces identical visual rhythm across all sections. No hierarchy contrast. |
| Purple gradient hero | Dark-to-purple gradient background with white centered text | Visually generic. Seen on thousands of AI-generated pages. Instant credibility loss. |
| Uniform rounded corners | `rounded-xl` on every card, button, image, and container | Removes visual tension. Everything looks soft and samey. |
| 01/02/03 numbered steps | Numbered process steps when content has no inherent sequence | Decorative numbering ≠ structure. Only use if order genuinely matters (e.g., booking flow). |
| Icon + heading + paragraph grid | 3-column grid where each column is icon → h3 → paragraph | The single most common AI layout. Immediately signals template. |
| Repeating identical CTAs | Same button text, same color, same placement every 2 sections | CTA fatigue. User stops seeing them after the second one. |
| Stock photo hero | Generic smiling people or handshake images | Destroys local trust. User knows it is not the real business. |

---

## Pattern catalog

---

### Pattern 1: EMERGENCY RESPONSE

**Intent:** Immediate action. User has an urgent problem and needs to call/book NOW.

**Total sections:** 3–5 (never more than 5)

**Visual rhythm:** Dense → sparse. High-density hero, then minimal supporting content.

```
┌─────────────────────────────────┐
│  ☎ PHONE NUMBER (large)         │
│  Single-line value prop         │
│  [CALL NOW]  [BOOK ONLINE]     │
│  ★★★★★ 4.9 · 200+ reviews     │
│  ✓ Licensed  ✓ 24/7  ✓ Local  │
├─────────────────────────────────┤
│  Service area map  │  3 key     │
│  (real coverage)   │  services  │
│                    │  listed    │
├─────────────────────────────────┤
│  "They came in 20 minutes..."  │
│  — Customer name, city         │
│  ────────────────────          │
│  "Fixed the leak same day..."  │
│  — Customer name, city         │
├─────────────────────────────────┤
│  ☎ PHONE  ·  Bottom CTA bar    │
└─────────────────────────────────┘
```

**Section order:**
1. Hero: phone-first with trust badges (licenses, ratings, availability)
2. Service area + core services (split layout, NOT centered)
3. Social proof: 2–3 short testimonials (inline, not cards)
4. Final CTA bar (sticky on mobile)
5. Optional: FAQ (only if data exists, max 4 questions)

**CTA strategy:**
- Primary CTA in hero: phone call (tap-to-call on mobile)
- Secondary CTA in hero: online booking/form
- Sticky bottom bar on mobile with phone number
- NO mid-page CTAs. The page is short enough that repetition is unnecessary.

**Signature element:** Pulsing availability indicator ("Available now — average response 23 min") or live service area map with real coverage zones.

**Niche mapping:** Plumber, electrician, locksmith, towing, HVAC emergency, water damage restoration, pest control (urgent), garage door repair.

**Variation axes within this pattern:**
- Hero layout: phone left + badges right VS phone centered + badges below
- Trust proof type: review stars VS "X jobs completed this month" VS license badges
- Map style: embedded map VS stylized service area illustration
- Testimonial format: inline quotes VS mini-cards with avatars

**Anti-patterns for this pattern:**
- Long pages. If it exceeds 5 sections, something is wrong.
- Image-heavy heroes. Emergency users want info, not ambiance.
- Form-first CTAs. Phone calls convert 3–5x better for emergencies.

---

### Pattern 2: TRUST BUILDER

**Intent:** Establish credibility for high-stakes decisions. User is researching, not impulse-buying.

**Total sections:** 5–7

**Visual rhythm:** Measured, steady. Consistent spacing. No visual surprises. Conveys stability.

```
┌─────────────────────────────────┐
│  Authority headline             │
│  (credentials or years in       │
│   business as subhead)          │
│                    [FREE CONSULT│
│                     ATION]      │
├────────────────┬────────────────┤
│  Credential    │  Professional  │
│  badges /      │  photo or      │
│  awards /      │  office photo  │
│  affiliations  │                │
├─────────────────────────────────┤
│  Practice areas / Services      │
│  ┌──────┐ ┌──────┐ ┌──────┐   │
│  │ Area │ │ Area │ │ Area │   │
│  │ 1    │ │ 2    │ │ 3    │   │
│  └──────┘ └──────┘ └──────┘   │
├─────────────────────────────────┤
│  Case results / Outcomes        │
│  (numbers, not stories)         │
│  $2.3M recovered │ 500+ cases  │
├─────────────────────────────────┤
│  Testimonials (longer form,     │
│  with full name + context)      │
├─────────────────────────────────┤
│  About / Team (photo + bio)     │
├─────────────────────────────────┤
│  Consultation form              │
│  (Name, Phone, Brief desc)      │
│  [SCHEDULE FREE CONSULTATION]   │
└─────────────────────────────────┘
```

**Section order:**
1. Hero: authority statement + primary credential + consultation CTA (split layout)
2. Credentials/awards/affiliations (badge wall or horizontal scroll)
3. Practice areas or services (cards or list — NOT icon grid)
4. Results/outcomes (data-driven: numbers, percentages, case counts)
5. Testimonials (long-form, with context: case type + outcome)
6. About/team (real photos mandatory, bios with credentials)
7. Consultation form (embedded, NOT a link to another page)

**CTA strategy:**
- Primary: "Free Consultation" form (bottom of page + hero button that scrolls to it)
- Secondary: phone number in header (visible but not dominant)
- NO aggressive CTAs. Trust-building requires patience. Max 2 CTA touchpoints.

**Signature element:** Results ticker (animated count-up of cases won, dollars recovered, years of experience) OR credential wall with real logos/badges.

**Niche mapping:** Lawyers (personal injury, family, criminal), financial advisors, accountants, medical specialists, insurance agents, wealth management.

**Variation axes within this pattern:**
- Hero split: text-left/image-right VS text-right/image-left VS full-width text with credentials as overlay badges
- Results display: large numbers in grid VS horizontal ticker VS vertical timeline of milestones
- Testimonial format: single featured testimonial VS carousel VS stacked quotes with case type tags
- Form position: dedicated final section VS sidebar that follows scroll

**Anti-patterns for this pattern:**
- Casual tone. These niches demand formality.
- Stock team photos. Real photos or no photos.
- Vague outcomes ("great results"). Specific numbers or nothing.

---

### Pattern 3: PORTFOLIO SHOWCASE

**Intent:** Show quality of work. User wants to SEE what the business can do before engaging.

**Total sections:** 5–8

**Visual rhythm:** Image-heavy → text-light. Wide visual blocks with minimal copy.

```
┌─────────────────────────────────┐
│                                 │
│  Full-bleed hero image          │
│  (best project photo)           │
│                                 │
│  Overlay: business name +       │
│  "Transforming [city] since     │
│   [year]"                       │
│              [SEE OUR WORK]     │
├─────────────────────────────────┤
│  Before ◄──slider──► After      │
│  ┌──────────┬──────────┐       │
│  │          │          │       │
│  │  Before  │  After   │       │
│  │          │          │       │
│  └──────────┴──────────┘       │
│  Project name · Location        │
├─────────────────────────────────┤
│  Project gallery                │
│  ┌─────┐┌───────────┐         │
│  │     ││           │         │
│  │ img ││   img     │         │
│  │     ││           │         │
│  ├─────┤├─────┬─────┤         │
│  │ img ││ img │ img │         │
│  └─────┘└─────┴─────┘         │
├─────────────────────────────────┤
│  Services (brief, visual)       │
│  Photo + service name + 1 line  │
├─────────────────────────────────┤
│  Testimonials with project      │
│  photos (review tied to work)   │
├─────────────────────────────────┤
│  [GET A FREE ESTIMATE]          │
│  Project type selector + zip    │
└─────────────────────────────────┘
```

**Section order:**
1. Hero: full-bleed best project image with minimal overlay text
2. Featured project: before/after slider OR large showcase with description
3. Project gallery: masonry or bento grid (NOT uniform cards)
4. Services: visual cards with project photo per service
5. Testimonials: tied to specific projects (review + project photo)
6. Process: how it works (only if genuinely sequential — 3 steps max)
7. CTA: estimate form with project type dropdown
8. Optional: service area or certifications

**CTA strategy:**
- Primary: "Get a Free Estimate" with project type selector
- Hero CTA: "See Our Work" (scrolls to gallery, NOT external link)
- End-of-gallery CTA: "Start Your Project"
- CTAs vary in text: estimate → quote → project — never the same word twice

**Signature element:** Interactive before/after slider on the featured project, OR masonry gallery with hover-to-expand.

**Niche mapping:** Landscaping, remodeling, painting, flooring, roofing, fencing, pool construction, interior design, photography, custom furniture, auto detailing.

**Variation axes within this pattern:**
- Hero type: full-bleed photo VS split (photo + text) VS video background
- Gallery layout: masonry VS bento grid VS horizontal scroll VS lightbox grid
- Before/after: slider component VS side-by-side VS toggle overlay
- Service cards: photo-dominant VS text-dominant with thumbnail

**Anti-patterns for this pattern:**
- Tiny images. Portfolio pages need large, high-quality visuals.
- Generic descriptions. Each project should have specific details (scope, location, materials).
- No before/after. If the business transforms things, showing only "after" wastes the strongest proof.

---

### Pattern 4: LOCAL AUTHORITY

**Intent:** Establish the business as the go-to local choice. Familiar, trustworthy, part of the community.

**Total sections:** 5–7

**Visual rhythm:** Balanced. Equal weight to images and text. Warm, approachable.

```
┌─────────────────────────────────┐
│  Business photo    │  Headline  │
│  (storefront or    │  Value prop│
│   team at work)    │  City name │
│                    │            │
│                    │ [BOOK NOW] │
│                    │ ☎ (555)... │
├─────────────────────────────────┤
│  Services overview              │
│  ┌──────────────┐ Description  │
│  │   Service    │ of what sets │
│  │   image      │ this apart   │
│  └──────────────┘              │
│  ┌──────────────┐ Description  │
│  │   Service    │ of second    │
│  │   image      │ offering     │
│  └──────────────┘              │
├─────────────────────────────────┤
│  ★★★★★  Google Reviews          │
│  "Best [service] in [city]..."  │
│  Carousel of 3-5 real reviews   │
├─────────────────────────────────┤
│  About us                       │
│  Team photo + story paragraph   │
│  Years in business · Local ties │
├─────────────────────────────────┤
│  ┌─────────────────────────┐   │
│  │   Embedded Google Map   │   │
│  │   with business pin     │   │
│  └─────────────────────────┘   │
│  Address · Hours · Phone        │
├─────────────────────────────────┤
│  [CALL US] or [BOOK ONLINE]     │
└─────────────────────────────────┘
```

**Section order:**
1. Hero: split layout — real business photo + headline with city name + dual CTA (book + call)
2. Services: alternating image-text rows (NOT cards grid)
3. Reviews: Google reviews carousel or featured reviews with star rating
4. About: team/owner story with real photo + local connection emphasis
5. Location: embedded map + business info (address, hours, phone)
6. Final CTA: contextual ("Visit us today" / "Call to book")
7. Optional: specials/offers or community involvement

**CTA strategy:**
- Hero: dual CTA (primary action + phone)
- Mid-page: none (trust-building zone)
- Post-reviews: soft CTA ("See why [city] trusts us")
- Final: action CTA with business info
- Vary CTA formats: button → inline link → phone number → form

**Signature element:** Embedded Google Map with custom pin + business info card overlay, OR a "Why [City] Chooses Us" section with real local stats.

**Niche mapping:** Restaurants, auto repair, dental (general), veterinary, dry cleaning, bakery, barbershop, salon, florist, local retail, tutoring, daycare.

**Variation axes within this pattern:**
- Hero split: image-left/text-right VS image-right/text-left VS image-top/text-bottom
- Services layout: alternating rows VS tabbed interface VS accordion
- Reviews format: carousel VS grid of cards VS single featured + link to Google
- Map integration: full-width embedded VS corner card VS illustrated neighborhood map

**Anti-patterns for this pattern:**
- Missing city name. Local authority REQUIRES geographic anchoring in hero and H1.
- No real photos. This pattern depends entirely on authentic local imagery.
- Generic "About" sections. Must include specific local ties, years, community involvement.

---

### Pattern 5: SERVICE MENU

**Intent:** Help user find and compare specific services/prices. Decision is WHICH service, not WHETHER to hire.

**Total sections:** 4–6

**Visual rhythm:** Structured, scannable. Grid-based. Visual hierarchy through grouping.

```
┌─────────────────────────────────┐
│  Lifestyle/atmosphere image     │
│  "Your [service] destination    │
│   in [city]"                    │
│        [BOOK APPOINTMENT]       │
├─────────────────────────────────┤
│  Service categories (tabs/nav)  │
│  [Haircuts] [Color] [Treatments]│
├─────────────────────────────────┤
│  ┌──────────────────────────┐  │
│  │ Service    │ Desc │ Price│  │
│  ├────────────┼──────┼──────┤  │
│  │ Basic Cut  │ ...  │ $35 │  │
│  │ Style Cut  │ ...  │ $55 │  │
│  │ Color Full │ ...  │ $120│  │
│  └──────────────────────────┘  │
│  [BOOK THIS SERVICE]            │
├─────────────────────────────────┤
│  Featured work / Instagram grid │
├─────────────────────────────────┤
│  Reviews + "Most booked" badge  │
├─────────────────────────────────┤
│  Location · Hours · Booking     │
└─────────────────────────────────┘
```

**Section order:**
1. Hero: lifestyle image + tagline + primary booking CTA
2. Service navigation: category tabs or anchored nav
3. Service listing: organized by category with name + description + price + individual booking CTA
4. Visual proof: work gallery or Instagram feed embed
5. Social proof: reviews with "most popular service" badges
6. Contact/booking: location + hours + booking link or form

**CTA strategy:**
- Hero: single booking CTA
- Per-service: individual "Book This" CTAs (each links to booking with service pre-selected)
- End: general booking + contact info
- CTAs are SERVICE-SPECIFIC, not generic

**Signature element:** Interactive service grid with filtering by category and price range, OR "Most Popular" badges dynamically assigned.

**Niche mapping:** Salon, spa, barbershop, nail studio, cleaning services (residential), car wash, pet grooming, tutoring center, fitness classes, photography packages.

**Variation axes within this pattern:**
- Service display: table VS cards VS accordion VS horizontal scroll per category
- Pricing: visible VS "Starting from" VS "Request quote"
- Category nav: horizontal tabs VS sidebar VS dropdown
- Gallery: grid VS carousel VS before/after per service

**Anti-patterns for this pattern:**
- No prices (when industry norm is to show them). Salon without prices = bounce.
- One giant list. Services MUST be categorized.
- Missing individual service CTAs. "Book now" without service context creates friction.

---

### Pattern 6: NARRATIVE SCROLL

**Intent:** Tell a story. Build emotional connection. Business has a compelling origin, mission, or approach.

**Total sections:** 6–9 (long-form is intentional here)

**Visual rhythm:** Cinematic. Wide sections, generous whitespace, editorial typography.

```
┌─────────────────────────────────┐
│                                 │
│  Large editorial headline       │
│  (statement, not description)   │
│                                 │
│  Subhead with founder/origin    │
│                                 │
├─────────────────────────────────┤
│                                 │
│  Full-width story image         │
│                                 │
│  "It started in a garage in     │
│   [city] in [year]..."          │
│  (2-3 paragraphs, real story)   │
│                                 │
├─────────────────────────────────┤
│  Timeline or milestones         │
│  ── 2005 ── Started in garage   │
│  ── 2010 ── First storefront    │
│  ── 2018 ── 10,000th customer   │
│  ── 2024 ── Expanded to [city]  │
├─────────────────────────────────┤
│  Our approach / Philosophy      │
│  (what makes it different)      │
│  Image left │ Text right        │
├─────────────────────────────────┤
│  The team                       │
│  Individual photos + bios       │
├─────────────────────────────────┤
│  Testimonials (story-style,     │
│  longer form, with context)     │
├─────────────────────────────────┤
│  Services (brief, secondary)    │
├─────────────────────────────────┤
│  [JOIN OUR STORY]               │
│  Contact form with personal     │
│  touch                          │
└─────────────────────────────────┘
```

**Section order:**
1. Hero: editorial headline (a statement, not "Welcome to...") with NO CTA in hero
2. Origin story: full-width image + narrative paragraphs
3. Timeline/milestones: vertical timeline with years + events
4. Approach/philosophy: what makes this business different (split layout)
5. Team: individual photos with real bios (not roles, stories)
6. Testimonials: long-form, story-style
7. Services: brief overview (services are secondary to story here)
8. CTA: personal-touch form ("Tell us about your project" not "Get a quote")
9. Optional: community involvement or press mentions

**CTA strategy:**
- NO CTA in hero. Story pages earn the CTA.
- First CTA appears after story + social proof (section 6-7 area)
- CTA language is personal and warm, not transactional
- Maximum 2 CTA touchpoints in entire page

**Signature element:** Vertical timeline with real milestones, OR a founder quote in large editorial typography that breaks the layout.

**Niche mapping:** Family-owned restaurants, artisan bakeries, craft breweries, boutique fitness studios, independent bookstores, custom jewelers, family farms, heritage businesses, specialty trades with master craftspeople.

**Variation axes within this pattern:**
- Hero typography: oversized serif VS handwritten-style VS minimal sans
- Story layout: single column editorial VS two-column magazine VS full-bleed photo breaks
- Timeline: vertical VS horizontal VS scattered/organic placement
- Team display: grid of cards VS horizontal scroll VS featured founder + team secondary

**Anti-patterns for this pattern:**
- CTA in hero. Kills the narrative flow.
- Short generic "About" paragraph. This pattern requires real, detailed storytelling.
- Formal/corporate tone. Narrative = conversational, personal, specific.
- Using this pattern for businesses without a real story. If there is no narrative, use another pattern.

---

### Pattern 7: COMPARISON CLOSER

**Intent:** User is comparing options. Win on clear differentiation and remove friction to decide.

**Total sections:** 5–7

**Visual rhythm:** Structured, data-forward. Clean lines, high-contrast comparison elements.

```
┌─────────────────────────────────┐
│  Problem statement headline     │
│  "Tired of [common complaint]?" │
│  Our differentiator in 1 line   │
│           [GET FREE QUOTE]      │
├─────────────────────────────────┤
│  Why us vs alternatives         │
│  ┌───────┬────────┬──────────┐ │
│  │       │  Us    │ Typical  │ │
│  ├───────┼────────┼──────────┤ │
│  │Price  │ Fair   │ Hidden   │ │
│  │Speed  │ 24hr   │ 3-5 days │ │
│  │Warr.  │ 5 yr   │ 90 days  │ │
│  └───────┴────────┴──────────┘ │
├─────────────────────────────────┤
│  How it works                   │
│  Step 1 → Step 2 → Step 3      │
│  (only if process IS the        │
│   differentiator)               │
├─────────────────────────────────┤
│  Savings calculator or          │
│  cost estimator                 │
│  [Input] → [Result]            │
├─────────────────────────────────┤
│  Reviews focused on switching   │
│  "Switched from X, wish I'd    │
│   done it sooner..."           │
├─────────────────────────────────┤
│  Guarantee / Risk reversal      │
│  "100% satisfaction or..."     │
├─────────────────────────────────┤
│  [GET YOUR FREE QUOTE]          │
│  Simple form (zip + service)    │
└─────────────────────────────────┘
```

**Section order:**
1. Hero: problem-first headline + single differentiator + CTA
2. Comparison: "Us vs. Typical" table (specific, honest, data-backed)
3. Process: how it works (ONLY if the process itself is the differentiator)
4. Calculator/estimator: interactive element for cost/savings
5. Testimonials: focused on switching stories ("I used to use X, then...")
6. Guarantee: risk reversal (warranty, money-back, satisfaction guarantee)
7. CTA: simple quote form (minimal fields)

**CTA strategy:**
- Hero: "Get Free Quote" (direct, value-explicit)
- Post-comparison: "See How Much You Save"
- Final: "Get Your Free Quote" (repeat hero CTA with minor variation)
- CTAs reference the comparison: "Join 500+ families who switched"

**Signature element:** Interactive savings calculator or cost comparison tool, OR a comparison table with animated highlighting.

**Niche mapping:** Pest control, moving companies, insurance, home security, solar installation, lawn care, cleaning services (commercial), IT support, marketing agencies.

**Variation axes within this pattern:**
- Comparison format: table VS side-by-side cards VS checklist (✓/✗)
- Calculator type: savings calculator VS instant quote VS cost estimator VS ROI calculator
- Hero approach: problem-first VS stat-first ("Save $X/year") VS question-first
- Guarantee display: badge VS dedicated section VS banner

**Anti-patterns for this pattern:**
- Vague comparisons. "Better quality" means nothing. Use specific numbers.
- Bashing competitors by name. Compare against "typical" or "industry average".
- No guarantee. This pattern targets skeptical users who need risk reversal.

---

### Pattern 8: COMMUNITY HUB

**Intent:** Invite participation. Business is a gathering place or community institution.

**Total sections:** 5–7

**Visual rhythm:** Warm, open, welcoming. Generous imagery of people and spaces.

```
┌─────────────────────────────────┐
│  Community/group photo          │
│  "Welcome to [business]"       │
│  "Your [city] [type] since     │
│   [year]"                       │
│    [JOIN US]  [VISIT TODAY]     │
├─────────────────────────────────┤
│  What we offer                  │
│  ┌───────┐ ┌───────┐          │
│  │Classes│ │Events ││          │
│  │       │ │       │          │
│  └───────┘ └───────┘          │
│  ┌───────┐ ┌───────┐          │
│  │Member-│ │Kids   │          │
│  │ships  │ │prog.  │          │
│  └───────┘ └───────┘          │
├─────────────────────────────────┤
│  Upcoming events / Schedule     │
│  ┌────────────────────────┐    │
│  │ Mon 6pm │ Yoga Class   │    │
│  │ Wed 7pm │ Open Night   │    │
│  │ Sat 10am│ Kids Workshop│    │
│  └────────────────────────┘    │
├─────────────────────────────────┤
│  Community gallery              │
│  (real photos of real events)   │
├─────────────────────────────────┤
│  Member testimonials            │
│  (belonging, not quality)       │
├─────────────────────────────────┤
│  Visit info + map               │
│  [BECOME A MEMBER]              │
└─────────────────────────────────┘
```

**Section order:**
1. Hero: community photo + welcoming headline + dual CTA (join + visit)
2. Offerings: what is available (classes, programs, memberships — visual cards)
3. Schedule/events: upcoming events with dates and times
4. Community gallery: real photos from real events/sessions
5. Testimonials: focused on belonging and community experience
6. Visit info: map + hours + first-visit instructions
7. CTA: membership or first-visit offer

**CTA strategy:**
- Hero: "Join Us" + "Visit Today" (dual, equal weight)
- Post-schedule: "Register for [specific event]"
- Final: "Become a Member" or "Start Your Free Trial"
- CTAs reference community: "Join 200+ members" not "Sign up"

**Signature element:** Live/upcoming events schedule with registration links, OR community photo gallery with real event photos.

**Niche mapping:** Gym/CrossFit, yoga studio, martial arts, community center, church, co-working space, daycare, dance studio, music school, art studio, local clubs.

**Variation axes within this pattern:**
- Hero: group photo VS facility photo VS event action shot
- Schedule display: calendar grid VS list VS timeline
- Offerings: cards VS tabs VS illustrated icons with descriptions
- Gallery: masonry VS carousel VS featured event spotlight

**Anti-patterns for this pattern:**
- Individual-focused messaging. This pattern is about COMMUNITY, not personal benefit.
- No schedule or events. If there is nothing upcoming, this is the wrong pattern.
- Stock photos of diverse groups. Must be real community photos.

---

## Niche-to-pattern mapping — Quick reference

| Niche | Primary pattern | Fallback pattern |
|---|---|---|
| Plumber (emergency) | Emergency Response | Local Authority |
| Plumber (scheduled) | Local Authority | Comparison Closer |
| Electrician | Emergency Response | Local Authority |
| HVAC | Emergency Response | Comparison Closer |
| Locksmith | Emergency Response | — |
| Lawyer (PI) | Trust Builder | Comparison Closer |
| Lawyer (family) | Trust Builder | Narrative Scroll |
| Accountant | Trust Builder | Local Authority |
| Financial advisor | Trust Builder | — |
| Dentist (general) | Local Authority | Trust Builder |
| Dentist (cosmetic) | Portfolio Showcase | Trust Builder |
| Veterinarian | Local Authority | Community Hub |
| Landscaping | Portfolio Showcase | Comparison Closer |
| Remodeling | Portfolio Showcase | Trust Builder |
| Painting | Portfolio Showcase | Local Authority |
| Roofing | Portfolio Showcase | Comparison Closer |
| Salon / Barbershop | Service Menu | Local Authority |
| Spa | Service Menu | Narrative Scroll |
| Cleaning (residential) | Service Menu | Comparison Closer |
| Cleaning (commercial) | Comparison Closer | Service Menu |
| Restaurant | Local Authority | Narrative Scroll |
| Bakery | Narrative Scroll | Local Authority |
| Auto repair | Local Authority | Trust Builder |
| Auto detailing | Portfolio Showcase | Service Menu |
| Pest control | Comparison Closer | Emergency Response |
| Moving company | Comparison Closer | Trust Builder |
| Solar installation | Comparison Closer | Trust Builder |
| Gym / CrossFit | Community Hub | Service Menu |
| Yoga studio | Community Hub | Narrative Scroll |
| Dance studio | Community Hub | Service Menu |
| Daycare | Community Hub | Trust Builder |
| Photography | Portfolio Showcase | Service Menu |
| Real estate agent | Trust Builder | Local Authority |
| Insurance agent | Trust Builder | Comparison Closer |
| Tutoring | Service Menu | Community Hub |
| Pet grooming | Service Menu | Local Authority |
| Florist | Local Authority | Portfolio Showcase |
| Brewery / Winery | Narrative Scroll | Community Hub |

---

## Variation rules — Preventing repetition across projects

When generating multiple landings in the same niche or same pattern:

### Rule 1: Rotate the variation axis
Each pattern has 4 variation axes. When a project uses axis combination A-B, the next project in the same pattern MUST use a different combination. Track used combinations in the project output.

### Rule 2: Signature element must differ
Two projects in the same pattern must NEVER have the same signature element. If Project 1 uses a before/after slider (Portfolio Showcase), Project 2 must use a masonry gallery or video background.

### Rule 3: Section count must vary
Within the allowed range (e.g., 5–7 for Trust Builder), do not default to the maximum. If Project 1 uses 7 sections, Project 2 should use 5–6.

### Rule 4: Hero layout must rotate
Never use the same hero layout for consecutive projects. If Project 1 uses split (text-left/image-right), Project 2 must use a different hero variant.

### Rule 5: CTA language must differ
Track CTA text used across projects. "Get a Free Quote" can only be used once per batch. Next project: "Request Your Estimate", "Start Your Project", "Book a Consultation".

### Rule 6: Fallback pattern injection
Every 3rd project in the same niche, consider using the fallback pattern instead of the primary. This prevents all businesses in a niche from having identical structure.

---

## Section catalog — Building blocks

Each section below can be used across patterns. The pattern defines WHICH sections and in what ORDER. This catalog defines HOW each section can be built.

### Hero variants
| ID | Name | Layout | Best for |
|---|---|---|---|
| H1 | Split classic | Text left, image right (50/50) | Local Authority, Trust Builder |
| H2 | Split reverse | Image left, text right (50/50) | Service Menu, Trust Builder |
| H3 | Full-bleed image | Background image, overlay text + CTA | Portfolio Showcase, Narrative |
| H4 | Phone-first | Large phone number, value prop, trust badges | Emergency Response |
| H5 | Editorial | Large typography, minimal, no image | Narrative Scroll |
| H6 | Video background | Looping video, overlay text | Portfolio Showcase, Community |
| H7 | Card overlay | Content card floating over background image | Local Authority, Community |
| H8 | Asymmetric | Off-grid text placement, partial image bleed | Narrative Scroll |

### Social proof variants
| ID | Name | Format | Best for |
|---|---|---|---|
| SP1 | Review carousel | Sliding cards with stars + text | Local Authority, Service Menu |
| SP2 | Featured single | One large review with photo + context | Trust Builder, Narrative |
| SP3 | Inline quotes | Text-only quotes between sections | Emergency Response |
| SP4 | Stats bar | "200+ reviews · 4.9★ · 15 years" horizontal | Emergency Response, Comparison |
| SP5 | Switching stories | Reviews focused on "I used to use X..." | Comparison Closer |
| SP6 | Community voices | Short quotes from members about belonging | Community Hub |
| SP7 | Case studies | Detailed outcome stories with numbers | Trust Builder |

### CTA variants
| ID | Name | Format | Best for |
|---|---|---|---|
| CTA1 | Button primary | Solid color button, action text | All patterns |
| CTA2 | Phone tap | Tap-to-call phone number as primary action | Emergency Response |
| CTA3 | Inline form | Embedded form (3-4 fields max) | Trust Builder, Comparison |
| CTA4 | Floating bar | Sticky bottom bar with CTA on mobile | Emergency Response |
| CTA5 | Contextual link | Text link within content ("see our work →") | Narrative, Portfolio |
| CTA6 | Service-specific | Per-service booking buttons | Service Menu |
| CTA7 | Dual CTA | Two equal buttons (call + book) | Local Authority, Community |
| CTA8 | Delayed form | Full form section at page bottom | Narrative Scroll |

---

## Completeness rules

- If data for a section is `[NOT FOUND]`, skip the section entirely. Do NOT render an empty section or placeholder content.
- Minimum viable landing: hero + 1 content section + CTA = 3 sections. Any pattern can be reduced to this minimum if data is sparse.
- Maximum: follow the pattern's upper limit. Never exceed it. Long ≠ better.
- Every section must contain real, extracted business data. No lorem ipsum. No "Your trusted partner in excellence."
