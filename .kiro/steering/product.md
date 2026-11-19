# Product Steering — Haunted Page Pet

## What this is
An embeddable, interactive Halloween desktop-pet widget for personal blogs, documentation
sites (Hexo / Hugo / VitePress) and developer communities. Built for Kiroween 2026,
category **Costume Contest**.

## Who it is for
- Blog / docs site owners who want a playful, zero-backend interactive widget
- Their visitors, who click, drag and play with the pet

## Product principles (apply in every change)
1. **The costume is functional.** Every haunted theme must change behaviour, floating
   texts AND synthesized sounds together. A theme that only recolours the pet is a bug.
2. **Atmosphere never eats readability.** Spooky visuals must keep text contrast and
   interaction targets usable. If fog/particles hide content, tone them down.
3. **Zero external assets.** No external audio files, no external images, no CDN scripts.
   Graphics are inline SVG; all sound is synthesized with Web Audio. This is a headline
   feature, not an implementation detail.
4. **Embed-first.** The widget must work when dropped into an arbitrary third-party page:
   no global CSS pollution, no required backend, offline standalone mode by default.
5. **Delight in small doses.** Milestone celebrations are full-screen but brief, and the
   Canvas used for them is created on demand and disposed of afterwards.
6. **Privacy by design.** No cookies, no tracking, no fingerprinting. State lives in
   localStorage under the `haunted_pet_` prefix only.

## Out of scope
- User accounts or login
- A production multiplayer backend (API mode is an interface + example route only)
- Mobile apps, browser extensions
- Any asset that has to be fetched at runtime
