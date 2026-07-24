# amp-templates

Custom AMP (CubeCoders Application Management Panel) Generic Module deployment templates.

Authored here (private, self-hosted GitLab). Push-mirrored automatically to a
public GitHub repo (`Comsicare/amp-templates`) because AMP's built-in
`ConfigurationRepositories` template-repo mechanism only supports unauthenticated
`git clone` against `github.com` — it cannot pull from a private repo or any
other git host.

## Security policy — no secrets in these files, ever

These files are templates only: application metadata, port definitions, and
update-source instructions for AMP's Generic Module system. **They must never
contain:**

- Passwords, admin passwords, or default credentials (use AMP's `{{Setting}}`
  templating or leave blank for the user to fill in during instance setup)
- API tokens, license keys, or auth secrets of any kind
- Internal hostnames, IPs, or filesystem paths specific to any one homelab
  deployment (a template must be generic/reusable, not hardcoded to one server)

A CI job (`.gitlab-ci.yml`) runs [gitleaks](https://github.com/gitleaks/gitleaks)
against every push to catch anything that slips through before it ever reaches
the public GitHub mirror. Treat a failing pipeline as a hard stop — do not
force-push around it.

## Templates

| Template | App | Notes |
|---|---|---|
| `pst.kvp` | [zaigie/palworld-server-tool](https://github.com/zaigie/palworld-server-tool) | Palworld server admin dashboard (PST). Linux x86_64/aarch64. Requires an existing Palworld dedicated server with RCON + REST API enabled; PST's own first-run wizard handles pointing it at the server's `Saved` folder and RCON/REST credentials — nothing server-specific is baked into this template. |

## Adding a new template

Follow AMP's Generic Module template convention (flat files at repo root,
lowercase, shared filename prefix per app):

- `<app>.kvp` — required
- `<app>config.json` — required (Settings Manifest; `[]` if the app configures
  itself via its own UI/wizard rather than AMP's config editor)
- `<app>metaconfig.json` — optional
- `<app>ports.json` — port definitions
- `<app>updates.json` — update source stages

## Mirror setup

GitLab push mirror: Settings → Repository → Mirroring repositories, direction
Push, target `https://github.com/Comsicare/amp-templates.git`. Syncs within a
few minutes of any push to `main`.
