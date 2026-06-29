# Palettes — design-database

> Color palette catalog for local US business landing pages.
> Each palette defines semantic color roles with exact hex values, contrast-validated.
> The agent MUST select based on niche classification from `niche-reasoning` + `visual-system` profile.

---

## How to use this file

1. `niche-reasoning` classifies the business into an **industry**.
2. `visual-system` assigns a **visual profile** (Clean Minimal, Dark Cinematic, Brutalist, etc.).
3. This file provides the **exact color tokens** for that combination.
4. The agent picks the palette row that matches the industry. If no exact match exists, pick the closest parent category.
5. Every color has a **semantic role** — use the role, not the position. `primary` is brand identity. `accent` is CTA/action. `destructive` is error/urgency.
6. Do NOT invent colors. Do NOT blend palettes. Pick one row and commit.

---

## Semantic color roles

| Role | Purpose | Usage |
|------|---------|-------|
| `primary` | Brand identity color | Headers, nav, key brand elements |
| `on-primary` | Text/icons ON primary | Must pass WCAG AA against primary |
| `secondary` | Supporting brand color | Secondary buttons, tags, badges |
| `on-secondary` | Text/icons ON secondary | Must pass WCAG AA against secondary |
| `accent` | Action/CTA color | Primary CTA buttons, links, highlights |
| `on-accent` | Text/icons ON accent | Must pass WCAG AA against accent |
| `background` | Page background | Main page bg |
| `foreground` | Primary text | Body text on background |
| `card` | Card/surface bg | Cards, modals, elevated surfaces |
| `card-foreground` | Text on cards | Body text inside cards |
| `muted` | Subtle bg | Section alternation, input fields |
| `muted-foreground` | De-emphasized text | Captions, placeholders, meta |
| `border` | Borders/dividers | Card borders, section dividers |
| `destructive` | Error/danger | Error states, delete actions |
| `on-destructive` | Text on destructive | Must pass WCAG AA against destructive |
| `ring` | Focus ring | Focus indicators for a11y |

---

## Contrast rules

- `on-primary` vs `primary` → minimum 4.5:1 (WCAG AA)
- `on-accent` vs `accent` → minimum 3:1 (WCAG AA large text) — CTA buttons use large/bold text
- `foreground` vs `background` → minimum 7:1 (WCAG AAA preferred)
- `card-foreground` vs `card` → minimum 4.5:1
- `muted-foreground` vs `muted` → minimum 4.5:1
- If a palette violates these ratios, the agent MUST flag it and adjust the `on-*` color, never the base color.

---

## Light background palettes

### Landscaping / Lawn Care
| Role | Value | Notes |
|------|-------|-------|
| primary | `#15803D` | Earth green — nature, growth |
| on-primary | `#FFFFFF` | |
| secondary | `#22C55E` | Lighter green for tags/badges |
| on-secondary | `#0F172A` | |
| accent | `#EA580C` | Urgency orange — "Get Quote" CTA |
| on-accent | `#FFFFFF` | |
| background | `#F0FDF4` | Subtle green-tinted white |
| foreground | `#14532D` | Dark green text |
| card | `#FFFFFF` | |
| card-foreground | `#14532D` | |
| muted | `#E8F0F1` | |
| muted-foreground | `#64748B` | |
| border | `#BBF7D0` | |
| destructive | `#DC2626` | |
| on-destructive | `#FFFFFF` | |
| ring | `#15803D` | |

### Plumbing / Electrician / Home Services
| Role | Value | Notes |
|------|-------|-------|
| primary | `#1E40AF` | Professional blue — trust, reliability |
| on-primary | `#FFFFFF` | |
| secondary | `#3B82F6` | |
| on-secondary | `#FFFFFF` | |
| accent | `#EA580C` | Urgent orange — "Call Now" CTA |
| on-accent | `#FFFFFF` | |
| background | `#EFF6FF` | Blue-tinted white |
| foreground | `#1E3A8A` | |
| card | `#FFFFFF` | |
| card-foreground | `#1E3A8A` | |
| muted | `#E9EEF6` | |
| muted-foreground | `#64748B` | |
| border | `#BFDBFE` | |
| destructive | `#DC2626` | |
| on-destructive | `#FFFFFF` | |
| ring | `#1E40AF` | |

