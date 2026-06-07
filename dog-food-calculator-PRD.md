# Product Requirements Document
## Pet Food Calculator — Web App (petfoodcal)

---

## 1. Product Overview

A free, neutral, one-page web tool that calculates the correct daily feeding amount
for any dog. It covers all major food types, outputs results in practical real-world
units (cups, grams, meals per day), and includes a bag duration calculator. Built
for regular pet owners in the US market — not vets, not UK users, not brand-specific
buyers.

**Brand name:** `petfoodcal`
**Domain:** `petfoodcal.com`

---

## 2. Target Audience

- US-based dog owners (primary)
- People feeding raw, dry kibble, wet food, homemade, or mixed diets
- New pet owners who just adopted a puppy and don't know where to start
- Raw feeding community (BARF, 80/10/10 feeders) — highly engaged, share tools heavily
- Mobile users (most searches happen on phone while holding a dog food bag)

---

## 3. Problem Being Solved

**Competitor 1 — PNA (petnutritionalliance.org):**
- Built for veterinary professionals only (their own disclaimer)
- Has zero age/life stage input — treats a puppy and adult the same
- Requires user to know "Body Condition Score" (1–9 scale) and calories per cup
  of their food — most owners don't have this information
- Output is in kcal/day — not actionable for regular owners
- No cups, no meals per day, no bag duration

**Competitor 2 — Southend Dog Training (southenddogtraining.co.uk):**
- UK website — KG only, no LB option (US market unserved)
- Has puppy option but output is just one number in grams
- No breed size, no activity level, no body condition
- Does not say how many meals per day (critical for puppies)
- Does not say when to transition from puppy to adult feeding
- Pushes user to buy their own UK food brand immediately after result

**The gap:** No clean, neutral, US-first tool exists that gives a pet owner practical,
meal-by-meal guidance in the units they actually use.

---

## 4. Goals

- Rank on Google for 6+ Easy KD keywords from one single page
- Build trust by being 100% neutral (no product links, no brand bias)
- Give output so practical that users bookmark petfoodcal.com and return when
  their dog's weight changes
- Drive sharing in dog owner communities (Reddit, Facebook raw feeding groups)
- Earn AdSense revenue from US traffic (highest CPM niche)

---

## 5. Primary SEO Keywords

**Main Keyword (build the page around this):**
- `raw dog food calculator` — Easy KD, >100 monthly US searches

**Supporting Keywords (use naturally in page content and FAQ):**
- `homemade dog food calculator`          — Easy KD, >100 vol
- `mixing wet and dry dog food calculator` — Easy KD, >100 vol
- `how much wet food to feed a dog calculator` — Easy KD, >100 vol
- `how long will my dog food last calculator`  — Easy KD, >100 vol
- `80/10/10 raw dog food calculator`      — Easy KD, >100 vol
- `dog food calculator by breed`          — Medium KD, >100 vol
- `how much should I feed my dog`         — Medium KD, >1000 vol (secondary target)
- `raw dog food calculator puppy`         — Low comp
- `pet food calculator`                   — Medium KD (brand-aligned keyword)

---

## 6. Page Structure

Single-page MPA (Multi-Page Application) layout:

```
[Header — petfoodcal logo + Tool Name]
[Hero — One line: "Find out exactly how much to feed your dog"]
[Calculator Section]  ← main tool
[How It Works — 600-word SEO content section]
[FAQ Section — JSON-LD structured data]
[Footer — Privacy Policy, Terms, About Us, Contact Us links]
```

---

## 7. Calculator — All Inputs

### Step 1: Food Type
User selects ONE option. This step determines what the output looks like.

| Option        | Label                    |
|---------------|--------------------------|
| Raw Complete  | Raw (Complete)           |
| Raw 80/10/10  | Raw (80/10/10 — DIY)     |
| Dry Kibble    | Dry Kibble               |
| Wet Food      | Wet / Canned Food        |
| Homemade      | Homemade Food            |
| Mixed         | Mixed (Dry + Wet)        |

---

### Step 2: Dog Details

| Field            | Type          | Options / Notes                                                        |
|------------------|---------------|------------------------------------------------------------------------|
| Dog Name         | Text input    | Optional — used to personalize result ("Tyson needs...")              |
| Weight           | Number input  | LB by default, toggle to KG                                           |
| Life Stage       | Toggle        | Puppy / Adult / Senior                                                 |
| Puppy Age Bracket| Shown if Puppy| Under 4 months / 4–6 months / 6–12 months                            |
| Breed Size       | Button select | Toy (<10 lb) / Small (10–25 lb) / Medium (25–55 lb) / Large (55–100 lb) / Giant (100 lb+) |

---

### Step 3: Health & Lifestyle

All questions use simple visual buttons — no dropdowns, no sliders.

