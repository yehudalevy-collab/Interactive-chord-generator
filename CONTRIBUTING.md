# Contributing

Thanks for improving Interactive Chord Generator. The repository has two related surfaces:

- `packages/chord-core`: framework-agnostic chord theory, MIDI, voicing, progression, and Tone.js playback helpers.
- `apps/web`: the Vite + React workspace that turns the core package into an interactive browser app.

Keep shared theory or playback behavior in `chord-core` when possible. App-only UI state, persistence, and interaction details belong under `apps/web`.

## Local Setup

```bash
npm install
npm run dev
```

The web app starts at `http://localhost:5173`.

## Validation

Run both checks before opening a pull request:

```bash
npm run build
npm test
```

`npm run build` compiles the core package first, then the web app. `npm test` runs the Vitest suite for chord theory, progression timing, persistence, and app behavior.

## Change Guidelines

- Add or update tests when changing chord identification, voicing, MIDI conversion, progression scheduling, or persistence behavior.
- Preserve the public exports in `packages/chord-core/src/index.ts` unless the change is intentionally breaking.
- Keep Tone.js/browser audio calls behind user-triggered UI flows; browsers may block audio started outside a gesture.
- Avoid committing generated build output from `apps/web/dist`.
- When changing UI behavior, check keyboard/mouse interaction on both the chromatic controls and the piano keyboard.

## Pull Request Notes

Please include:

- what changed and why
- commands run for validation
- screenshots or a short screen recording for visible UI changes
- any changes to the `chord-engine-core` public API
