---  
name: niche-reasoning  
description: Classifies a business into its primary niche, sub-niche, market tier, and customer profile. Determines the optimal visual personality, urgency level, and decision factors. Cross-references all classifications against the design-database skill.  
compatibility: opencode  
metadata:  
  domain: research  
  agent: research-seo-agent  
---  
  
## What I do  
  
- Classify the business into a precise niche and sub-niche  
- Determine market positioning (tier, customer type, competitive landscape)  
- Identify the psychological drivers behind the target customer's buying decision  
- Assign a visual personality profile backed by niche logic  
- Cross-reference every classification against the design-database to pull matched palette, style, typography, landing pattern, and UX considerations  
- Produce a complete niche profile that downstream skills use as their decision framework  
  
## When to use me  
  
Use this skill after `research-scraper` has produced raw business data. This skill interprets that data and makes strategic classifications that drive every design and content decision downstream.  
  
Never run this skill without completed research data.  
  
## Classification framework  
  
### Primary niche  
Identify the single broadest industry category:  
- Examples: plumbing, dental, landscaping, legal, HVAC, roofing, cleaning, auto repair, real estate, restaurant, salon, fitness, accounting, veterinary, pest control, electrical, photography, tutoring, moving, storage  
  
### Sub-niche  
Identify the specialization within the primary niche:  
- Examples: emergency plumbing, cosmetic dentistry, commercial landscaping, personal injury law, residential HVAC installation  
- If no clear specialization exists, use `general-[niche]` (e.g., `general-plumbing`)  
  
### Market tier  
Classify based on pricing signals, brand positioning, and service descriptions:  

| Tier      | Signals                                                                        |
|-----------|--------------------------------------------------------------------------------|
| Budget    | Price emphasis, discounts, "affordable", "cheap", coupon codes                 |
| Mid-range | Value emphasis, "quality service", balanced price/quality messaging            |
| Premium   | Quality emphasis, "expert", "specialized", higher price points, certifications |
| Luxury    | Exclusivity, "bespoke", "concierge", prestige language, no prices listed       |

Customer type

| Type              | Signals                                                               |
|-------------------|-----------------------------------------------------------------------|
| Residential (B2C) | Home addresses, family language, "your home", neighborhood references |
| Commercial (B2B)  | Business clients, "commercial", "enterprise", "property management"   |
| Mixed             | Both residential and commercial services listed                       |

Urgency level

| Level         | Niches                                                                          | Conversion implication                                       |
|---------------|---------------------------------------------------------------------------------|--------------------------------------------------------------|
| Emergency     | Plumbing, locksmith, towing, water damage, pest (certain), HVAC (summer/winter) | CTA = call now, phone prominent, speed claims, 24/7 emphasis |
| Planned       | Landscaping, remodeling, dental (general), accounting, photography              | CTA = schedule/quote, trust emphasis, portfolio/gallery      |
| Discretionary | Salon, spa, fitness, tutoring, photography (personal)                           | CTA = book/explore, emotional appeal, experience emphasis    |

Decision factors
Rank the top 3 factors driving the customer's choice (order matters):

| Factor      | Typical niches                                                 |
|-------------|----------------------------------------------------------------|
| Price       | Budget tier, commoditized services (cleaning, moving, storage) |
| Trust       | Medical, legal, financial, childcare, home services            |
| Quality     | Premium/luxury tier, specialized trades, cosmetic services     |
| Convenience | Emergency services, on-demand, mobile services                 |
| Speed       | Emergency, time-sensitive services                             |
| Experience  | Restaurants, salons, fitness, entertainment                    |

Competitive landscape

| Level       | Signals                                                                    |
|-------------|----------------------------------------------------------------------------|
| Saturated   | Many competitors in the area, generic service offerings, price competition |
| Moderate    | Some competitors, room for differentiation, mix of quality levels          |
| Underserved | Few competitors, specialized service, geographic monopoly signals          |

Visual profile assignment

Assign ONE primary profile based on niche characteristics:

Precision

    Niches: medical, dental, legal, financial, accounting, insurance, tech, consulting

    Traits: clean lines, structured layouts, muted colors, serif or thin sans-serif fonts, minimal decoration

    Border radius: 4-8px

    Shadows: subtle, low opacity

    Animations: minimal, functional only

Warmth

    Niches: family services, childcare, pet care, home services, cleaning, senior care, tutoring, bakery

    Traits: rounded shapes, warm colors, friendly typography, soft shadows, approachable imagery

    Border radius: 12-20px

    Shadows: medium, warm tones

    Animations: gentle, easing-based

Authority

    Niches: construction, roofing, industrial, B2B, manufacturing, engineering, heavy equipment

    Traits: bold typography, strong contrast, geometric layouts, dark backgrounds, uppercase accents

    Border radius: 0-6px

    Shadows: strong, dramatic

    Animations: sharp, confident

Energy

    Niches: fitness, entertainment, food/restaurant, nightlife, sports, events, music

    Traits: vibrant colors, dynamic layouts, large imagery, bold CTAs, movement-oriented design

    Border radius: 8-16px

    Shadows: colored, layered

    Animations: energetic, attention-grabbing

Override rule

If the research data reveals a business that doesn't fit the typical profile for its niche (e.g., a luxury pet spa that should be Precision, not Warmth), justify the override with specific evidence from the extracted data.
Design database cross-reference

After classification, query the design-database skill and load:

    industry-reasoning.md — Validate your niche classification against documented industry patterns. If there's a conflict, the database wins unless research data provides strong counter-evidence.

    palettes.md — Pull the recommended color palette for the classified niche. Record the exact palette values.

    styles.md — Identify the matching design style. Record style name, characteristics, and keywords.

    typography.md — Select the font pairing for the niche. Record font names, Google Fonts URLs, and mood.

    landing-patterns.md — Determine the landing page pattern. Record section order, CTA placement strategy, and conversion tips.

    ux-guidelines.md — Flag all UX considerations relevant to the niche and platform. Record best practices and anti-patterns.

Database values override profile defaults. If the database says dental uses palette X but the Precision profile would suggest palette Y, use palette X.
Output format

Return all classifications as structured Markdown sections:

## Niche Classification  
- Primary niche: [value]  
- Sub-niche: [value]  
- Market tier: [value]  
- Customer type: [value]  
- Urgency level: [value]  
- Decision factors: [ranked list]  
- Competitive landscape: [value]  
  
## Visual Profile  
- Assigned profile: [name]  
- Justification: [why this profile fits, citing specific research data]  
- Override applied: [yes/no — if yes, explain]  
  
## Design Database Matches  
### Color Palette  
[exact values from palettes.md]  
  
### Design Style  
[name + characteristics from styles.md]  
  
### Typography Pairing  
[fonts + URLs from typography.md]  
  
### Landing Page Pattern  
[section order + CTA strategy from landing-patterns.md]  
  
### UX Considerations  
[relevant guidelines from ux-guidelines.md]  

Rules

Classify from data, not assumptions. Every classification must cite specific evidence from the research-scraper output.

One primary profile only. Do not blend profiles. Pick one and justify it.

Database overrides profiles. Always. No exceptions.

If the niche is ambiguous, go specific. "Home services" is too broad — determine if it's cleaning, handyman, remodeling, etc.

Market tier is not about the business's actual quality. It's about how they position themselves. A mediocre plumber who writes "premium service" on their site is positioning as premium.

Do not skip the cross-reference. Every classification must be validated against the design-database. Missing this step creates downstream inconsistencies.

Log uncertainty. If a classification is borderline (e.g., could be mid-range or premium), state both options and explain which you chose and why.