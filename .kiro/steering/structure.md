# Structure Steering — Haunted Page Pet

## Repository layout
```
haunted-page-pet/
  .kiro/
    steering/   product.md / tech.md / structure.md   (this file)
    specs/      core-widget/ haunted-themes-audio/ milestone-effects/
    hooks/      agent hooks created in the Kiro UI (see hooks/README.md)
  src/
    components/ FunPetWidget.tsx (main widget component)
    lib/
      fun-themes.ts          theme data + daily rotation
      fun-sound.ts           Web Audio synthesis engine
      fun-easter-eggs.ts     milestone Canvas effects
      fun-counter.ts         counter model + input sanitising
      fun-cst.ts             Beijing business-day helpers
      fun-theme-preference.ts theme preference persistence
      buzz-simulation.ts     standalone-mode community buzz curve
    index.ts                 package entrypoint
  examples/
    vanilla-html/index.html  zero-build embed demo
    backend-api/route.example.ts  multiplayer API route example
  tests/                     node --test suites
  index.html / package.json / README.md / LICENSE
```

## Rules
- One feature = one spec folder. Do not implement a feature that has no spec;
  write or update the spec first, then code to its tasks.md.
- `src/lib` modules stay framework-free (pure TypeScript) so they can be unit-tested
  without a DOM; React lives only in `src/components`.
- The `/.kiro` directory is part of the deliverable: never gitignore it, never move it.
- Examples must keep working: the vanilla HTML demo is the fastest smoke test and the
  page that gets deployed for judging.
