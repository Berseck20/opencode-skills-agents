---  
name: image-strategy  
description: Analyzes the built landing page and produces a complete image specification document — shot list, technical specs, art direction per visual profile, and placeholder optimization. Ensures every image slot has a defined purpose, style, and production-ready specification.  
compatibility: opencode  
metadata:  
  domain: rebuild  
  agent: rebuild-landing  
---  
  
## What I do  
  
- Audit every image slot in the built landing page  
- Generate a complete shot list with art direction per visual profile  
- Define technical specs (dimensions, aspect ratio, format, compression) for each image  
- Produce client-ready image descriptions in non-technical language  
- Optimize placeholder strategy for pre-image loading states  
- Ensure image specifications align with the visual profile and niche reasoning  
  
## When to use me  
  
Use this skill as the first step in the `rebuild-landing` agent workflow. Before enhancing visual quality, you need to know exactly what images the page needs and how they should look.  
  
Requires:  
- A built Astro project (output of `landing-base-builder`)  
- `research-[business-slug].md`  
- The landing architecture document  
- Active visual profile assignment from `niche-reasoning`  
  
## Image audit process  
  
### Step 1 — Inventory scan  
  
Scan every file in `src/components/` and `src/pages/` for:  
- `<img>` tags and their containers  
- Elements with `role="img"`  
- Background image containers  
- SVG illustrations  
- Icon usage (inline SVGs vs decorative)  
  
Output: numbered list of every image slot with its location, current state, and container dimensions.  
  
### Step 2 — Classification  
  
Classify each image slot:  

| Type              | Definition                      | Examples                                     |
|-------------------|---------------------------------|----------------------------------------------|
| Hero              | Primary visual, above fold      | Hero background, hero product shot           |
| Service           | Illustrates a specific service  | Service card image, service detail           |
| Social proof      | Supports credibility            | Team photo, certification badge, award       |
| Atmosphere        | Sets mood/context               | Office interior, workspace, neighborhood     |
| Functional        | UI element with image treatment | Map placeholder, form decoration             |
| Icon/Illustration | Small graphic element           | Service icons, feature icons, decorative SVG |

Step 3 — Art direction per profile

Each image receives art direction based on the active visual profile:
Precision profile

    Color grading: desaturated, cool tones, clinical whites

    Composition: centered, symmetrical, clean backgrounds

    Subjects: professional settings, clean workspaces, equipment close-ups

    Avoid: warm filters, candid shots, busy backgrounds, stock clichés

    Format preference: sharp edges, no vignettes, minimal post-processing

Warmth profile

    Color grading: warm tones, golden hour feel, soft contrast

    Composition: off-center, natural framing, depth of field

    Subjects: people interacting, hands at work, cozy environments

    Avoid: clinical lighting, sterile backgrounds, corporate poses

    Format preference: soft edges acceptable, gentle color grading

Authority profile

    Color grading: high contrast, dramatic lighting, deep shadows

    Composition: low angle when possible, strong geometric framing

    Subjects: finished work, heavy equipment, team in action, raw materials

    Avoid: soft focus, pastel tones, delicate compositions

    Format preference: sharp, punchy, bold processing

Energy profile

    Color grading: saturated, vibrant, high energy

    Composition: dynamic angles, motion blur acceptable, tight crops

    Subjects: action shots, vibrant food, crowd energy, movement

    Avoid: static poses, muted colors, empty spaces

    Format preference: vivid processing, can push saturation

Shot list format

For each image slot, produce:

### Image [number]: [Descriptive name]  
  
- **Location:** `src/components/sections/[Component].astro` line [X]  
- **Type:** [Hero | Service | Social proof | Atmosphere | Functional]  
- **Container:** [width]x[height] | aspect-[ratio]  
- **Loading:** [eager | lazy]  
  
