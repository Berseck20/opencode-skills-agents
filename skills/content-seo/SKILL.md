---  
name: content-seo  
description: Transforms raw business research and niche classification into a complete SEO-optimized content strategy — message hierarchy, conversion framework, CTA strategy, objection engineering, social proof selection, tone calibration, and full SEO architecture with local signals and schema markup.  
compatibility: opencode  
metadata:  
  domain: research  
  agent: research-seo-agent  
---  
  
## What I do  
  
- Define the message hierarchy (H1, H2s, supporting copy) ordered by conversion impact  
- Select and justify a conversion framework (PAS, AIDA, BAB, or hybrid)  
- Build complete SEO architecture with local signals, meta tags, and schema markup  
- Engineer objection-counter pairs mapped to specific page sections  
- Design a multi-level CTA strategy (primary, secondary, micro) calibrated to niche urgency  
- Curate social proof by selecting the highest-impact testimonials and trust signals  
- Calibrate tone and voice with specific word usage rules for the niche  
  
## When to use me  
  
Use this skill after `research-scraper` and `niche-reasoning` have completed. This skill takes raw data + niche classification and produces the content layer that the builder agent will implement.  
  
Never run without both research data and niche classification available.  
  
## Message hierarchy  
  
Define the complete copy structure for the landing page:  
  
### H1 (Hero headline)  
- Single, clear value proposition  
- Must contain the primary keyword naturally  
- Must reference the specific service + location when applicable  
- Maximum 10 words — every word must earn its place  
- Must NOT be generic ("Welcome to [Business]", "Your Trusted Partner")  
- Must answer: "Why should I choose this business in 3 seconds?"  
  
### H2s (Section headlines)  
- One per major section, ordered by conversion impact  
- Each must advance the visitor toward the CTA  
- Progressive disclosure: awareness → interest → trust → action  
- Must use language from the actual business, not marketing clichés  
  
### Supporting copy  
- Short paragraphs (2-3 sentences max per block)  
- Written in the voice calibrated in the tone section  
- Every paragraph has a job: inform, reassure, or push toward action  
- No filler sentences that could be deleted without losing meaning  
  
## Conversion framework selection  
  
Choose ONE primary framework based on niche + urgency level:  

| Framework                               | Best for                                      | Structure                                                                                        |
|-----------------------------------------|-----------------------------------------------|--------------------------------------------------------------------------------------------------|
| PAS (Problem-Agitate-Solve)             | Emergency/urgent services, pain-driven niches | Hero states problem → Section agitates consequences → Services present solution                  |
| AIDA (Attention-Interest-Desire-Action) | Planned services, considered purchases        | Hero grabs attention → Features build interest → Social proof creates desire → CTA drives action |
| BAB (Before-After-Bridge)               | Transformation services, premium positioning  | Hero shows current state → Sections paint desired outcome → Business is the bridge               |
| Hybrid                                  | Complex niches, mixed urgency                 | Combine elements — must specify which parts come from which framework and why                    |

Justification is mandatory. State: "Selected [framework] because [niche] customers at [urgency level] urgency are primarily motivated by [decision factors], making [framework structure] the optimal persuasion path."
SEO architecture
Keywords

    Primary keyword: 1 phrase, 2-4 words, includes service + location (e.g., "emergency plumber Austin")

    Secondary keywords: 3-5 phrases covering:

        Service variations ("24 hour plumbing repair")

        Location variations ("plumber near downtown Austin")

        Intent variations ("fix burst pipe", "water heater installation")

    Long-tail keywords: 2-3 phrases for FAQ or content sections

    All keywords must be naturally placeable — no keyword stuffing

Meta tags

    Title: ≤60 characters, format: [Primary Service] in [City] | [Business Name]

    Description: ≤155 characters, includes primary keyword, value proposition, and CTA hint

    Open Graph: title, description, type (website), locale (en_US)

Local SEO signals

    City and neighborhood mentions in copy (natural placement, not forced)

    "Near me" variant targeting in FAQ or service descriptions

    Service area definition in structured data

    NAP consistency (Name, Address, Phone) across all page mentions

Schema markup

