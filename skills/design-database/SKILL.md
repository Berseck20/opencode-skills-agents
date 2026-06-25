---  
name: design-database  
description: Searchable design intelligence database containing UI styles, color palettes by industry, typography pairings, landing page patterns, UX guidelines, and niche-based reasoning. Use this skill to look up design decisions based on business niche, visual profile, or specific design domain.  
compatibility: opencode  
metadata:  
  domain: design  
  scope: shared  
---  
  
## What I do  
  
- Provide industry-specific design reasoning for niche classification  
- Return color palettes matched to business type and market tier  
- Recommend typography pairings by industry and visual personality  
- Define landing page section patterns optimized for conversion by niche  
- Supply UX guidelines with anti-patterns, best practices, and severity levels  
- Catalog 20 design styles with characteristics, keywords, and use cases  
  
## When to use me  
  
Use this skill when you need to make any design decision for a landing page project. This includes:  
  
- Classifying a business niche and determining its visual strategy  
- Selecting a color palette for a specific industry  
- Choosing font pairings that match a brand personality  
- Deciding section order and layout patterns for a landing page  
- Validating UX decisions against known best practices  
- Auditing existing designs for compliance with industry standards  
  
Always query this skill BEFORE making visual decisions. Do not rely on defaults or assumptions.  
  
## Available files  
  
This skill contains 6 reference files. Load the one you need based on your task:  

| File                  | Domain         | Use when you need                                                  |
|-----------------------|----------------|--------------------------------------------------------------------|
| industry-reasoning.md | Niche analysis | Classifying a business and determining its conversion strategy     |
| styles.md             | Visual style   | Selecting a design style (minimal, brutalist, glassmorphism, etc.) |
| palettes.md           | Color          | Choosing colors matched to industry and market tier                |
| typography.md         | Typography     | Selecting font pairings with Google Fonts URLs                     |
| landing-patterns.md   | Page structure | Determining section order, CTA placement, and conversion flow      |
| ux-guidelines.md      | UX             | Validating interactions, accessibility, and responsive behavior    |

    Identify what design domain you need (color, typography, layout, etc.)

    Load the corresponding file from this skill's directory

    Filter by the business niche, visual profile, or specific keyword

    Apply the result — design database values override any default or profile-based assumptions

Rules

    Database values override defaults. If the database specifies a palette for "dental", use it — do not fall back to a generic "Precision" profile palette.

    Cross-reference when possible. A complete design decision combines palette + typography + style + landing pattern for the same niche.

    Do not modify these files. They are read-only reference data.

    If no exact match exists, use the closest category and log the gap in your output.