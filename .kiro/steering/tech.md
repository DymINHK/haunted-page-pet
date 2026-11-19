# Tech Steering — Haunted Page Pet

## Stack
- TypeScript (strict) + React 18+ + Vite
- Web Audio API for all sound; Canvas 2D for milestone effects
- localStorage for standalone persistence; no backend required
- Tests: Node's built-in test runner under `tests/`

## Hard rules
1. **No external audio or image files.** Every sound is synthesized at runtime from
   oscillators, shared noise buffers, biquad filters and gain envelopes. Every graphic
   is inline SVG defined in code. If a change adds a media file or a remote URL, reject it.
2. **No runtime CDN dependencies.** The built widget must run from a static host
   (GitHub Pages) and from a plain `<script>` embed with no network calls for assets.
3. **Sanitise before DOM.** All SVG strings and floating texts are statically defined
   and validated; never inject unsanitised user input into the DOM.
4. **Rate-limit interaction.** Client-side: more than 120 clicks in 10s triggers a 30s
   cooldown. Counter deltas are validated and clamped before they are applied or sent.
5. **Clean up effects.** Any Canvas or AudioContext created for an effect must be
   released when the effect ends. No leaked canvases, no orphaned audio nodes.
6. **Business day = Beijing time (UTC+8), day boundary 04:00.** Theme rotation and
   daily counters use this definition everywhere; do not use local midnight.
7. **Accessibility floor.** Interactive elements keep visible focus, the pet can be
   muted, and milestone effects respect `prefers-reduced-motion` by shortening.

## Conventions
- Storage keys are prefixed `haunted_pet_`
- Theme definitions are data (`FunTheme` objects), not per-theme components
- Sound recipes are pure functions of (theme, action) returning a node graph plan