| Recommend specific schema types with required properties: | Best for                   | Structure                                               |
|-----------------------------------------------------------|----------------------------|---------------------------------------------------------|
| Schema type                                               | When to use                | Required properties                                     |
| LocalBusiness (or subtype)                                | Always                     | name, address, telephone, openingHours, geo, url, image |
| Service                                                   | Per service listed         | name, description, provider, areaServed                 |
| Review                                                    | If testimonials exist      | reviewBody, author, reviewRating                        |
| AggregateRating                                           | If aggregate ratings found | ratingValue, reviewCount, bestRating                    |
| FAQPage                                                   | If FAQ section planned     | mainEntity with Question + acceptedAnswer pairs         |

## CTA strategy  
  
### CTA levels  
Each landing page uses 3 levels: **primary**, **secondary**, and **micro**. Text rules remain the same — action verb + specific outcome, urgency-calibrated, no generic phrases.  
  
### CTA format diversification (CRITICAL)  
Every CTA instance on the page MUST use a **different visual format**. Two CTAs with the same format = homogeneity failure.  
  
Available formats:  


| Format         | HTML pattern                                                 | Best for                             | Visual weight |
|----------------|--------------------------------------------------------------|--------------------------------------|---------------|
| button         | Standard <button> or <a> styled as button                    | Hero primary CTA, final CTA section  | Highest       |
| sticky-bar     | Fixed bar at bottom of viewport, appears on scroll past hero | Mobile conversion, emergency niches  | High          |
| inline-link    | Underlined text link within a paragraph, arrow icon          | Mid-content secondary CTAs           | Low           |
| floating-badge | Fixed circular or pill element at bottom-right corner        | Phone/WhatsApp tap, emergency niches | Medium        |
| form-embedded  | Inline form (name + phone/email + submit) within a section   | Lead gen niches, planned services    | High          |
| phone-tap      | Large phone number styled as tappable link, tel: href        | Emergency/urgent, mobile-first       | Medium        |
| text-banner    | Full-width colored band with text + action, between sections | Urgency reinforcement, mid-scroll    | Medium        |

CTA assignment rules

    Primary CTA — appears in hero + dedicated CTA section. Each instance uses a DIFFERENT format (e.g., hero = button, CTA section = form-embedded)

    Secondary CTA — alternative conversion path. Must use a format NOT used by primary (e.g., inline-link or text-banner)

    Micro-CTAs — one per content section, contextual. Use remaining formats. After testimonials → inline-link. After services → phone-tap. Sticky-bar appears after scrolling past hero.

    Minimum 3 distinct formats per page. Maximum = number of CTA instances (no repeats unless page has 8+ CTAs)

    Emergency niches MUST include at least one phone-tap and one sticky-bar

    Planned niches MUST include at least one form-embedded

CTA assignment output format

For each CTA instance, specify:

CTA-[number]:  
  Level: primary | secondary | micro  
  Text: "[exact CTA text]"  
  Format: [format from table above]  
  Placement: [section name]  
  Urgency: [emergency | planned | discretionary]  
  Notes: [why this format for this placement]

Words to NEVER use in CTAs

    "Submit" (feels like bureaucracy)

    "Click here" (meaningless)

    "Learn more" without context (lazy)

    "Get started" without specificity (vague)

Objection engineering

Identify the top 3-5 objections a potential customer has for this specific niche and tier:

| Common objection patterns by niche type                                                                   |
|-----------------------------------------------------------------------------------------------------------|
| Price-sensitive niches: "Is this worth the cost?", "Are there hidden fees?", "Can I find cheaper?"        |
| Trust-sensitive niches: "Are they qualified?", "What if something goes wrong?", "Are they insured?"       |
| Quality-sensitive niches: "Will the results last?", "Do they use good materials?", "Can I see past work?" |
| Convenience niches: "How fast can they come?", "Do I need to be home?", "What's the process?"             |

For each objection:

    Objection: The exact doubt in the customer's mind

    Counter: The answer, using real business data (certifications, guarantees, reviews, years of experience)

    Evidence type: testimonial, stat, certification, guarantee, process explanation

    Placement: Which section neutralizes this objection most naturally

    Copy approach: Direct address ("Worried about X? Here's why...") vs. indirect proof (testimonial that addresses it)

Rule: Every counter must use real data from the research. If no evidence exists to counter an objection, log it as a gap — do not fabricate reassurance.
Social proof strategy
Testimonial selection

If reviews were found, select the top 3-5 based on:

    Specificity — Reviews mentioning specific services, outcomes, or experiences beat generic "great service" reviews

    Objection neutralization — Reviews that answer common objections rank higher

    Emotional impact — Reviews with a story (before/after, problem/resolution) beat flat praise

    Recency — Tiebreaker only, not primary selection factor