### Restaurant / Café / Food Service
| Role | Value | Notes |
|------|-------|-------|
| primary | `#DC2626` | Appetizing red |
| on-primary | `#FFFFFF` | |
| secondary | `#F87171` | Soft red |
| on-secondary | `#0F172A` | |
| accent | `#A16207` | Warm gold — "Reserve" CTA |
| on-accent | `#FFFFFF` | |
| background | `#FEF2F2` | Warm-tinted white |
| foreground | `#450A0A` | |
| card | `#FFFFFF` | |
| card-foreground | `#450A0A` | |
| muted | `#F0EDF1` | |
| muted-foreground | `#64748B` | |
| border | `#FECACA` | |
| destructive | `#DC2626` | |
| on-destructive | `#FFFFFF` | |
| ring | `#DC2626` | |

### Bakery / Café (Warm variant)
| Role | Value | Notes |
|------|-------|-------|
| primary | `#92400E` | Warm brown — artisanal, cozy |
| on-primary | `#FFFFFF` | |
| secondary | `#B45309` | |
| on-secondary | `#FFFFFF` | |
| accent | `#92400E` | Earth tone CTA |
| on-accent | `#FFFFFF` | |
| background | `#FEF3C7` | Cream/parchment |
| foreground | `#78350F` | |
| card | `#FFFFFF` | |
| card-foreground | `#78350F` | |
| muted | `#EDEEF0` | |
| muted-foreground | `#64748B` | |
| border | `#FDE68A` | |
| destructive | `#DC2626` | |
| on-destructive | `#FFFFFF` | |
| ring | `#92400E` | |

### Brewery / Winery
| Role | Value | Notes |
|------|-------|-------|
| primary | `#7C2D12` | Deep burgundy — craft, premium |
| on-primary | `#FFFFFF` | |
| secondary | `#B91C1C` | Wine red |
| on-secondary | `#FFFFFF` | |
| accent | `#A16207` | Craft gold |
| on-accent | `#FFFFFF` | |
| background | `#FEF2F2` | Warm white |
| foreground | `#450A0A` | |
| card | `#FFFFFF` | |
| card-foreground | `#450A0A` | |
| muted | `#ECEDF0` | |
| muted-foreground | `#64748B` | |
| border | `#FECACA` | |
| destructive | `#DC2626` | |
| on-destructive | `#FFFFFF` | |
| ring | `#7C2D12` | |

### Real Estate / Property
| Role | Value | Notes |
|------|-------|-------|
| primary | `#0F766E` | Trust teal |
| on-primary | `#FFFFFF` | |
| secondary | `#14B8A6` | |
| on-secondary | `#0F172A` | |
| accent | `#0369A1` | Professional blue CTA |
| on-accent | `#FFFFFF` | |
| background | `#F0FDFA` | |
| foreground | `#134E4A` | |
| card | `#FFFFFF` | |
| card-foreground | `#134E4A` | |
| muted | `#E8F0F3` | |
| muted-foreground | `#64748B` | |
| border | `#99F6E4` | |
| destructive | `#DC2626` | |
| on-destructive | `#FFFFFF` | |
| ring | `#0F766E` | |

### Legal Services
| Role | Value | Notes |
|------|-------|-------|
| primary | `#1E3A8A` | Authority navy |
| on-primary | `#FFFFFF` | |
| secondary | `#1E40AF` | |
| on-secondary | `#FFFFFF` | |
| accent | `#B45309` | Trust gold |
| on-accent | `#FFFFFF` | |
| background | `#F8FAFC` | Clean neutral |
| foreground | `#0F172A` | |
| card | `#FFFFFF` | |
| card-foreground | `#0F172A` | |
| muted | `#E9EEF5` | |
| muted-foreground | `#64748B` | |
| border | `#CBD5E1` | |
| destructive | `#DC2626` | |
| on-destructive | `#FFFFFF` | |
| ring | `#1E3A8A` | |

### Medical Clinic / Healthcare
| Role | Value | Notes |
|------|-------|-------|
| primary | `#0891B2` | Medical teal — calm, clinical |
| on-primary | `#FFFFFF` | |
| secondary | `#22D3EE` | |
| on-secondary | `#0F172A` | |
| accent | `#16A34A` | Health green |
| on-accent | `#FFFFFF` | |
| background | `#F0FDFA` | |
| foreground | `#134E4A` | |
| card | `#FFFFFF` | |
| card-foreground | `#134E4A` | |
| muted | `#E8F1F6` | |
| muted-foreground | `#64748B` | |
| border | `#CCFBF1` | |
| destructive | `#DC2626` | |
| on-destructive | `#FFFFFF` | |
| ring | `#0891B2` | |

