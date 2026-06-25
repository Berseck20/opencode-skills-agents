---  
name: data-extractor  
description: Transforms the research document and landing architecture into typed, structured data files ready for Astro components — business info, services, testimonials, team, FAQ, stats, and navigation. Every data field is sourced, typed, and conditionally handled.  
compatibility: opencode  
metadata:  
  domain: builder  
  agent: landing-base-builder  
---  
  
## What I do  
  
- Parse the research document and extract every data point into structured TypeScript-ready files  
- Create one data file per domain (business, services, testimonials, team, stats, navigation, FAQ)  
- Type every field with TypeScript interfaces  
- Handle `[NOT FOUND]` fields with explicit `null` values and conditional rendering flags  
- Ensure zero data fabrication — every value traces to the research document  
- Produce files that Astro components import directly, with no runtime parsing needed  
  
## When to use me  
  
Use this skill after `landing-architecture` has produced the blueprint and before `astro-builder` starts coding components. The builder needs structured data files to populate components.  
  
Requires:  
- `research-[business-slug].md` (completed research document)  
- Landing architecture document (completed blueprint with section plan)  
  
## Data file structure  
  
All data files go in `src/data/`. Each file exports a typed constant.  
  
### `src/data/business.ts`  
  
```typescript  
export interface BusinessInfo {  
  name: string  
  slug: string  
  tagline: string | null  
  description: string | null  
  phone: string | null        // Format: (XXX) XXX-XXXX  
  email: string | null  
  address: {  
    street: string | null  
    city: string | null  
    state: string | null  
    zip: string | null  
    full: string | null        // Pre-formatted complete address  
  }  
  serviceArea: string | null  
  hours: {  
    day: string  
    hours: string  
  }[] | null  
  yearFounded: string | null  
  yearsInBusiness: string | null  
  logo: {  
    description: string | null  // Visual description for image generation  
  }  
  socialLinks: {  
    platform: string  
    url: string  
  }[] | null  
  licenses: string[] | null  
  certifications: string[] | null  
  insurance: string | null  
  guarantees: string[] | null  
  awards: string[] | null  
  associations: string[] | null  
}  
  
export const business: BusinessInfo = {  
  // Values populated from research document  
}```

src/data/services.ts

```export interface Service {  
  id: string                    // kebab-case slug  
  name: string  
  description: string | null  
  price: string | null  
  category: string | null  
  isHighlighted: boolean        // true for top 3 services by prominence in research  
}  
  
export const services: Service[] = [  
  // Ordered by prominence in research document  
]```  

src/data/testimonials.ts

```export interface Testimonial {  
  id: string  
  text: string                  // VERBATIM from research — never paraphrased  
  author: string | null  
  source: string | null         // "google", "yelp", "facebook", "website"  
  rating: number | null         // 1-5  
  date: string | null  
  isHighlighted: boolean        // true if selected by content-seo strategy  
}  
  
export interface AggregateRating {  
  platform: string  
  rating: number  
  reviewCount: number  
}  
  
export const testimonials: Testimonial[] = []  
export const aggregateRatings: AggregateRating[] = []```

src/data/team.ts

```export interface TeamMember {  
  id: string  
  name: string  
  role: string | null  
  bio: string | null            // Verbatim from research  
  credentials: string[] | null  
  imageDescription: string | null  // For image strategy  
  isOwner: boolean  
}  
  
export const team: TeamMember[] = []```

src/data/stats.ts

```export interface Stat {  
  id: string  
  value: string                 // The number/text to display ("500+", "15", "4.9★")  
  label: string                 // Short descriptor ("Homes Served", "Years Experience")  
  source: string                // Where this number comes from in the research  
}  
  
export const stats: Stat[] = [  
  // Only stats verified in research — max 4  
]```

src/data/navigation.ts

```export interface NavItem {  
  label: string  
  href: string                  // Anchor link (#services, #testimonials, etc.)  
  isVisible: boolean            // false if section is conditional and has no data  
}  
  
export interface CTAConfig {  
  primary: {  
    text: string  
    href: string                // tel: link, form anchor, or external URL  
    ariaLabel: string  
  }  
  secondary: {  
    text: string  
    href: string  
    ariaLabel: string  
  } | null  
}  
  
export const navigation: NavItem[] = []  
export const cta: CTAConfig = {  
  // From content-seo CTA strategy  
}```  

src/data/faq.ts

```export interface FAQItem {  
  id: string  
  question: string  
  answer: string  
}  
  
export const faq: FAQItem[] = [  
  // Only if FAQ section exists in architecture  
]```  

