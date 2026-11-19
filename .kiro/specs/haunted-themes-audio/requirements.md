# Requirements — Haunted Themes & Audio

## R1 Theme system
As a visitor, I want the pet to transform between haunted themes so the page feels alive.
- THE SYSTEM SHALL ship 7 themes: Ghost Cat, Pumpkin Pal, Vampire Bat, Haunted Lantern,
  Skeleton Buddy, Witch's Familiar, Zombie Mochi.
- Each theme SHALL define: an inline SVG icon, accent/glow colours, an action word, a
  floating-text bank, a behaviour profile and at least 2 synthesized sound recipes.
- WHEN the business day rolls over THE SYSTEM SHALL rotate the default theme using a
  deterministic permutation that SHALL NOT repeat a theme within any 3 consecutive days.
- A visitor SHALL be able to switch themes manually; the choice SHALL persist.

## R2 Synthesized sound
As a site owner, I want Halloween sounds with no audio files to host or break.
- THE SYSTEM SHALL synthesize every sound with the Web Audio API (oscillators, noise
  buffers, biquad filters, gain envelopes) and SHALL NOT load any external audio asset.
- WHEN a visitor mutes the widget THE SYSTEM SHALL stay silent and persist the choice.
- Sounds SHALL only start after a user gesture (browser autoplay policy).

## Theme sound sketches
- Ghost Cat: sine-glide ghost wail with delayed echo; soft synthetic mew
- Pumpkin Pal: noise-burst pumpkin pop through a lowpass; hollow wooden knock
- Vampire Bat: amplitude-modulated high-frequency flutter; short descending screech
- Haunted Lantern: woody lantern knock (bandpass ping); flame whoosh (filtered noise swell)
- Skeleton Buddy: short pulse-train bone clicks; rattle shake
- Witch's Familiar: bell-like harmonic sparkle; bubbling cauldron (slow LFO on a bandpass)
- Zombie Mochi: low-frequency squish envelope; slow groan (detuned saws, lowpass)
