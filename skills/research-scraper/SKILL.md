---  
name: research-scraper  
description: Scrapes a business website URL and all publicly available sources to extract every piece of real business data — name, services, location, reviews, team, trust signals, brand voice, and imagery. Outputs raw structured data with strict no-fabrication rules.  
compatibility: opencode  
metadata:  
  domain: research  
  agent: research-seo-agent  
---  
  
## What I do  
  
- Scrape the provided business URL and extract all available structured data  
- Supplement with publicly available sources (Google Business Profile, Yelp, Facebook, social media)  
- Identify and catalog every service, product, team member, testimonial, and trust signal  
- Analyze brand voice indicators from existing copy  
- Describe existing imagery for downstream image strategy  
- Flag missing data explicitly — never fill gaps with assumptions  
  
## When to use me  
  
Use this skill as the first step when building a landing page for a local US business. It is the data foundation that every other skill depends on.  
  
Invoke when you have a business URL and need to extract raw data before any strategic or design decisions.  
  
## Extraction targets  
  
### Business identity  
- Legal/display business name  
- Tagline or slogan (exact text)  
- Business description / "about" text (verbatim)  
- Logo description (visual characteristics)  
- Year founded / years in business  
  
### Services and products  
- Every service or product listed, with:  
  - Name (exact)  
  - Description (verbatim from source)  
  - Price or price range (if visible)  
  - Category or grouping  
- Service area specializations  
  
### Location and contact  
- Full street address  
- City, state, ZIP  
- Service area / radius (if stated)  
- Phone number (US format)  
- Email address  
- Contact form URL  
- Driving directions or landmarks mentioned  
  
### Operating hours  
- Hours per day of the week  
- Holiday hours or seasonal notes  
- Emergency / after-hours availability  
  
### Reviews and testimonials  
- Every review or testimonial found, with:  
  - Full text (verbatim — do not paraphrase or summarize)  
  - Reviewer name  
  - Source (Google, Yelp, Facebook, website)  
  - Star rating (if available)  
  - Date (if available)  
- Aggregate ratings per platform (e.g., "4.8 stars, 127 reviews on Google")  
  
### Team and founder  
- Owner / founder name and title  
- Team members with roles  
- Bio text (verbatim)  
- Credentials, certifications per person  
- Photos described (not URLs)  
  
### Trust signals  
- Licenses and license numbers  
- Certifications (EPA, BBB, industry-specific)  
- Insurance coverage mentions  
- Awards and recognitions  
- Professional associations / memberships  
- Guarantees or warranties offered  
- Years of experience claims  
  
### Brand voice indicators  
- Tone: formal, casual, technical, friendly, authoritative, warm  
- Vocabulary patterns: jargon level, emotional language, power words  
- Person: first person ("we"), second person ("you"), third person  
- Sample phrases that define the voice (extract 3-5 verbatim)  
  
### Digital presence  
- Social media links (all platforms found)  
- Blog presence and content type  
- Video content (YouTube, embedded)  
- External directory listings  
  
### Imagery inventory  
- Describe every significant image on the site:  
  - Subject (what it shows)  
  - Style (professional photo, stock, illustration, screenshot)  
  - Quality assessment (high-res, pixelated, outdated)  
  - Usage context (hero, service card, about section)  
  
### Competitor signals  
- Competitor names mentioned or linked  
- Differentiation claims ("unlike other...", "the only...", "best in...")  
- Pricing comparison signals  
  
## Data integrity rules  
  
1. **Extract only. Never generate.** If the website says "Best plumber in Austin" — record it. If it doesn't say it — don't write it.  
2. **Verbatim over summary.** Always prefer the exact text from the source. Summarize only if the original exceeds 500 words for a single field.  
3. **Source every data point.** Tag each extracted item with its source: `[source: website]`, `[source: google-business]`, `[source: yelp]`, etc.  
4. **Mark missing data.** Use `[NOT FOUND]` for any target field where no data was found. Never use empty strings, "N/A", or omit the field.  
5. **No inference.** If the site shows a photo of a person but doesn't name them, record `[photo of unidentified person]` — do not guess who they are.  
6. **No category invention.** If the business lists "Kitchen Remodeling" and "Bathroom Remodeling", do not combine them into "Home Remodeling" unless that exact term appears on the site.  
7. **Preserve structure.** If the website groups services into categories, preserve that grouping in your output.  
8. **US market assumption.** Format phones as (XXX) XXX-XXXX. Addresses in US format. Currency in USD. All content in English.  
  
## Output format  
  
Return all extracted data as structured Markdown sections matching the extraction targets above. Each section must include source tags. This output feeds directly into the `niche-reasoning` and `content-seo` skills.  
  
## Limitations  
  
- Cannot access password-protected pages  
- Cannot extract data from JavaScript-only rendered content that requires browser execution  
- Cannot verify the accuracy of business claims — report what is stated, not what is true  
- If the URL is inaccessible or returns no usable content, STOP and report the failure to the agent