src/data/seo.ts

```export interface SEOData {  
  title: string                 // ≤60 chars  
  description: string           // ≤155 chars  
  canonical: string  
  openGraph: {  
    title: string  
    description: string  
    type: string                // "website"  
    locale: string              // "en_US"  
    siteName: string  
    image: string | null  
  }  
  schema: {  
    localBusiness: object       // Complete JSON-LD  
    services: object[] | null  
    reviews: object[] | null  
    aggregateRating: object | null  
    faq: object | null  
  }  
  keywords: {  
    primary: string  
    secondary: string[]  
    longTail: string[]  
  }  
}  
  
export const seo: SEOData = {  
  // From content-seo SEO architecture  
}```  

Extraction rules

Source mapping

Every value must be traceable:

// CORRECT — value exists in research  
name: "Austin Pro Plumbing"  // [source: research > business identity > name]  
  
// CORRECT — value not found  
tagline: null  // [source: research > business identity > tagline: NOT FOUND]  
  
// WRONG — value invented  
tagline: "Your Trusted Local Plumber"  // NOT in research document  

[NOT FOUND] handling

| Research value  | Data file value       | Component behavior                                  |
|-----------------|-----------------------|-----------------------------------------------------|
| [NOT FOUND]     | null                  | Component checks for null and conditionally renders |
| Empty string "" | null                  | Treat empty as not found                            |
| Actual value    | Exact value as string | Component renders normally                          |

Verbatim rules

These fields must be EXACT copies from the research, character for character:

    testimonials[].text — full review text

    team[].bio — biographical text

    services[].description — service description as written by the business

    business.description — about text

    business.tagline — exact tagline

Never:

    Paraphrase or "improve" the text

    Fix grammar or spelling in reviews

    Shorten descriptions to fit a component

    Add marketing language not present in research

ID generation

All id fields are generated as kebab-case slugs:

"Kitchen Remodeling" → "kitchen-remodeling"  
"Dr. Sarah Chen" → "dr-sarah-chen"  
"24/7 Emergency Service" → "24-7-emergency-service"

Ordering

    services: ordered by prominence in research (most detailed/featured first)

    testimonials: ordered by content-seo selection ranking

    team: owner first, then by order of appearance in research

    stats: ordered by visual impact (largest/most impressive number first)

    navigation: ordered by section position in landing architecture

Conditional rendering contract
The data extractor establishes a contract with the builder:

// In components — the pattern to follow:  
{testimonials.length > 0 && <TestimonialsSection testimonials={testimonials} />}  
{team.length > 0 && <TeamSection team={team} />}  
{business.hours !== null && <HoursDisplay hours={business.hours} />}  

Rule: Empty arrays [] and null values are the signals. Components must check. The data extractor never omits a file — it creates every file with either real data or empty/null values.
Validation checks

Before outputting data files, verify:
    Every value traces to a specific field in the research document
    No [NOT FOUND] text appears in any data file (converted to null)
    All testimonial text is verbatim (character-level match)
    Phone numbers are formatted as (XXX) XXX-XXXX
    All IDs are valid kebab-case with no special characters
    SEO title ≤ 60 characters
    SEO description ≤ 155 characters
    Schema JSON-LD is valid against schema.org specs
    Arrays that should be empty (no data) are [], not missing
    No field contains placeholder text ("Lorem ipsum", "TODO", "TBD")
    isHighlighted flags match content-seo selections
    Navigation isVisible reflects actual data availability

Output

All files created in src/data/:

src/data/  
├── business.ts  
├── services.ts  
├── testimonials.ts  
├── team.ts  
├── stats.ts  
├── navigation.ts  
├── faq.ts  
└── seo.ts  

Each file is self-contained, importable, and fully typed.
Rules

    Zero fabrication. Every string in every data file must exist in the research document. If you can't point to where it came from, delete it.
    Null is honest. null means "we don't have this data." An empty string "" or a placeholder means "we're pretending." Always use null.
    Testimonials are sacred. The exact text the customer wrote. Not your improved version. Not a summary. The exact text.
    Types are strict. No any. No unknown unless genuinely unknowable. Every field has a specific type.
    Files are always created. Even if there are zero testimonials, testimonials.ts exists with an empty array. The builder should never get an import error.
    IDs are deterministic. Given the same input, the same IDs are generated. No random suffixes, no counters that depend on order of processing.
    SEO data is complete. Missing meta title or description is a critical defect. These are the minimum viable SEO fields.
    Schema markup is valid. Invalid JSON-LD is worse than no JSON-LD. Validate structure before outputting.