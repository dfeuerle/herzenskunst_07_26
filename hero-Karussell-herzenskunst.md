# Goal: Hero-Karussell für herzenskunst.ch

## Spec
Ein interaktives Hero-Karussell für herzenskunst.ch (Spiritual-Plattform). Sanft, mystisch, organisch — "Herz-Karussell".

## Constraints
- **KEIN Framework, KEIN npm, KEINE externen Assets**
- Single-File: `hero-karussell.html` (alles inline: HTML + CSS + JS)
- Pure CSS-Animationen (opacity/transform Keyframes)
- GPU: `will-change: transform, opacity; transform: translateZ(0)`
- Responsive: Mobile 1 Item → ab 768px 3 Items sichtbar
- `prefers-reduced-motion` respektieren
- IntersectionObserver + loading="lazy"
- 6 Platzhalter mit Gradient-Containern + Emoji + Titel

## Animationen
1. **Einschweben:** opacity 0→1, scale 0.85→1, 600ms ease-out
2. **Float:** Sanfte Sinus-Schwebebewegung (3-5s, 5-8px)
3. **Klick-Exit:** Klick → blur(8px) + opacity 0 + scale 1.2, 400ms → nächstes rückt auf
4. **Z-Index-Stacking:** Überlagerungseffekt

## Deliverables
1. Erstelle `hero-karussell.html` im Arbeitsverzeichnis
2. Serve mit `npx serve .` — zeig dass Seite läuft

## Karpathy-Regeln
- **Think Before Coding:** Layout skizzieren vor Code
- **Simplicity First:** < 250 Zeilen. Keine Abstraktionen.
- **Surgical Changes:** Nur 1 Datei.
- **Goal-Driven:** "serve läuft + Karussell interaktiv" = ▉