### Dental Practice
| Role | Value | Notes |
|------|-------|-------|
| primary | `#0EA5E9` | Fresh blue — clean, bright |
| on-primary | `#0F172A` | |
| secondary | `#38BDF8` | |
| on-secondary | `#0F172A` | |
| accent | `#0EA5E9` | Consistent blue CTA |
| on-accent | `#0F172A` | |
| background | `#F0F9FF` | |
| foreground | `#0C4A6E` | |
| card | `#FFFFFF` | |
| card-foreground | `#0C4A6E` | |
| muted | `#E8F2F8` | |
| muted-foreground | `#64748B` | |
| border | `#BAE6FD` | |
| destructive | `#DC2626` | |
| on-destructive | `#FFFFFF` | |
| ring | `#0EA5E9` | |

### Veterinary Clinic
| Role | Value | Notes |
|------|-------|-------|
| primary | `#0D9488` | Caring teal |
| on-primary | `#FFFFFF` | |
| secondary | `#14B8A6` | |
| on-secondary | `#0F172A` | |
| accent | `#EA580C` | Warm orange — "Book Visit" |
| on-accent | `#FFFFFF` | |
| background | `#F0FDFA` | |
| foreground | `#134E4A` | |
| card | `#FFFFFF` | |
| card-foreground | `#134E4A` | |
| muted | `#E8F1F4` | |
| muted-foreground | `#64748B` | |
| border | `#99F6E4` | |
| destructive | `#DC2626` | |
| on-destructive | `#FFFFFF` | |
| ring | `#0D9488` | |

### Beauty / Spa / Wellness
| Role | Value | Notes |
|------|-------|-------|
| primary | `#EC4899` | Soft pink — luxury, care |
| on-primary | `#FFFFFF` | |
| secondary | `#F9A8D4` | |
| on-secondary | `#0F172A` | |
| accent | `#8B5CF6` | Lavender luxury |
| on-accent | `#FFFFFF` | |
| background | `#FDF2F8` | Pink-tinted white |
| foreground | `#831843` | |
| card | `#FFFFFF` | |
| card-foreground | `#831843` | |
| muted | `#F1EEF5` | |
| muted-foreground | `#64748B` | |
| border | `#FBCFE8` | |
| destructive | `#DC2626` | |
| on-destructive | `#FFFFFF` | |
| ring | `#EC4899` | |

### Florist / Plant Shop
| Role | Value | Notes |
|------|-------|-------|
| primary | `#15803D` | Natural green |
| on-primary | `#FFFFFF` | |
| secondary | `#22C55E` | |
| on-secondary | `#0F172A` | |
| accent | `#EC4899` | Floral pink — contrast CTA |
| on-accent | `#FFFFFF` | |
| background | `#F0FDF4` | |
| foreground | `#14532D` | |
| card | `#FFFFFF` | |
| card-foreground | `#14532D` | |
| muted | `#E8F0F1` | |
| muted-foreground | `#64748B` | |
| border | `#BBF7D0` | |
| destructive | `#DC2626` | |
| on-destructive | `#FFFFFF` | |
| ring | `#15803D` | |

### Construction / Architecture
| Role | Value | Notes |
|------|-------|-------|
| primary | `#64748B` | Industrial grey — raw, strong |
| on-primary | `#FFFFFF` | |
| secondary | `#94A3B8` | |
| on-secondary | `#0F172A` | |
| accent | `#EA580C` | Safety orange |
| on-accent | `#FFFFFF` | |
| background | `#F8FAFC` | |
| foreground | `#334155` | |
| card | `#FFFFFF` | |
| card-foreground | `#334155` | |
| muted | `#EBF0F5` | |
| muted-foreground | `#64748B` | |
| border | `#E2E8F0` | |
| destructive | `#DC2626` | |
| on-destructive | `#FFFFFF` | |
| ring | `#64748B` | |

