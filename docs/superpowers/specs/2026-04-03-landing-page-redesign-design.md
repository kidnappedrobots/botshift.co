# BotShift Landing Page Redesign — Industrial Terminal

## Direction

Redesign the BotShift.co landing page from "AI slop" (cyan-on-dark, Inter font, glowing cards, AI-generated images everywhere) to an **Industrial Terminal** aesthetic: near-black background, warm orange accent, engineered feel. Mission control meets Bloomberg Terminal.

The content stays as-is — it's strong. The visual presentation changes completely.

## Design System

### Colors

| Token | Value | Usage |
|---|---|---|
| `--bg-primary` | `#0a0a0a` | Page background |
| `--bg-elevated` | `#111111` | Elevated surfaces, nav |
| `--border` | `#1a1a1a` | All borders and dividers |
| `--accent` | `#ff6b35` | Orange accent — labels, eyes, CTA, highlights |
| `--text-primary` | `#f5f5f5` | Headlines, important text |
| `--text-secondary` | `#777777` | Body text, descriptions |
| `--text-muted` | `#444444` | Tertiary text, system labels |

No gradients. No glow. No blur. No transparency effects.

### Typography

- **Headlines**: Space Grotesk (700, 800) — geometric, techy, distinctive
- **Body**: DM Sans (400, 500, 600) — clean, modern, readable
- **System labels**: JetBrains Mono (400, 600) — monospace for prefixes, numbers, status text

Font loading via Google Fonts with `display=swap`.

### Principles

- No glow, no gradients, no backdrop-filter
- 1px solid borders, not box-shadows
- Left-aligned by default, not centered
- Monospace labels for structural elements (`// section-name`, `[ok]`, numbered sequences)
- `border-radius: 4px` max (sharp, engineered)
- Dot-grid background texture on key sections (radial-gradient pattern)
- Orange used sparingly — accent, not dominant

## Images

### Drop (9 images)

- `hero-bg.png` — replaced by dot-grid + typography
- `process.png` — redundant with step funnel
- `philosophy-today.png` — replaced by typographic split
- `philosophy-tomorrow.png` — replaced by typographic split
- `agent-concierge.png`, `agent-sales.png`, `agent-operations.png`, `agent-ambassador.png`, `agents-all.png` — agents section is now a text roster with SVG icons, no images

### Keep (5 images + 1 updated)

- `logo.png`, `logo-transparent.png` — displayed without glow/drop-shadow
- `alexprofile.jpg`, `bohdan-white.jpg`, `turing-headshot.jpg` — real team photos
- `results.png` — UPDATED: same composition (phone + robot walking outside + receptionist) but phone screen recolored to orange/dark UI matching new design system. Already generated and placed.

### Generated new (1 image)

- `vision-hero.png` — Tall sleek robot with orange LED accents walking through a modern hotel corridor. Low angle, cinematic. Natural daylight, people walking casually. Already generated and placed at `images/generated/vision-hero.png`.

## Crafted Elements

### ASCII Robots (Hero)

6 ASCII art robots displayed randomly on each page load. Each has blinking eyes (CSS animation on the eye characters, orange color). One is picked at random via JS on page load and rendered in the hero section.

The robots (provided by user):

```
Robot 1 "classic":     Y__ / q p / O
Robot 2 "scout":       .---. / u u / r
Robot 3 "antenna":     _._._  / q q / e
Robot 4 "heavy":       .---. / q p / - (with wide arms)
Robot 5 "box":         |---| / n n / -
Robot 6 "visor":       __i / o o / ]-[
```

Eye blink animation: 4s cycle, brief blink at 90%. Left and right eyes offset by 0.1s.

### Boot Sequence (Hero) — REMOVABLE

A terminal boot sequence that plays on page load before the robot appears:

```
$ botshift init
[ok] loading agent framework ............ done
[ok] connecting business systems ...... done
[ok] calibrating spatial awareness .... done
[ok] deploying concierge agent ........ done
[ok] all systems operational
READY_█
```

Lines appear sequentially (0.5s stagger). Blinking cursor at end. After the sequence completes (~3s), the ASCII robot fades in on the right.

**Flag**: If this feels too busy with headline + boot sequence + robot, remove the boot sequence and just show headline + robot with a simpler fade-in. Test both versions.

## Section-by-Section Layout

### Nav (Fixed)

- Solid `--bg-elevated` background (no blur, no glass)
- 1px bottom border
- Logo left, links right
- CTA button: filled `--accent`, 4px radius, sharp
- Mobile: simple slide-down menu, no backdrop-filter

