# Viper AI — Team Venom HPR

Viper AI is a dark, venom-green operations dashboard prototype for Team Venom.

## Features
- Responsive dashboard and quick navigation
- Local task board with add, complete, and delete actions
- Viper Chat demo with built-in responses (not a connected AI model)
- Editable sample team roster and CSV export
- Race-day checklist
- Browser-local persistence with `localStorage`

## Run locally
Open `index.html` in a modern browser. No build tools or dependencies are required.

## GitHub Pages
This repository includes a GitHub Actions workflow that publishes the root of the repository to GitHub Pages. In GitHub, open **Settings → Pages** and ensure the publishing source is **GitHub Actions** if prompted. After the first workflow succeeds, the site should be available at:

https://hughston-cyber.github.io/Viper-AI/

## Important limitations
This is a front-end prototype. It does not have user accounts, a shared database, background automations, or a real AI provider connection. Data stored in localStorage only exists in the browser/device where it was entered.

Never place private API keys or secrets in client-side files. A real AI connection should be implemented through a secure backend, with authentication, access controls, and appropriate privacy protections.