### Automotive / Car Dealership
| Role | Value | Notes |
|------|-------|-------|
| primary | `#1E293B` | Premium dark — sleek, modern |
| on-primary | `#FFFFFF` | |
| secondary | `#334155` | |
| on-secondary | `#FFFFFF` | |
| accent | `#DC2626` | Action red — "Test Drive" |
| on-accent | `#FFFFFF` | |
| background | `#F8FAFC` | |
| foreground | `#0F172A` | |
| card | `#FFFFFF` | |
| card-foreground | `#0F172A` | |
| muted | `#E9EDF1` | |
| muted-foreground | `#64748B` | |
| border | `#E2E8F0` | |
| destructive | `#DC2626` | |
| on-destructive | `#FFFFFF` | |
| ring | `#1E293B` | |

### Photography Studio
| Role | Value | Notes |
|------|-------|-------|
| primary | `#18181B` | Pure black — work IS the design |
| on-primary | `#FFFFFF` | |
| secondary | `#27272A` | |
| on-secondary | `#FFFFFF` | |
| accent | `#F8FAFC` | White contrast on dark elements |
| on-accent | `#0F172A` | |
| background | `#000000` | Full black — gallery mode |
| foreground | `#FAFAFA` | |
| card | `#0C0C0C` | |
| card-foreground | `#FAFAFA` | |
| muted | `#181818` | |
| muted-foreground | `#94A3B8` | |
| border | `#3F3F46` | |
| destructive | `#EF4444` | |
| on-destructive | `#FFFFFF` | |
| ring | `#18181B` | |

### Luxury / Premium Brand
| Role | Value | Notes |
|------|-------|-------|
| primary | `#1C1917` | Premium black |
| on-primary | `#FFFFFF` | |
| secondary | `#44403C` | |
| on-secondary | `#FFFFFF` | |
| accent | `#A16207` | Gold accent — premium feel |
| on-accent | `#FFFFFF` | |
| background | `#FAFAF9` | Warm off-white |
| foreground | `#0C0A09` | |
| card | `#FFFFFF` | |
| card-foreground | `#0C0A09` | |
| muted | `#E8ECF0` | |
| muted-foreground | `#64748B` | |
| border | `#D6D3D1` | |
| destructive | `#DC2626` | |
| on-destructive | `#FFFFFF` | |
| ring | `#1C1917` | |

### Hotel / Hospitality
| Role | Value | Notes |
|------|-------|-------|
| primary | `#1E3A8A` | Luxury navy |
| on-primary | `#FFFFFF` | |
| secondary | `#3B82F6` | |
| on-secondary | `#FFFFFF` | |
| accent | `#A16207` | Gold service — "Book Now" |
| on-accent | `#FFFFFF` | |
| background | `#F8FAFC` | |
| foreground | `#1E40AF` | |
| card | `#FFFFFF` | |
| card-foreground | `#1E40AF` | |
| muted | `#E9EEF5` | |
| muted-foreground | `#64748B` | |
| border | `#BFDBFE` | |
| destructive | `#DC2626` | |
| on-destructive | `#FFFFFF` | |
| ring | `#1E3A8A` | |

### Wedding / Event Planning
| Role | Value | Notes |
|------|-------|-------|
| primary | `#DB2777` | Romantic pink |
| on-primary | `#FFFFFF` | |
| secondary | `#F472B6` | |
| on-secondary | `#0F172A` | |
| accent | `#A16207` | Elegant gold |
| on-accent | `#FFFFFF` | |
| background | `#FDF2F8` | |
| foreground | `#831843` | |
| card | `#FFFFFF` | |
| card-foreground | `#831843` | |
| muted | `#F0EDF4` | |
| muted-foreground | `#64748B` | |
| border | `#FBCFE8` | |
| destructive | `#DC2626` | |
| on-destructive | `#FFFFFF` | |
| ring | `#DB2777` | |

### Insurance
| Role | Value | Notes |
|------|-------|-------|
| primary | `#0369A1` | Security blue |
| on-primary | `#FFFFFF` | |
| secondary | `#0EA5E9` | |
| on-secondary | `#0F172A` | |
| accent | `#16A34A` | Protected green |
| on-accent | `#FFFFFF` | |
| background | `#F0F9FF` | |
| foreground | `#0C4A6E` | |
| card | `#FFFFFF` | |
| card-foreground | `#0C4A6E` | |
| muted | `#E7EFF5` | |
| muted-foreground | `#64748B` | |
| border | `#BAE6FD` | |
| destructive | `#DC2626` | |
| on-destructive | `#FFFFFF` | |
| ring | `#0369A1` | |

