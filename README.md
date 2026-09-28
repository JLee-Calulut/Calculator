# Calculator

A keyboard-friendly calculator — extracted from the [John Lee Calulut portfolio](https://github.com/JLee-Calulut) into a standalone
**Vue 3 + Vite + Tailwind CSS** project. No backend, no build complexity.

## Features

- Chained operations (`128 × 4 ÷ 2`), percent, sign toggle, decimal handling
- Rolling history (last 20) with click-to-reuse results
- Floating-point-safe arithmetic (0.1 + 0.2 → 0.3)
- Full keyboard support: `0-9`, `.`, `+ - * /`, `Enter`/`=`, `%`, `Backspace`, `Esc`
- Divide-by-zero error handling
- Same dark orange/black design system as the portfolio (ink palette, Inter + JetBrains Mono)

## Run

```bash
npm install
npm run dev      # → http://localhost:5173
```

Production build & preview:

```bash
npm run build    # outputs to dist/
npm run preview
```

## Structure

```
src/
├─ App.vue                      → standalone page shell (backdrop, heading, layout)
├─ Composables/
│  ├─ useCalculator.js          → all calculator logic (pure client-side)
│  └─ useScrollReveal.js        → scroll-reveal animation helper
└─ Components/
   ├─ UI/AppIcon.vue            → inline SVG icon set
   └─ Calculator/               → Calculator, Display, Keypad, HistoryPanel
```