**Body Condition:**
- Underweight (ribs visible, very lean)
- Ideal (healthy weight)
- Overweight (hard to feel ribs)

**Activity Level:**
- Low (mostly indoors, short walks)
- Normal (daily walks, regular play)
- High (runs, hikes, very active)

**Goal:**
- Lose Weight
- Maintain Weight
- Gain Weight

**Neutered / Spayed:**
- Yes
- No

---

## 8. Calculator Logic & Formulas

### Base Feeding Percentage by Life Stage

| Life Stage | Age            | Base % of Body Weight Per Day |
|------------|----------------|-------------------------------|
| Puppy      | Under 4 months | 9%                            |
| Puppy      | 4–6 months     | 7%                            |
| Puppy      | 6–12 months    | 5%                            |
| Adult      | 1–7 years      | 2.5%                          |
| Senior     | 7+ years       | 2%                            |

---

### Multipliers Applied on Top of Base

**Breed Size Multiplier**
| Breed Size    | Multiplier |
|---------------|------------|
| Toy / Small   | × 1.10     |
| Medium        | × 1.00     |
| Large         | × 0.95     |
| Giant         | × 0.90     |

**Activity Multiplier**
| Activity | Multiplier |
|----------|------------|
| Low      | × 0.90     |
| Normal   | × 1.00     |
| High     | × 1.15     |

**Goal Multiplier**
| Goal         | Multiplier |
|--------------|------------|
| Lose Weight  | × 0.80     |
| Maintain     | × 1.00     |
| Gain Weight  | × 1.20     |

**Body Condition Multiplier**
| Condition   | Multiplier |
|-------------|------------|
| Underweight | × 1.10     |
| Ideal       | × 1.00     |
| Overweight  | × 0.85     |

**Neutered Multiplier**
| Status            | Multiplier |
|-------------------|------------|
| Neutered / Spayed | × 0.90     |
| Intact            | × 1.00     |

---

### Final Formula

```
weight_kg = weight_lb / 2.205   (if user entered LB)

base_grams = weight_kg × (base_percentage / 100) × 1000

daily_grams = base_grams
              × breed_multiplier
              × activity_multiplier
              × goal_multiplier
              × body_condition_multiplier
              × neutered_multiplier

daily_grams = round to nearest 5g
```

---

### Meal Frequency by Life Stage

| Life Stage           | Meals Per Day |
|----------------------|---------------|
| Puppy under 6 months | 3 meals       |
| Puppy 6–12 months    | 2–3 meals     |
| Adult                | 2 meals       |
| Senior               | 2 meals       |

Divide `daily_grams` equally across meals for per-meal amount.

---

### Cups Conversion (for Dry Kibble and Mixed)

Use 110g per cup as default (average for standard dry kibble).
Show as: `X cups (approx.)` — note that actual cups may vary by brand density.

```
daily_cups    = daily_grams / 110
per_meal_cups = daily_cups / meals_per_day
```

---

### 80/10/10 Breakdown (only shown when Raw 80/10/10 selected)

```
muscle_meat = daily_grams × 0.80
raw_bone    = daily_grams × 0.10
organ_total = daily_grams × 0.10
  liver       = daily_grams × 0.05
  other_organ = daily_grams × 0.05
```

---

### Mixed Feeding Split (only shown when Mixed selected)

Default: 50% dry + 50% wet by caloric contribution.
Since wet food is ~75% water, by weight: 40% dry kibble + 60% wet food by grams.

```
dry_grams = daily_grams × 0.40
wet_grams = daily_grams × 0.60
```

---

## 9. Calculator Output

### Result Card — shown after clicking Calculate

**Header line (personalized):**
`Tyson needs approximately X grams per day`

**Main output block:**

```
Daily Total:    XXXg  |  X.X oz  |  ~X cups*

Meals per day:  2 (recommended for adult dogs)

Morning meal:   XXXg  |  ~X cup
Evening meal:   XXXg  |  ~X cup

*Cups are approximate. Actual amount varies by food brand density.
```

**If Raw 80/10/10 selected, add:**
```
80/10/10 Daily Breakdown:
  Muscle Meat:    XXXg  (80%)
  Raw Bone:        XXg  (10%)
  Organ:           XXg  (10%)
    └ Liver:       XXg   (5%)
    └ Other Organ: XXg   (5%)
```

**If Mixed (Dry + Wet) selected, add:**
```
Mixed Feeding Breakdown:
  Dry Kibble:  XXXg  (~X cups)   — Morning
  Wet Food:    XXXg  (~X pouch)  — Evening
```

**Puppy transition note (shown only for 6–12 month puppies):**
```
📌 When Tyson turns 12 months, switch to adult feeding: ~XXg/day (2.5% body weight).
```

---

## 10. Bag Duration Calculator

