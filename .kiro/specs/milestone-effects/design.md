# Design — Milestone Effects

## Engine (`fun-easter-eggs.ts`)
- Trigger check runs on every accepted count change: an effect fires when the count
  crosses a milestone value (prev < milestone <= next), never on page load.
- The engine creates a fixed-position Canvas on demand, runs a requestAnimationFrame
  particle loop with a hard particle budget, then cancels the loop, clears and removes
  the Canvas. No Canvas exists in the DOM outside an active effect.
- Effect variants share one particle system with different emitters/palettes:
  - 520: pink-gold confetti hearts → haunted version: glowing fireflies
  - 666: fog layer (large soft sprites drifting) + pumpkin rain + moon flash
  - 888: golden coin/pumpkin downpour
  - 1314: starfield sparkle with ghost trails
  - 9999: combined grand finale (fog + downpour + sparkle), still ≤ 3s of blocking

## Performance guardrails
- Particle budget scales with viewport area and is halved under
  `prefers-reduced-motion`.
- If the tab is hidden mid-effect, the loop pauses instead of burning CPU.