### Childcare / Daycare
| Role | Value | Notes |
|------|-------|-------|
| primary | `#F472B6` | Soft pink — safe, gentle |
| on-primary | `#0F172A` | |
| secondary | `#FBCFE8` | |
| on-secondary | `#0F172A` | |
| accent | `#16A34A` | Safe green |
| on-accent | `#FFFFFF` | |
| background | `#FDF2F8` | |
| foreground | `#9D174D` | |
| card | `#FFFFFF` | |
| card-foreground | `#9D174D` | |
| muted | `#F1F0F6` | |
| muted-foreground | `#64748B` | |
| border | `#FCE7F3` | |
| destructive | `#DC2626` | |
| on-destructive | `#FFFFFF` | |
| ring | `#F472B6` | |

### Senior Care / Elderly Services
| Role | Value | Notes |
|------|-------|-------|
| primary | `#0369A1` | Calm blue — reassuring |
| on-primary | `#FFFFFF` | |
| secondary | `#38BDF8` | |
| on-secondary | `#0F172A` | |
| accent | `#16A34A` | Reassuring green |
| on-accent | `#FFFFFF` | |
| background | `#F0F9FF` | |
| foreground | `#0C4A6E` | |
| card | `#FFFFFF` | |
| card-foreground | `#0C4A6E` | |
| muted | `#E7EFF5` | |
| muted-foreground | `#64748B` | |
| border | `#E0F2FE` | |
| destructive | `#DC2626` | |
| on-destructive | `#FFFFFF` | |
| ring | `#0369A1` | |

### Cleaning Service
| Role | Value | Notes |
|------|-------|-------|
| primary | `#0EA5E9` | Fresh blue — clean, bright |
| on-primary | `#0F172A` | |
| secondary | `#38BDF8` | |
| on-secondary | `#0F172A` | |
| accent | `#059669` | Fresh green — "Book Cleaning" |
| on-accent | `#FFFFFF` | |
| background | `#F0F9FF` | Clean white-blue |
| foreground | `#0C4A6E` | |
| card | `#FFFFFF` | |
| card-foreground | `#0C4A6E` | |
| muted | `#E8F2F8` | |
| muted-foreground | `#64748B` | |
| border | `#BAE6FD` | |
| destructive | `#DC2626` | |
| on-destructive | `#FFFFFF` | |
| ring | `#0EA5E9` | |

### Pet Services (Grooming / Boarding)
| Role | Value | Notes |
|------|-------|-------|
| primary | `#F97316` | Playful orange — warm, friendly |
| on-primary | `#0F172A` | |
| secondary | `#FB923C` | |
| on-secondary | `#0F172A` | |
| accent | `#2563EB` | Trust blue |
| on-accent | `#FFFFFF` | |
| background | `#FFF7ED` | Warm cream |
| foreground | `#9A3412` | |
| card | `#FFFFFF` | |
| card-foreground | `#9A3412` | |
| muted | `#F1F0F0` | |
| muted-foreground | `#64748B` | |
| border | `#FED7AA` | |
| destructive | `#DC2626` | |
| on-destructive | `#FFFFFF` | |
| ring | `#F97316` | |

### Fitness / Gym
| Role | Value | Notes |
|------|-------|-------|
| primary | `#F97316` | Energy orange |
| on-primary | `#0F172A` | |
| secondary | `#FB923C` | |
| on-secondary | `#0F172A` | |
| accent | `#22C55E` | Success green — "Join Now" |
| on-accent | `#0F172A` | |
| background | `#1F2937` | Dark bg — energy feel |
| foreground | `#F8FAFC` | |
| card | `#313742` | |
| card-foreground | `#F8FAFC` | |
| muted | `#37414F` | |
| muted-foreground | `#94A3B8` | |
| border | `#374151` | |
| destructive | `#EF4444` | |
| on-destructive | `#FFFFFF` | |
| ring | `#F97316` | |