Shown below the main result as a secondary feature.

**Label:** "How long will your food last?"

**Input:**
- Bag / pack size — number field
- Unit toggle: KG / LB

**Output (calculated instantly on input):**
```
Your Xkg bag will last approximately XX days.
Next purchase date: [today's date + XX days]
```

**Formula:**
```
bag_grams    = bag_size_kg × 1000   (or bag_lb / 2.205 × 1000)
days_lasted  = floor(bag_grams / daily_grams)
next_purchase = today + days_lasted
```

---

## 11. SEO Content Section (600 words minimum)

Required by Google to understand what the page is about. Place below the calculator.

**Heading structure:**
```
H2: How Much Should You Feed Your Dog?
H3: Pet Food Calculator — How It Works
H3: Feeding by Life Stage: Puppies vs Adults vs Seniors
H3: How Activity Level Affects Your Dog's Food Amount
H3: Raw Feeding: Understanding the 80/10/10 Ratio
H3: Mixing Wet and Dry Dog Food
H3: How Long Will My Dog Food Last?
```

Content must naturally include all supporting keywords listed in Section 5.
Write for US audience. Use LB as default unit in examples. Mention common US
brands by name (Purina, Royal Canin, Blue Buffalo, Merrick) for context —
but do not recommend any brand.

---

## 12. FAQ Section

Use JSON-LD structured data for all FAQ items (triggers Google rich results).

**Questions to include (pulled directly from Ahrefs "Questions" tab):**

1.  How much should I feed my dog?
2.  How much raw food should I feed my puppy?
3.  What is the 80/10/10 raw dog food ratio?
4.  How much wet food should I feed my dog calculator?
5.  How long will my dog food last?
6.  How do I mix wet and dry dog food?
7.  How much homemade food should I feed my dog?
8.  How much should I feed my dog to lose weight?
9.  How often should I feed my dog per day?
10. How much should I feed my dog after neutering?
11. How do I calculate raw dog food for a puppy?
12. How much dry food should I feed my dog calculator?

---

## 13. Required Pages for AdSense Approval

All four pages must be separate routes and linked in both header and footer:

| Page             | Minimum Content                                                          |
|------------------|--------------------------------------------------------------------------|
| Privacy Policy   | How data is used, no personal data collected, Google Analytics disclosure |
| Terms & Conditions | Tool is a guide, not veterinary advice, use at own risk               |
| About Us         | What petfoodcal is, who it is for, why it was built                     |
| Contact Us       | Contact form or email address                                            |

**Also required:**
- `robots.txt` — with sitemap link pointing to `petfoodcal.com/sitemap.xml`
- `sitemap.xml` — all page URLs under `petfoodcal.com`
- 404 error page — custom, not default Astro error page
- Google Analytics tracking — in `<head>` on every page
- `_headers` file — block `.pages.dev` subdomain from indexing

---

## 14. Meta Tags

**Homepage `<title>`:**
`Pet Food Calculator — Free Dog Feeding Calculator by Weight & Age | petfoodcal`

**Meta description (under 160 characters):**
`Free pet food calculator for raw, kibble, wet & homemade diets. Get daily grams,
cups, meal splits & bag duration. Works for puppies, adults & seniors.`

**Canonical URL:** `https://petfoodcal.com`

**OG image:** Tool screenshot or clean illustrated dog graphic (1200×630px)
**OG title:** `petfoodcal — Free Pet Food Calculator`
**OG description:** Same as meta description

---

## 15. What This Tool Does NOT Include

- No product recommendations or affiliate links inside the calculator
- No brand-specific calorie databases (keeps tool neutral and future-proof)
- No login or account creation required
- No email capture wall before showing results
- No vet disclaimer that blocks or scares users away from the result
- No kcal-based output (too technical for regular owners)

---

## 16. Competitive Edge Summary

| What Makes petfoodcal Different        | Why It Matters                                          |
|----------------------------------------|---------------------------------------------------------|
| LB as default unit                     | US market is largest; both competitors ignore it        |
| Age/life stage properly handled        | PNA ignores age; Southend has basic brackets only       |
| Practical output (cups + meals/day)    | Both competitors give only grams — not actionable       |
| Puppy transition note                  | No competitor tells owner when/how to switch to adult   |
| Bag duration calculator                | Unique feature — not on any competing tool              |
| 80/10/10 breakdown                     | Raw feeding community will share this; no clean tool    |
| 100% neutral, no product push          | Southend immediately upsells their UK food after result |
| Covers all 5 food types                | Southend is raw-only; PNA is calorie-based only         |
| Clean brand name: petfoodcal.com       | Short, memorable, keyword-adjacent, easy to type        |
| One page ranks for 6+ Easy KD keywords | More keywords = more traffic paths, more AdSense CPM    |