#### Art direction  
- **Subject:** [What the image shows — specific, not generic]  
- **Mood:** [Emotional tone this image conveys]  
- **Composition:** [Framing, angle, focus point]  
- **Color treatment:** [Grading, saturation, temperature]  
- **Must include:** [Required elements]  
- **Must avoid:** [Forbidden elements]  
  
#### Technical specs  
- **Dimensions:** [width]x[height]px (1x) / [width]x[height]px (2x)  
- **Format:** WebP with JPEG fallback  
- **Max file size:** [X]KB  
- **Alt text:** "[Descriptive alt text for accessibility]"  
  
#### Client brief (non-technical)  
"[Plain language description for the business owner: what to photograph,   
where, how, and any props or preparation needed]"  

Technical specifications

Dimension rules

| Container type     | 1x dimensions | 2x dimensions | Max file size |
|--------------------|---------------|---------------|---------------|
| Hero full-width    | 1440×[h]      | 2880×[h]      | 200KB         |
| Hero contained     | 1200×[h]      | 2400×[h]      | 150KB         |
| Card image         | 400×[h]       | 800×[h]       | 80KB          |
| Thumbnail          | 200×[h]       | 400×[h]       | 40KB          |
| Team portrait      | 300×300       | 600×600       | 60KB          |
| Background texture | 1440×[h]      | Not needed    | 100KB         |

Format strategy

Primary: WebP (lossy, quality 80-85)  
Fallback: JPEG (quality 82-85)  
Icons/Illustrations: SVG (inline, optimized with SVGO)  

Responsive images

Every <img> must use srcset and sizes:

<img  
  src="image-400.webp"  
  srcset="image-400.webp 400w, image-800.webp 800w, image-1200.webp 1200w"  
  sizes="(max-width: 640px) 100vw, (max-width: 1024px) 50vw, 33vw"  
  width="400"  
  height="300"  
  alt="[descriptive alt text]"  
  loading="lazy"  
/>  

Placeholder optimization

Replace the basic gradient placeholders from the initial build with profile-appropriate placeholders:

Precision

/* Subtle neutral gradient */  
background: linear-gradient(135deg, #f8fafc 0%, #e2e8f0 100%);  

Warmth

/* Warm soft gradient */  
background: linear-gradient(135deg, #fef7ed 0%, #fed7aa 100%);  

Authority

/* Dark dramatic gradient */  
background: linear-gradient(135deg, #1e293b 0%, #0f172a 100%);  

Energy

/* Vibrant gradient using primary colors */  
background: linear-gradient(135deg, var(--color-primary) 0%, var(--color-accent) 100%);  

Validation checks

    Every image slot in the built page appears in the shot list
    Every image has explicit dimensions (no unsized containers)
    Alt text is descriptive, not decorative (alt="" only for truly decorative images)
    Hero images use loading="eager", everything else uses loading="lazy"
    File size targets are realistic for the specified dimensions
    Art direction matches the active visual profile
    Client brief uses non-technical language a business owner can understand
    No stock photo clichés in any specification (handshake, pointing at laptop, etc.)
    Responsive srcset strategy covers mobile, tablet, and desktop
    SVG icons are specified as inline, not <img> tags

Output
Write the complete document to image-strategy-[business-slug].md in the project root.

Rules
    Every image slot gets a specification. If the page has 12 image containers, the document has 12 entries. No "remaining follow same pattern."

    Art direction is profile-specific. A dental clinic (Precision) and a bakery (Warmth) cannot have the same image style. The profile dictates everything.

    Client briefs are human. The business owner reads this to know what to photograph. No CSS terms, no technical jargon, no "ensure proper aspect ratio."

    No stock photo language. "Diverse team collaborating in modern office" is banned. Specify real, specific scenes based on the actual business.

    File sizes are budgets. The spec says max 80KB for a card image. If the final image is 200KB, it fails the spec.

    Alt text is for blind users. "Image" and "photo" are not alt text. Describe what the image shows in a way that conveys the same information a sighted user gets.