Trust signals to highlight

Rank by impact for the specific niche:

    Years in business (if significant: 10+)

    Number of completed projects/customers served

    Aggregate rating + review count

    Certifications and licenses (especially niche-specific ones)

    Insurance and bonding

    Guarantees and warranties

    Professional association memberships

    Awards and recognitions

Stats to display

Select 3-4 numbers that create the strongest impression:

    Format: large number + short label (e.g., "500+ Homes Served", "15 Years Experience", "4.9★ Google Rating")

    Must be real numbers from research — never rounded up or exaggerated

    If insufficient stats exist, use fewer. Two real stats beat four invented ones.

Tone and voice calibration
Scales (1-5)

| Dimension | 1                         | 5                          | Determined by                         |
|-----------|---------------------------|----------------------------|---------------------------------------|
| Formality | Casual, conversational    | Corporate, professional    | Market tier + niche                   |
| Technical | No jargon, plain language | Industry terminology       | Customer type (B2B higher, B2C lower) |
| Emotional | Rational, fact-based      | Feeling-driven, empathetic | Urgency level + decision factors      |

Word lists

    Words to USE: 10-15 words that match the calibrated tone and appear in the business's own copy (extracted from research)

    Words to AVOID: 10-15 words that are wrong for this niche/tier (e.g., premium dental should avoid "cheap", "deal", "discount")

Voice rules

    Person: Specify "we/our" vs "they/their" vs "[Business Name]" — be consistent

    Sentence length: Short (emergency/energy) vs. medium (planned/warmth) vs. varied (premium/precision)

    Proof style: Data-forward (authority/precision) vs. story-forward (warmth/energy)

Output format

Return the complete content strategy as structured Markdown:

## Message Hierarchy  
### H1  
### H2s (ordered)  
### Key supporting copy points  
  
## Conversion Framework  
- Selected: [framework]  
- Justification: [reasoning]  
- Section flow: [how framework maps to page sections]  
  
## SEO Architecture  
### Keywords (primary, secondary, long-tail)  
### Meta Tags (title, description, OG)  
### Local SEO Signals  
### Schema Markup Recommendations  
  
## CTA Strategy  
### Primary CTA  
- Text: [copy]  
- Format: [format from catalog]  
- Placement: [section]  
### Secondary CTA  
- Text: [copy]  
- Format: [format from catalog]  
- Placement: [section]  
### Micro-CTAs (per section)  
- [Section]: [copy] — Format: [format from catalog]  
  
## Objection Map  
| Objection | Counter | Evidence | Placement | Approach |  
  
## Social Proof Strategy  
### Selected Testimonials (ranked, with selection reasoning)  
### Trust Signals (ranked)  
### Stats to Display  
  
## Tone & Voice Calibration  
### Scale Values  
### Words to Use  
### Words to Avoid  
### Voice Rules  

Rules

Every content decision must trace to research data. If you can't cite the source, you're inventing.

No generic marketing copy. "Quality service you can trust" is banned. Use the business's own language.

SEO must be natural. If a keyword doesn't fit naturally in a sentence, don't force it. Search engines and humans both penalize awkward phrasing.

CTAs must match urgency. A "Book a Relaxing Session" CTA on an emergency plumbing page is a conversion killer.

Objections without evidence stay as gaps. Never write "We guarantee satisfaction" if the business doesn't actually offer a guarantee.

Testimonials are verbatim or not at all. Do not rewrite, trim, or "improve" customer reviews.

Tone calibration is binding. The builder agent will use these scales and word lists. If you set formality to 2 and the page reads like a legal document, something went wrong.

Local SEO is not optional. Every local business landing page must target geographic terms. If the city isn't in the H1 or H2s, there's a problem.

Anti-pattern: keyword-stuffed meta description. The meta description is for humans first. One natural keyword inclusion is enough.

Anti-pattern: objection map without placement. Every objection must have a specific section where it gets addressed. Floating objections don't convert.
**Anti-pattern: CTA monotony.** If all CTAs on the page are styled buttons with similar text, the page feels templated. Vary format AND copy. "Get a Free Quote" as a button and "Get Your Free Estimate" as another button is NOT variation.  
**Anti-pattern: CTA overload.** More than 3 CTA instances makes the page feel desperate. If you need to persuade that hard, the content above the CTA has failed.