# 🎠 Hero-Karussell für herzenskunst.ch

Interaktives Bild-Karussell für die Pouring-Kunst-Galerie von [herzenskunst.ch](https://herzenskunst.ch).

**Live Preview:** https://dfeuerle.github.io/hero-karussell/hero-karussell.html  
**Live Seite:** https://herzenskunst.ch

---

## Features

| Feature | Beschrieb |
|---------|-----------|
| 🖼️ **6 Pouring-Kunst-Bilder** | Echtfotografie, lokal als `.webp` |
| 🔁 **Autoplay** | Automatischer Bildwechsel alle 3 Sekunden |
| ↻ **Reset bei Interaktion** | Klick auf Pfeil/Dot/Card setzt Autoplay zrugg |
| ↗️ **Diagonale Rotation** | Carousel um −2.5° gedreht für dynamische Optik |
| ✨ **Float-Animation** | Sanfte Sinus-Schwebebewegung, versetzt pro Card |
| 💨 **Exit-Blur-Effekt** | Beim Klick blur + scale + opacity-Ausblendung (400ms) |
| 📱 **Responsive** | Desktop 3 Items sichtbar, Mobile 1 Item |
| ♿ **reduced-motion** | `prefers-reduced-motion` wird respektiert |
| ⚡ **Lazy Loading** | `loading="lazy"` + `IntersectionObserver` |
| 🚀 **GPU-accelerated** | `will-change: transform, opacity` |

## Technik

### Stack

- **Single-File HTML** — alles inline, kein Framework, kein npm
- **CSS-in-HTML** — `<style>`-Block mit Tailwind-ähnlichem Inline-Ansatz
- **Vanilla JS** — Z-Index-Stacking-Positionierig, kei Library
- **Kei externe Assets** — bis uf d'Bilder (.webp) isch alles inline

### Quellcode-Struktur

```
hero-karussell.html          ← Single-File (155 Zeilen)
├── CSS (42 Zeilen)          ← Styles, Animationen, Media Queries
├── HTML (5 Zeilen)          ─ Section > Carousel > Track + Arrows + Dots
└── JS (93 Zeilen)           ─ Positionierung, Navigation, Autoplay
images/
├── 001.webp                 ← Sanfte Wogen
├── 004.webp                 ← Goldene Ader
├── 006.webp                 ← Farben der Tiefe
├── 008.webp                 ← Kristallblüte
├── 010.webp                 ← Feuer & Wasser
└── 012.webp                 ← Mond über Meer
hero-Karussell-herzenskunst.md  ← Ursprüngliche Spec
```

### Positionierungs-Algorithmus

Z-Index-basierts Stacking mit `translateX` + `scale`:

```
for each Card i:
  offset = i - current (mit Wrap)
  scale  = 1 - offset × 0.18
  opacity = max(0.25, 1 - offset × 0.35)
  zIndex = 10 - offset
  x = base + offset × (cardWidth + gap)
```

### Animationen

| Animation | Dauer | Easing | Beschrieb |
|-----------|-------|--------|-----------|
| **Float** | 4s | ease-in-out | Sinus-Schwebe (0 → −5px → 0), versetzte Delays |
| **Exit** | 400ms | ease-out | blur(8px) + opacity 0 + scale 1.15 |
| **Hover** | 400ms | ease | img scale(1.06) |
| **Transition** | 600ms | cubic-bezier(.25,.1,.25,1) | Card-Position + Skalierung |

### Bilderquelle

D Bilder stamme us dr Galerie vo [herzenskunst.ch](https://herzenskunst.ch/galerie) unter `/graphik/galerie/galerie/*.webp`.

## Entwicklung

```bash
# Lokal serve
python3 -m http.server 8080
# oder
npx serve .

# Öffne im Browser
open http://localhost:8080/hero-karussell.html
```

## Spec / Prompts

### Ursprünglichi Aaforderig

```
Hero-Karussell für herzenskunst.ch (Spiritual-Plattform).
Sanft, mystisch, organisch — "Herz-Karussell".

Constraints:
- KEI Framework, KEI npm, KEI externe Assets
- Single-File: hero-karussell.html (alles inline)
- Pure CSS-Animationen (opacity/transform Keyframes)
- GPU: will-change: transform, opacity
- Responsive: Mobile 1 Item → ab 768px 3 Items sichtbar
- prefers-reduced-motion respektiere
- IntersectionObserver + loading="lazy"
- 6 Items mit Bilder us dr Live-Galerie

Animationen:
1. Einschwebe: opacity 0→1, scale 0.85→1, 600ms ease-out
2. Float: Sanfti Sinus-Schwebebewegig (4s, 5px)
3. Klick-Exit: Klick → blur(8px) + opacity 0 + scale 1.15, 400ms
4. Z-Index-Stacking: Überlagerigseffekt
```

### Iteratione

| Schritt | Prompt | Änderig |
|---------|--------|---------|
| 1 | Emoji + Gradient-Cards durch echti Bilder ersetze | Galerie-Bilder vo herzenskunst.ch downgeloaded, reale img-Tag |
| 2 | chliner mache | Hero-Höhe reduziert, Cards 200×200 |
| 3 | selbstständig langsam drehe | Autoplay mit setInterval alle 4s + Reset bi Interaktion |
| 4 | no chliner | Cards 160×160, Carousel 170px Höhe |
| 5 | schneller, diagonal, no chliner | Autoplay 3s, Carousel -2.5° rotiert, Hero Gradient diagonal |

---

Erstellt mit ❤️ für **herzenskunst.ch** by Daniel Feuerle