### Roofing
| Role | Value | Notes |
|------|-------|-------|
| primary | `#334155` | Slate grey — roofing material |
| on-primary | `#FFFFFF` | |
| secondary | `#475569` | |
| on-secondary | `#FFFFFF` | |
| accent | `#DC2626` | Urgency red — "Free Estimate" |
| on-accent | `#FFFFFF` | |
| background | `#F8FAFC` | |
| foreground | `#0F172A` | |
| card | `#FFFFFF` | |
| card-foreground | `#0F172A` | |
| muted | `#E9EDF1` | |
| muted-foreground | `#64748B` | |
| border | `#E2E8F0` | |
| destructive | `#DC2626` | |
| on-destructive | `#FFFFFF` | |
| ring | `#334155` | |

### HVAC / Air Conditioning
| Role | Value | Notes |
|------|-------|-------|
| primary | `#0284C7` | Cool blue — temperature, comfort |
| on-primary | `#FFFFFF` | |
| secondary | `#0EA5E9` | |
| on-secondary | `#0F172A` | |
| accent | `#EA580C` | Warm orange — balance hot/cold |
| on-accent | `#FFFFFF` | |
| background | `#F0F9FF` | |
| foreground | `#0C4A6E` | |
| card | `#FFFFFF` | |
| card-foreground | `#0C4A6E` | |
| muted | `#E8F2F8` | |
| muted-foreground | `#64748B` | |
| border | `#BAE6FD` | |
| destructive | `#DC2626` | |
| on-destructive | `#FFFFFF` | |
| ring | `#0284C7` | |

### Pest Control
| Role | Value | Notes |
|------|-------|-------|
| primary | `#15803D` | Nature green — safe, eco |
| on-primary | `#FFFFFF` | |
| secondary | `#22C55E` | |
| on-secondary | `#0F172A` | |
| accent | `#DC2626` | Alert red — "Eliminate Now" |
| on-accent | `#FFFFFF` | |
| background | `#F0FDF4` | |
| foreground | `#14532D` | |
| card | `#FFFFFF` | |
| card-foreground | `#14532D` | |
| muted | `#E8F0F1` | |
| muted-foreground | `#64748B` | |
| border | `#BBF7D0` | |
| destructive | `#DC2626` | |
| on-destructive | `#FFFFFF` | |
| ring | `#15803D` | |

### Moving / Storage
| Role | Value | Notes |
|------|-------|-------|
| primary | `#2563EB` | Tracking blue — logistics |
| on-primary | `#FFFFFF` | |
| secondary | `#3B82F6` | |
| on-secondary | `#FFFFFF` | |
| accent | `#EA580C` | Action orange — "Get Quote" |
| on-accent | `#FFFFFF` | |
| background | `#EFF6FF` | |
| foreground | `#1E40AF` | |
| card | `#FFFFFF` | |
| card-foreground | `#1E40AF` | |
| muted | `#E9EFF8` | |
| muted-foreground | `#64748B` | |
| border | `#BFDBFE` | |
| destructive | `#DC2626` | |
| on-destructive | `#FFFFFF` | |
| ring | `#2563EB` | |

### Travel / Tourism Agency
| Role | Value | Notes |
|------|-------|-------|
| primary | `#0EA5E9` | Sky blue — adventure |
| on-primary | `#0F172A` | |
| secondary | `#38BDF8` | |
| on-secondary | `#0F172A` | |
| accent | `#EA580C` | Adventure orange — "Book Trip" |
| on-accent | `#FFFFFF` | |
| background | `#F0F9FF` | |
| foreground | `#0C4A6E` | |
| card | `#FFFFFF` | |
| card-foreground | `#0C4A6E` | |
| muted | `#E8F2F8` | |
| muted-foreground | `#64748B` | |
| border | `#BAE6FD` | |
| destructive | `#DC2626` | |
| on-destructive | `#FFFFFF` | |
| ring | `#0EA5E9` | |

### Pharmacy / Drug Store
| Role | Value | Notes |
|------|-------|-------|
| primary | `#15803D` | Pharmacy green |
| on-primary | `#FFFFFF` | |
| secondary | `#22C55E` | |
| on-secondary | `#0F172A` | |
| accent | `#0369A1` | Trust blue |
| on-accent | `#FFFFFF` | |
| background | `#F0FDF4` | |
| foreground | `#14532D` | |
| card | `#FFFFFF` | |
| card-foreground | `#14532D` | |
| muted | `#E8F0F1` | |
| muted-foreground | `#64748B` | |
| border | `#BBF7D0` | |
| destructive | `#DC2626` | |
| on-destructive | `#FFFFFF` | |
| ring | `#15803D` | |