### Hero (Full viewport)

- **Left side**: Monospace prefix `// forward compatible ai` → Big headline (Space Grotesk 800) with "AI operators" in plain orange (not gradient) → Subtitle → Orange CTA button → Status bar at bottom: `● systems online | agents: 4 active`
- **Right side**: Boot sequence (if included) → Random ASCII robot with blinking eyes
- **Background**: Dot-grid texture (radial-gradient, subtle)
- No background image. No hero logo (it's in the nav).
- Left-aligned layout, not centered.

### Results — "We Build For Business Impact"

- 3-column grid separated by 1px lines (not card borders with rounded corners)
- Each cell: small SVG icon + monospace number (`01`, `02`, `03`) + title + description
- No hover lift effects.
- `results.png` image below the grid (phone with orange UI + robot in background) — this is the partner's original concept, recolored to match new design system
- Background: `--bg-elevated`

### Process — "Our Process To Grow KPIs"

- Keep the vertical step funnel structure (it's good)
- Restyle: orange step numbers, 1px connecting line, monospace step labels
- Remove progress bars (decorative only)
- Remove companion image (`process.png`)
- Left-aligned

### Vision — "AI is already here. The robots are coming."

- Two-column: `vision-hero.png` image left (full column width, no border-radius — raw edge), text right
- This is the emotional anchor — the only large photographic image on the page
- Monospace section label prefix
- Background: `--bg-elevated`

### Philosophy — "Build Once, Deploy Everywhere"

- Dramatic 50/50 horizontal split
- Left ("Today"): darker background, monospace label, heading, description
- Right ("Tomorrow"): subtle warm tint, same structure
- Separated by 1px vertical line
- No images
- Quote block below with left orange border
- **Fix broken copy**: "Our agents Because our agents..." → "Because our agents are built with spatial and situational logic from day one, they are ready to 'cross over' into robotic hardware the moment you are ready."

### Agents — "Your AI Team"

- No hero image — the roster format is strong enough on its own
- Vertical list/roster layout (NOT card grid)
- Each agent row: circle with SVG icon (orange stroke) + name + one-line description + monospace status label (`ACTIVE`)
- 1px border between rows
- "And many more possibilities..." as a subtle text line, not a dashed card

### Why Bot Shift — "Results Over Technology"

- Strong typographic hierarchy
- Lead statement in large text
- "Zero Migration" and "Future-Proofed ROI" as two text blocks separated by 1px horizontal line (not cards)
- Pure content, no images

### Team — "Built by Operators"

- Keep real team photos
- Cards restyled: 4px border-radius, 1px border, no hover glow
- Photo + name + role + experience bullets + company logos + social links
- Same content, editorial treatment
- Adam Turing card keeps its humor

### CTA — "Build Your Agent"

- No background image
- Centered text: big headline + subtitle + orange CTA button
- Dot-grid background echoing the hero
- Confident, minimal

### Footer

- Simple. Copyright. 1px top border. Monospace style.

## Animations

- **Scroll-triggered fade-in**: Keep the IntersectionObserver approach but use `opacity` + `translateY(16px)` (smaller movement than current 24px). No bounce.
- **Boot sequence**: Sequential line appearance with 0.5s stagger (hero only, removable).
- **ASCII robot blink**: 4s CSS animation cycle on eye characters.
- **Robot fade-in**: 0.6s opacity transition after boot sequence completes (or on load if boot is removed).
- **Hover states**: Subtle color shifts only. No `translateY` lifts, no glow shadows.
- **Status bar pulse**: The `●` dot in the hero status bar pulses gently (opacity animation).

## Responsive

- **1024px**: Vision section stacks (image on top). Team grid → 2 columns. Results → 2 columns.
- **768px**: Mobile nav (hamburger, slide-down, no blur). Hero stacks (text on top, robot below, smaller). Agents roster stays vertical (works naturally). Philosophy split stacks vertically.
- **480px**: Font size reductions. Team → 1 column.

## Content Changes

1. Fix philosophy "Tomorrow" broken sentence
2. Remove hero logo image (redundant with nav)
3. Add monospace section label prefixes throughout
4. All other content preserved exactly as-is

## Out of Scope

- No new pages
- No backend/JS framework changes
- No build tools — stays as single HTML file
- Images `vision-hero.png` and `agent-hero.png` need to be provided by user (placeholder treatment until available)
