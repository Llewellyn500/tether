# Contributing

Thanks for helping improve Tether. This project is an Obsidian plugin, so changes should keep desktop and mobile-compatible Obsidian environments in mind.

## Development Setup

1. Install dependencies with `npm install`.
2. Run `npm run dev` while developing. This rebuilds `main.js` when source files change.
3. For a production bundle, run `npm run build`.
4. Copy `main.js`, `manifest.json`, and `styles.css` into `.obsidian/plugins/tether/` in a test vault.

## Pull Requests

- Keep changes focused and describe the user-visible behavior they affect.
- Update documentation when behavior, setup, commands, or release steps change.
- Run `npm run build` before opening a pull request.
- Avoid committing credentials, access tokens, vault contents, or local Obsidian settings.

## Release Assets

GitHub releases should include these files:

- `main.js`
- `manifest.json`
- `styles.css`

Release assets are built and attested through the release workflow so users can verify their provenance with GitHub artifact attestations.