### Tattoo / Piercing Studio
| Role | Value | Notes |
|------|-------|-------|
| primary | `#18181B` | Ink black |
| on-primary | `#FFFFFF` | |
| secondary | `#3F3F46` | |
| on-secondary | `#FFFFFF` | |
| accent | `#DC2626` | Blood red — edgy CTA |
| on-accent | `#FFFFFF` | |
| background | `#0F172A` | Dark bg — studio vibe |
| foreground | `#F8FAFC` | |
| card | `#1E293B` | |
| card-foreground | `#F8FAFC` | |
| muted | `#334155` | |
| muted-foreground | `#94A3B8` | |
| border | `#475569` | |
| destructive | `#EF4444` | |
| on-destructive | `#FFFFFF` | |
| ring | `#DC2626` | |

### Church / Religious Organization
| Role | Value | Notes |
|------|-------|-------|
| primary | `#7C3AED` | Spiritual purple |
| on-primary | `#FFFFFF` | |
| secondary | `#A78BFA` | |
| on-secondary | `#0F172A` | |
| accent | `#A16207` | Warm gold |
| on-accent | `#FFFFFF` | |
| background | `#FAF5FF` | |
| foreground | `#4C1D95` | |
| card | `#FFFFFF` | |
| card-foreground | `#4C1D95` | |
| muted | `#ECEEF9` | |
| muted-foreground | `#64748B` | |
| border | `#DDD6FE` | |
| destructive | `#DC2626` | |
| on-destructive | `#FFFFFF` | |
| ring | `#7C3AED` | |

### Coworking Space
| Role | Value | Notes |
|------|-------|-------|
| primary | `#F59E0B` | Energetic amber — community |
| on-primary | `#0F172A` | |
| secondary | `#FBBF24` | |
| on-secondary | `#0F172A` | |
| accent | `#2563EB` | Booking blue |
| on-accent | `#FFFFFF` | |
| background | `#FFFBEB` | Warm cream |
| foreground | `#78350F` | |
| card | `#FFFFFF` | |
| card-foreground | `#78350F` | |
| muted | `#F1F2EF` | |
| muted-foreground | `#64748B` | |
| border | `#FDE68A` | |
| destructive | `#DC2626` | |
| on-destructive | `#FFFFFF` | |
| ring | `#F59E0B` | |

---

## Dark background palettes

> Use these when `visual-system` assigns Dark Cinematic profile or the niche demands it.

### Fitness / Gym (Dark)
| Role | Value | Notes |
|------|-------|-------|
| primary | `#F97316` | Energy orange |
| on-primary | `#0F172A` | |
| secondary | `#FB923C` | |
| on-secondary | `#0F172A` | |
| accent | `#22C55E` | Success green |
| on-accent | `#0F172A` | |
| background | `#1F2937` | |
| foreground | `#F8FAFC` | |
| card | `#313742` | |
| card-foreground | `#F8FAFC` | |
| muted | `#37414F` | |
| muted-foreground | `#94A3B8` | |
| border | `#374151` | |
| destructive | `#EF4444` | |
| on-destructive | `#FFFFFF` | |
| ring | `#F97316` | |

### Auto Repair (Dark)
| Role | Value | Notes |
|------|-------|-------|
| primary | `#1E293B` | Garage dark |
| on-primary | `#FFFFFF` | |
| secondary | `#334155` | |
| on-secondary | `#FFFFFF` | |
| accent | `#EA580C` | Safety orange |
| on-accent | `#FFFFFF` | |
| background | `#0F172A` | |
| foreground | `#F8FAFC` | |
| card | `#1E293B` | |
| card-foreground | `#F8FAFC` | |
| muted | `#334155` | |
| muted-foreground | `#94A3B8` | |
| border | `#475569` | |
| destructive | `#EF4444` | |
| on-destructive | `#FFFFFF` | |
| ring | `#EA580C` | |

### Nightclub / Bar / Entertainment (Dark)
| Role | Value | Notes |
|------|-------|-------|
| primary | `#7C3AED` | Neon purple |
| on-primary | `#FFFFFF` | |
| secondary | `#A78BFA` | |
| on-secondary | `#0F172A` | |
| accent | `#F43F5E` | Rose action |
| on-accent | `#FFFFFF` | |
| background | `#0F0F23` | Deep dark |
| foreground | `#E2E8F0` | |
| card | `#1E1C35` | |
| card-foreground | `#E2E8F0` | |
| muted | `#27273B` | |
| muted-foreground | `#94A3B8` | |
| border | `#4C1D95` | |
| destructive | `#EF4444` | |
| on-destructive | `#FFFFFF` | |
| ring | `#7C3AED` | |

