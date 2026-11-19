# Design — Haunted Themes & Audio

## Theme data model (`fun-themes.ts`)
```ts
interface FunTheme {
  id: string; name: string; subtitle: string;
  accentColor: string; glowColor: string;
  actionWord: string; floatTexts: string[];
  behaviour: 'float' | 'hang' | 'bounce-slow' | 'glow-pulse' | 'rattle';
  svgIcon: string; // inline SVG, validated before render
}
```
Themes are data, not components. The widget renders any theme through the same code
path, which is what makes the daily rotation and manual switching trivial.

## Rotation
- Seed = Beijing business date. A deterministic permutation of the 7 themes is derived
  from the date; the algorithm guarantees no repeat inside any 3-day window and is
  covered by unit tests over a simulated year.

## Sound engine (`fun-sound.ts`)
- One lazily created `AudioContext`, resumed on first gesture.
- A single shared white-noise buffer is reused by all noise-based recipes.
- A recipe is a function `(ctx, destination, params)` building a small node graph
  (source → filters → gain envelope → destination) that stops and disconnects itself.
- Master gain node implements mute; per-theme gains keep volumes balanced.
