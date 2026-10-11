# Viper AI — Team Venom HPR

Viper AI is Team Venom's information hub. The private dashboard is served by Cloudflare Worker; the GitHub Pages source has been changed to a public-only landing page.

## Links

- Secure login and registration: https://viper-ai.hughfletcher.workers.dev/login
- One-time captain setup: https://viper-ai.hughfletcher.workers.dev/setup-captain
- Intended public landing page: https://hughston-cyber.github.io/Viper-AI/

**Deployment note:** The latest GitHub Pages deployment reported that Pages is not enabled for this repository. To publish the safe landing page, open repository **Settings → Pages**, set the build and deployment source to **GitHub Actions**, then rerun the Pages workflow. Until that is enabled, use the Cloudflare Worker URL above.

## Access controls

- Registration requires a one-use invitation code.
- New accounts remain pending until the Team Captain approves them.
- Rider statistics, member information, race information and captain controls are served only after server-side authentication.
- The captain dashboard can approve or reject account requests, create and revoke invitation codes, and disable or restore member accounts.
- Passwords are hashed with PBKDF2; session tokens are stored as hashes and issued in Secure, HttpOnly, SameSite cookies.
- Invitation codes are stored as hashes and are single-use with an expiry.
- Private pages use no-store caching and are excluded from indexing.

## Infrastructure

- Authentication API and private dashboard: Cloudflare Worker `viper-ai`
- Authentication database: Cloudflare D1 `viper-ai-auth`
- Public landing page source: `index.html`

## First-time captain setup

Use the one-time setup code provided directly to the Team Captain at `/setup-captain`. Choose a strong password of at least 12 characters. The setup code is removed from the database after the captain account is created and cannot be reused.

Do not put setup codes, passwords, session tokens or API secrets in this repository. If the one-time setup code is lost before use, generate a new hash in the D1 `app_config` table and provide a new code securely.

## Important

Do not re-add member or rider records to the public GitHub Pages landing page or any other public static asset. Add private data only to the authenticated application or protected API.