### Photography (Dark)
| Role | Value | Notes |
|------|-------|-------|
| primary | `#18181B` | Pure black |
| on-primary | `#FFFFFF` | |
| secondary | `#27272A` | |
| on-secondary | `#FFFFFF` | |
| accent | `#F8FAFC` | White contrast |
| on-accent | `#0F172A` | |
| background | `#000000` | |
| foreground | `#FAFAFA` | |
| card | `#0C0C0C` | |
| card-foreground | `#FAFAFA` | |
| muted | `#181818` | |
| muted-foreground | `#94A3B8` | |
| border | `#3F3F46` | |
| destructive | `#EF4444` | |
| on-destructive | `#FFFFFF` | |
| ring | `#18181B` | |

### Tech / IT Services (Dark)
| Role | Value | Notes |
|------|-------|-------|
| primary | `#1E293B` | Code dark |
| on-primary | `#FFFFFF` | |
| secondary | `#334155` | |
| on-secondary | `#FFFFFF` | |
| accent | `#22C55E` | Terminal green |
| on-accent | `#0F172A` | |
| background | `#0F172A` | |
| foreground | `#F8FAFC` | |
| card | `#1B2336` | |
| card-foreground | `#F8FAFC` | |
| muted | `#272F42` | |
| muted-foreground | `#94A3B8` | |
| border | `#475569` | |
| destructive | `#EF4444` | |
| on-destructive | `#FFFFFF` | |
| ring | `#1E293B` | |

---

## Palette selection rules

1. **Exact match first.** If the business industry matches a palette name exactly, use it.
2. **Closest parent.** If no exact match (e.g., "tree trimming"), go to the parent category ("Landscaping / Lawn Care").
3. **Never blend.** Do NOT mix colors from two palettes. Pick one and commit.
4. **Visual profile override.** If `visual-system` assigns Dark Cinematic but the industry palette is light, check if a dark variant exists in this file. If yes, use it. If no, the agent may darken the palette by:
   - Swapping `background` ↔ `foreground`
   - Keeping `primary`, `secondary`, `accent` unchanged
   - Adjusting `card`, `muted`, `border` to dark equivalents
   - Re-validating ALL contrast ratios after swap
5. **Brand color override.** If `research-seo-agent` found the business's actual brand colors, those REPLACE `primary` and `secondary`. The rest of the palette stays. Re-validate contrast.
6. **CTA color = accent.** Always. No exceptions. The main CTA button uses `accent` bg + `on-accent` text.
7. **Section alternation.** Alternate between `background` and `muted` for visual rhythm. Never use the same bg for consecutive sections.
8. **No grey-on-grey.** If `primary` is grey-family AND `background` is grey-family, the result looks dead. Add color through `accent` aggressively.

---

## Tailwind CSS variable mapping

```css
:root {
  --primary: <primary>;
  --on-primary: <on-primary>;
  --secondary: <secondary>;
  --on-secondary: <on-secondary>;
  --accent: <accent>;
  --on-accent: <on-accent>;
  --background: <background>;
  --foreground: <foreground>;
  --card: <card>;
  --card-foreground: <card-foreground>;
  --muted: <muted>;
  --muted-foreground: <muted-foreground>;
  --border: <border>;
  --destructive: <destructive>;
  --on-destructive: <on-destructive>;
  --ring: <ring>;
}
```

The agent MUST output this CSS block in the landing's global styles, populated with the selected palette values. No hardcoded hex values in component code — always reference variables.

---

## Anti-patterns

- ❌ Using `primary` for CTA buttons (use `accent`)
- ❌ Using `accent` for large background areas (it's for small, high-impact elements)
- ❌ Ignoring `on-*` colors and guessing white/black
- ❌ Using the same color for `primary` and `accent` (they must contrast)
- ❌ Picking colors "that feel right" instead of from this catalog
- ❌ Using raw hex in components instead of CSS variables
- ❌ Skipping contrast validation after brand color override
