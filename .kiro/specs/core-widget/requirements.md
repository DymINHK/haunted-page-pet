# Requirements — Core Widget

User stories with EARS acceptance criteria.

## R1 Embeddable widget
As a site owner, I want to add the pet to my page with one script tag or one React
component, so that I need no backend and no build changes.
- WHEN the widget is loaded on a page THE SYSTEM SHALL render the pet without any
  network request for audio or image assets.
- WHEN the host page uses its own CSS THE SYSTEM SHALL NOT leak global styles into it.

## R2 Click interaction
As a visitor, I want clicking the pet to feel responsive and rewarding.
- WHEN a visitor clicks the pet THE SYSTEM SHALL increment the counter, play the
  current theme's click sound and show a floating text from the theme's text bank.
- WHEN clicks exceed 120 within 10 seconds THE SYSTEM SHALL enter a 30 second
  cooldown and ignore further clicks.

## R3 Dragging
As a visitor, I want to move the pet out of my way.
- WHEN a pointer moves less than 5px THE SYSTEM SHALL treat the gesture as a click.
- WHEN a visitor drags the pet THE SYSTEM SHALL follow the pointer, clamp to the
  viewport, snap to the nearest edge on release, and persist the position.

## R4 Collapsed form and hotkey
- WHEN a visitor collapses the widget THE SYSTEM SHALL shrink it to a small round
  pumpkin/ghost orb that can be re-expanded with one click.
- WHEN a visitor presses the `L` key THE SYSTEM SHALL register a click interaction.

## R5 Persistence and modes
- THE SYSTEM SHALL persist counter, position, mute and theme preference in
  localStorage under the `haunted_pet_` prefix (standalone mode).
- WHERE an API endpoint is configured THE SYSTEM SHALL batch clicks (40 per request)
  and sync counts in API mode, falling back to standalone behaviour on failure.
- Daily counters SHALL roll over on the Beijing (UTC+8) 04:00 business-day boundary.
