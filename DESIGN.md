---
name: petfoodcal-design
description: "A quieter Vercel-inspired design system: a stark monochrome duet of ink and canvas, softened by static ambient glows, and paired with clean Outfit sans and JetBrains Mono fonts."

colors:
  primary: "#171717"
  on-primary: "#ffffff"
  neutral-bg: "#fafafa"
  canvas: "#ffffff"
  canvas-soft-2: "#f5f5f5"
  ink: "#171717"
  body: "#4d4d4d"
  mute: "#595959"
  hairline: "#ebebeb"
  hairline-strong: "#a1a1a1"
  link: "#0070f3"

typography:
  display:
    fontFamily: "Outfit, system-ui, -apple-system, sans-serif"
    fontSize: "clamp(36px, 5.5vw, 54px)"
    fontWeight: 600
    lineHeight: 1.05
    letterSpacing: "-2.4px"
  body:
    fontFamily: "Outfit, system-ui, -apple-system, sans-serif"
    fontSize: "16px"
    fontWeight: 400
    lineHeight: 1.7
  mono:
    fontFamily: "JetBrains Mono, ui-monospace, SFMono-Regular, Menlo, Monaco, monospace"
    fontSize: "12px"
    fontWeight: 400

rounded:
  xs: "4px"
  sm: "6px"
  md: "8px"
  lg: "12px"
  xl: "16px"
  pill: "100px"
  full: "9999px"

spacing:
  sm: "12px"
  md: "16px"
  lg: "24px"
  xl: "32px"
  xxl: "48px"

components:
  button-primary:
    backgroundColor: "{colors.primary}"
    textColor: "{colors.on-primary}"
    rounded: "{rounded.pill}"
    height: "48px"
  button-primary-sm:
    backgroundColor: "{colors.primary}"
    textColor: "{colors.on-primary}"
    rounded: "{rounded.sm}"
    height: "32px"
  form-input:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.ink}"
    rounded: "{rounded.sm}"
    height: "40px"
  card-container:
    backgroundColor: "{colors.canvas}"
    rounded: "{rounded.md}"
    padding: "32px"
---

# Design System: petfoodcal

## 1. Overview

**Creative North Star: "The Restrained Studio"**

This system represents a quieter, highly disciplined interpretation of a developer-inspired design system. The user interface acts as a silent helper for pet owners, letting the math-driven nutritional calculations stand at the center without visual distraction. The page layout is built on a stark monochrome grid of white `{colors.canvas}`, soft-gray `{colors.neutral-bg}`, and deep ink `{colors.ink}` text. Rather than loud marketing highlights, depth and texture are created using subtle static gradient backdrops, crisp hairline borders, and clean typography.

This design system explicitly rejects the overstimulating conventions of consumer products, including moving mesh gradients, pulsing dots, and warning-box alerts. The result is a calm, premium, and trustworthy utility that pet owners can consult in any lighting condition.

**Key Characteristics:**
- Stark monochrome ink and canvas surface layout.
- Static, extremely low-opacity (≤8%) background gradients instead of active motion.
- Monospaced metadata and eyebrows in muted neutral gray.
- Rounded pill marketing CTAs paired with sharp, functional 6px border radii on UI inputs.
- Layered, soft stacked shadows for UI cards.

## 2. Colors

The color palette is restricted to pure black-ink conversions, warm-tinted grays, and a single functional blue accent for inline links.

### Primary
- **Ink** (`{colors.primary}` — `#171717`): The primary conversion target color, used for all primary CTAs, headings, and bold text.
- **On Primary** (`{colors.on-primary}` — `#ffffff`): Text color used on primary background surfaces.

### Neutral
- **Canvas Soft** (`{colors.neutral-bg}` — `#fafafa`): The default page background surface, providing a soft 98% white reading backdrop.
- **Canvas** (`{colors.canvas}` — `#ffffff`): Pure white, used exclusively for foreground interactive surfaces and card containers.
- **Canvas Soft 2** (`{colors.canvas-soft-2}` — `#f5f5f5`): Light-gray background fill, used for input elements, default options, and notice card wrappers.
- **Body Gray** (`{colors.body}` — `#4d4d4d`): Secondary text color, used for descriptions and explanatory prose.
- **Mute Gray** (`{colors.mute}` — `#595959`): Third-tier text color, used for placeholders, annotations, and footnotes.
- **Hairline** (`{colors.hairline}` — `#ebebeb`): 1px borders, dividers, and default input outlines.
- **Hairline Strong** (`{colors.hairline-strong}` — `#a1a1a1`): Stronger dividers and neutral accent markers.

### Named Rules
**The Restrained Glow Rule.** Colored gradients must only be used as static, low-opacity (≤8%) background atmospheric glow layers. They are never animated, never foregrounded, and never used on interactive elements.

