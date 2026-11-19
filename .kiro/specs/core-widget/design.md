# Design — Core Widget

## Components
- `FunPetWidget.tsx` — the only React component. Props: `mode` ('standalone' | 'api'),
  `apiEndpoint?`, `storagePrefix`, `themes?`, `initialMuted?`, `initialCollapsed?`,
  `enableHotkey?`, `className?`, `style?`.
- Rendering is layered: pet button (inline SVG from the active theme), floating-text
  layer, and (only during milestones) a full-screen Canvas layer owned by
  `milestone-effects`.

## State model (`fun-counter.ts`)
- `todayCount`, `yesterdayCount`, `totalCount`, `myCount` — all integers, sanitised
  on load and on every delta (non-finite / negative / oversized deltas are clamped).
- Gesture state machine: idle → pressed (records origin) → dragging once movement
  passes 5px → released (snap + persist) | clicked (if released before threshold).

## Persistence
- One JSON blob per storage prefix; versioned key so future migrations are possible.
- Position is stored as viewport-relative ratios, not pixels, so it survives resizes.

## API mode
- POST `{ delta }` → `{ success, businessDate, todayCount, yesterdayCount, totalCount,
  myCount, topCount, acceptedDelta }`. The client applies the server's accepted delta,
  never its own optimistic count, when the two disagree.
