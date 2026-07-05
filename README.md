# 🐅 Royal Bengal Tiger — Bangladesh Chrome Theme

A Chrome browser theme inspired by the folk art traditions of Bengal — rickshaw painting, patachitra, and nakshi kantha motifs — brought together into a single cohesive visual identity for the browser chrome and New Tab Page. Available in **Light (Day)** and **Dark (Dusk)** variants.

![Platform](https://img.shields.io/badge/platform-Chrome-4285F4?logo=googlechrome&logoColor=white)
![Manifest](https://img.shields.io/badge/manifest-v3-orange)
![Status](https://img.shields.io/badge/status-stable-brightgreen)

---

## 📖 Purpose

Most Chrome themes fall into one of two traps: photographic wallpapers that ignore the browser's own UI elements, or generic "colorful gradient" packs with no cultural identity. This project set out to do something more specific — build a theme that is unmistakably **Bangladeshi in visual language**, using the country's own folk-art traditions as the design system rather than as decoration layered on top of a template.

The Royal Bengal Tiger, water lily (*shapla*, the national flower), and doyel bird (the national bird) anchor the composition, rendered in the bold flat-color, thick-outline style of traditional rickshaw-art and patachitra painting — the same visual tradition seen on hand-painted rickshaws, kantha embroidery, and folk scroll paintings across rural Bengal.

Beyond the artwork itself, this project treats the **Chrome theme spec as a real design system** — every color slot, tint value, and property flag was deliberately chosen and tested, rather than left at Chrome's defaults, so the browser frame, toolbar, tab strip, and New Tab Page all read as one considered object instead of a background image dropped behind an unrelated stock UI.

---

## 🎨 Content

### Light Theme — "Day"
A warm terracotta-red sky over a Bengal riverside scene: a Royal Bengal tiger resting beside a lily pond, a doyel bird in flight, palm trees, and a setting sun, bordered by a nakshi-kantha-inspired diamond pattern strip. Composition is deliberately minimal in the upper two-thirds of the frame — empty sky space — so the New Tab Page's search bar and shortcuts stay legible and uncluttered, with all illustrated elements confined to the lower third.

### Dark Theme — "Dusk"
The same scene reimagined as a night sky — deep navy blues, a warm orange moon/sun on the horizon, stars scattered across the upper frame, and the same tiger, lily pond, and border motif carried through for visual continuity between the two variants.

### Design Principles Applied
- **Cultural specificity over generic "folk art"** — explicit reference to Bangladeshi rickshaw art and patachitra painting styles rather than a broad, ambiguous "ethnic pattern" aesthetic.
- **Negative space as a feature** — the composition intentionally reserves calm, empty space in the region where NTP UI elements (search bar, shortcuts) render, avoiding visual competition with functional UI.
- **One accent color, consistently applied** — a single warm terracotta/orange accent used across both variants for every interactive element (links, toolbar icons, separators), so the eye learns "orange = actionable" throughout the browser.
- **Frame and toolbar colors sampled directly from the artwork**, not chosen independently — this closes the seam between the browser's static UI chrome and the illustrated background, which was the main visual problem solved during iteration (see Technicalities below).

---

## ⚙️ Technicalities

### File Structure
```
bangladesh_tiger_theme/          (Light variant)
├── manifest.json
└── images/
    └── ntp_background_4k.png

bangladesh_tiger_theme_dark/     (Dark variant)
├── manifest.json
└── images/
    └── ntp_background_4k_dark.png
```

### Manifest Version
Built on **Manifest V3**, Chrome's current extension/theme schema.

### Theme Fields Used
| Field | Purpose |
|---|---|
| `theme.images.theme_ntp_background` | 4K New Tab Page illustration |
| `theme.colors.frame` / `frame_inactive` | Browser window top-frame color (active/inactive window states) |
| `theme.colors.toolbar` / `toolbar_text` | Address bar and toolbar background/text |
| `theme.colors.toolbar_button_icon` | Icon color for toolbar buttons (extensions, profile, etc.) |
| `theme.colors.toolbar_vertical_separator` | Divider line between toolbar icon groups |
| `theme.colors.ntp_background` | Solid fallback color shown before the background image finishes decoding |
| `theme.colors.ntp_header` / `ntp_section` / `ntp_link` / `ntp_text` | New Tab Page text and accent colors |
| `theme.colors.bookmark_text` / `button_background` | Bookmark bar and button base colors |
| `theme.tints.buttons` / `frame` / `frame_inactive` | HSL tint shifts applied to Chrome's own default-rendered UI elements (e.g. profile avatar ring), aligned to the theme's hue family so no default grey/blue leaks through |
| `theme.properties.ntp_background_alignment` | Anchors the illustration to `bottom center` so key subjects stay visible regardless of window width |
| `theme.properties.ntp_background_repeat` | Set to `no-repeat` — a single full illustration, not a tiled pattern |
| `theme.properties.ntp_logo_alternate` | Forces the white Google logo lockup for legibility against the dark/warm background |

### Design Problems Solved During Development
1. **Frame/background color collision** — an early version used a frame color too close in hue to the artwork's own sky, creating a visually noisy "almost-matching-but-not-quite" seam at the top of the window. Fixed by deliberately choosing a frame color from a *different* element in the artwork (the water/night sky, a near-complementary tone) rather than trying to closely match the sky color.
2. **Load-flash mismatch** — Chrome renders `ntp_background` as a solid fallback color for a few frames before the illustration finishes decoding. Fixed by exact-matching this fallback color to the image's own corner pixel value, making the transition imperceptible instead of a visible flash.
3. **Overlay/texture experiments** — `theme_toolbar` (tiling texture) and `theme_frame_overlay` (corner motif) were tested and ultimately removed; both rendered as repeating tiled patterns across the full frame width rather than the subtle single-placement effect intended, and added visual noise without improving the design. Final build relies on solid, precisely-tuned colors only.

### Color Palette Reference

**Light Theme**
| Role | Hex |
|---|---|
| Frame / Toolbar | `#1E2A30` |
| Frame Inactive | `#161F25` |
| Accent (icons/links) | `#D8633A` |
| NTP Background (fallback) | `#C14732` |
| Text | `#FAF4EB` |

**Dark Theme**
| Role | Hex |
|---|---|
| Frame / Toolbar | `#111524` |
| Frame Inactive | `#0C0F1B` |
| Accent (icons/links) | `#E0783A` |
| NTP Background (fallback) | `#15192A` |
| Text | `#F0E9DE` |

---

## 🛠 Installation

1. Clone or download this repository.
2. Go to `chrome://extensions` in Chrome.
3. Enable **Developer mode** (top-right toggle).
4. Click **Load unpacked** and select either the `bangladesh_tiger_theme` (light) or `bangladesh_tiger_theme_dark` (dark) folder.
5. The theme will apply immediately. Switch variants by loading the other folder the same way.

---

## 📌 Notes

- This is a **static theme**, not an extension — Chrome's theme spec does not support animation, motion, or JavaScript-driven effects. Everything here is achieved through color, image, and tint configuration only.
- Both variants share the same accent color language and compositional structure so they read as one cohesive product rather than two unrelated designs.

---

## 🙏 Credits

Artwork generated with AI image tools, art-directed to follow the visual conventions of traditional Bangladeshi rickshaw art and patachitra folk painting. National symbols referenced: Royal Bengal Tiger (national animal), water lily / *shapla* (national flower), doyel bird (national bird).
