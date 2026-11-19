# Haunted Page Pet 🎃👻

> A brand-new Halloween edition of an embeddable web page pet widget for personal blogs,
> documentation sites (Hexo / Hugo / VitePress) and developer communities.
> Built with [Kiro](https://kiro.dev) for **Kiroween 2026 — Category: Costume Contest**.

**Status: project skeleton.** The repository structure, Kiro steering docs and specs are in place;
implementation follows the task lists in `.kiro/specs/` (see *How this project is built* below).

---

## What it is

An interactive ghost pet that lives on a web page: visitors click it, drag it around, collapse it
into a tiny pumpkin, and trigger full-screen haunted celebrations at milestone counts.
The Halloween interface is **functional, not decorative** — every spooky theme changes the pet's
behaviour, floating texts and synthesized sounds, not just its colours.

All sound is synthesized live with the **Web Audio API** — zero external audio assets,
zero CDN requests, nothing to 404 or leak.

## Planned features

- **Interactive pet widget** — click counter with floating action texts, 5px-threshold drag with
  edge snapping, collapsible floating-orb form, `[ L ]` keyboard hotkey, position persistence
- **7 haunted themes** — Ghost Cat, Pumpkin Pal, Vampire Bat, Haunted Lantern, Skeleton Buddy,
  Witch's Familiar, Zombie Mochi; deterministic daily rotation (Beijing 04:00 business day,
  guaranteed non-repeating across any 3 consecutive days)
- **Zero-asset sound synthesis** — ghost wails, pumpkin pops, bat flutters, lantern knocks and more,
  generated from oscillators, noise buffers and biquad filters in real time
- **Milestone easter eggs** — full-screen Canvas fog / moonlight / pumpkin-rain effects at
  520 / **666** / 888 / 1314 / 9999, with on-demand Canvas creation and disposal (no memory leaks)
- **Dual mode** — standalone offline mode (localStorage) and an optional multiplayer API mode
  (batched sync, client-side rate limiting against autoclickers)
- **Embed anywhere** — a vanilla HTML snippet for static blogs and a React component

## Tech stack

TypeScript · React 18+ · Vite · Web Audio API · Canvas · localStorage

## How this project is built (Kiro)

This project is developed spec-first in Kiro. The `/.kiro` directory at the repository root is
part of the submission and is intentionally **not** gitignored:

- `.kiro/steering/` — product, tech and structure rules Kiro follows in every session
- `.kiro/specs/core-widget/` — the widget core (interaction, drag, persistence, dual mode)
- `.kiro/specs/haunted-themes-audio/` — the theme system and the sound synthesis engine
- `.kiro/specs/milestone-effects/` — the milestone particle / fog effects
- `.kiro/hooks/` — agent hooks (type-check + tests on save), created in the Kiro UI

## Disclosure

This is a **new project**, created during the Kiroween 2026 submission period (from 2026-11-19).
It is inspired by the author's earlier open-source widget
[page_pet_widget](https://github.com/DymINHK/page_pet_widget) (MIT). That earlier repository is
not the submission; any ideas or code reused from it will be disclosed here and in the Devpost
submission, and this repository is built fresh in the submission period.

## Getting started (once implementation lands)

```bash
npm install
npm run dev     # local demo
npm test        # unit tests (theme rotation, counter sanitising, milestone triggers)
```

Or open `examples/vanilla-html/index.html` directly in a browser — no build step.

## License

[MIT](LICENSE)
