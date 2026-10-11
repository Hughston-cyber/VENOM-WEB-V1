# Viper AI — Team Venom HPR

Viper AI is Team Venom's information hub. The public GitHub Pages site is only a landing page; the private dashboard is served by the Cloudflare Worker.

## Live sites

- Public landing page: https://hughston-cyber.github.io/Viper-AI/
- Secure team hub: https://viper-ai.hughfletcher.workers.dev/

## Access controls

- Members must register using a one-use invitation code.
- New accounts remain pending until the Team Captain approves them.
- Rider statistics, member information, race information and captain controls are served only after server-side authentication.
- The captain dashboard can approve/reject account requests, create and revoke invitation codes, and disable/restore member accounts.
- Passwords are hashed with PBKDF2; session tokens are stored as hashes and issued in Secure, HttpOnly, SameSite cookies.
- Invitation codes are stored as hashes and are single-use with an expiry.
- Private pages use no-store caching and are excluded from indexing.

## Infrastructure

- Front end and authentication API: Cloudflare Worker `viper-ai`
- Database: Cloudflare D1 `viper-ai-auth`
- Public landing page: GitHub Pages

## First-time captain setup

Use the one-time setup code provided directly to the Team Captain at `/setup-captain`. Choose a strong password of at least 12 characters. The setup code is deleted from the database after the captain account is created and cannot be reused.

Do not put setup codes, passwords, session tokens or API secrets in this repository. If the one-time setup code has been lost before use, generate a new hash in the D1 `app_config` table and provide a new code securely.

## Important

This project uses server-side authorization. Do not re-add member or rider records to the public GitHub Pages landing page or other public static assets. Add new private data to the authenticated application or protected API instead.