**The Muted Eyebrow Rule.** All metadata tags, section labels, and monospaced subtitles must use muted neutral gray (`{colors.mute}`). Primary colors or high-contrast accent fills are prohibited on labels.

## 3. Typography

**Display Font:** Outfit (fallback: sans-serif)
**Body Font:** Outfit (fallback: sans-serif)
**Label/Mono Font:** JetBrains Mono (fallback: monospace)

The typography is built on Outfit, a clean geometric sans, paired with JetBrains Mono for a precise technical voice. Displays use tight line height and negative letter-spacing for an editorial feel.

### Hierarchy
- **Display** (600, `clamp(36px, 5.5vw, 54px)`, 1.05): Hero headlines. Uses negative letter-spacing (`-2.4px`).
- **Headline** (600, `32px`, 1.25): Main section titles. Uses negative letter-spacing (`-1.28px`).
- **Title** (600, `20px`, 1.4): Card headings and item subtitles.
- **Body** (400, `16px` / `15px`, 1.7): Default copy. Line length capped at 65–75 characters (`65ch`–`75ch`) for readability.
- **Label** (400, `12px` / `11px`, normal): Small monospaced subtitles and categorical eyebrows.

### Named Rules
**The Sentence-Case Headline Rule.** All display headlines and titles must be written in sentence-case and terminate with a period.

**The Monospace Limit Rule.** Monospaced text is strictly reserved for technical data labels, step headers, and calculations. It must never be used for main body paragraphs or narratives.

## 4. Elevation

The system is flat-by-default, relying on 1px hairline borders (`{colors.hairline}`) and tonal changes (`{colors.canvas}` cards against a `{colors.neutral-bg}` page) to define hierarchy.

### Shadow Vocabulary
- **Level 1 (Subtle)** (`0px 0px 0px 1px rgba(0, 0, 0, 0.08) inset`): Default border definition for inputs and interactive items.
- **Level 2 (Active)** (`0px 0px 0px 1px rgba(0, 0, 0, 0.08) inset, 0px 1px 1px rgba(0, 0, 0, 0.02), 0px 2px 2px rgba(0, 0, 0, 0.04)`): Elevates buttons and active selections.
- **Level 3 (Card)** (`0px 0px 0px 1px rgba(0, 0, 0, 0.08) inset, 0px 2px 2px rgba(0, 0, 0, 0.04), 0px 8px 8px -8px rgba(0, 0, 0, 0.04)`): Elevates main interactive panels (e.g. the calculator container).

### Named Rules
**The Flat-At-Rest Rule.** All cards and containers sit flat on the canvas. Shadows must only be applied to indicate active state transitions or user input focus.

## 5. Components

### Buttons
- **Shape:** Rounded pill (`{rounded.pill}`) for marketing buttons; sharp 6px corner radius (`{rounded.sm}`) for inline utility buttons.
- **Primary:** Background `{colors.primary}`, text `{colors.on-primary}`, height 48px, horizontal padding 32px.
- **Hover:** Slight reduction in opacity (92%) and micro-scaling transition.

### Cards / Containers
- **Corner Style:** 8px border radius (`{rounded.md}`).
- **Background:** Pure white `{colors.canvas}` or light-gray inset `{colors.canvas-soft-2}`.
- **Internal Padding:** 32px (`{spacing.xl}`) on desktop, 20px on mobile viewports.
- **Border:** 1px `{colors.hairline}`.

### Inputs / Fields
- **Style:** 1px `{colors.hairline}` border, background `{colors.canvas}`, height 40px, corner radius 6px (`{rounded.sm}`).
- **Focus:** 2px solid `{colors.primary}` outline with 2px offset.

### Navigation
- **Header Nav:** Sticky 64px tall nav bar, canvas background, 1px hairline border bottom. Links are set in Outfit `body-sm` (13px) and transition to `{colors.canvas-soft-2}` on hover with a fully rounded (`{rounded.full}`) shape.

## 6. Do's and Don'ts

### Do:
- **Do** use static, low-opacity (≤8%) background gradients for atmosphere.
- **Do** write display headlines in sentence-case, ending with a period.
- **Do** use 1px hairline borders for all card and container dividers.
- **Do** keep body text readable by capping line length at 65–75 characters.
- **Do** make information cards (like the transition notice) neutral gray and border-hairlined.

### Don't:
- **Don't** animate background mesh gradients. Keep them static.
- **Don't** use pulsating dots or high-contrast accent backgrounds on eyebrows and labels.
- **Don't** use warning-colored yellow/orange boxes for general informational notices.
- **Don't** use colored side-stripe borders on cards.
- **Don't** require user login, email capture, or show vet-advice overlays that block calculation results.
- **Don't** include product recommendations or brand-sponsored links in results.
