# Codex desktop handover — Wrangler staging execution

**Project:** MAREVERE · SBJR yacht marketplace  
**Repository:** <https://github.com/itisdanieltest-lab/marevere-sbjr-yacht-marketplace>  
**Imported source baseline:** Phase 6.20  
**Current state:** public GitHub repository; local-only Python/SQLite prototype; no Wrangler Worker, Cloudflare D1/R2 bindings, hosted staging URL, or production release.

## First actions on the desktop

Clone into the desktop and work from that checkout. Do not copy secrets or runtime files into it.

**Windows PowerShell**

```powershell
Set-Location "$env:USERPROFILE\Desktop"
git clone https://github.com/itisdanieltest-lab/marevere-sbjr-yacht-marketplace.git
Set-Location .\marevere-sbjr-yacht-marketplace
git status --short --branch
git switch -c codex/wrangler-staging
```

**macOS/Linux**

```sh
cd ~/Desktop
git clone https://github.com/itisdanieltest-lab/marevere-sbjr-yacht-marketplace.git
cd marevere-sbjr-yacht-marketplace
git status --short --branch
git switch -c codex/wrangler-staging
```

Before changing code, read this document, `START_HERE_FOR_CHATGPT_WORK.md`, and every file in `HANDOVER/`. Treat the handover plan as sequential. Keep the current main branch intact and send progress as commits on `codex/wrangler-staging`.

## What is included and what stays local

The repo contains the website code, backend prototype, SQL history, development checks, current handover docs, and non-inventory design assets. The full Phase 6.20 source archive is named `MAREVERE_SBJR_GPT_WORK_COMPLETE_HANDOVER_2026-11-18.zip` in the owner's ChatGPT Library. It remains the source of truth for the 30 research photos, three broker videos, source/rights manifest, workbook, and approximate yacht-specific 3D files.

Those research media and workbook files are marked private and rights-pending in the handover. Keep them out of this public repository, public Worker assets, and public Git history. If the owner supplies a local copy for engineering, put it under the ignored `inventory_private/` path, verify its checksum against `CHECKSUMS_AND_CONTENTS.json`, and use only fictional or cleared media in an internet-accessible staging site. Do not delete or overwrite the original archive. `.gitignore` is configured to keep `inventory_private/` and `.runtime/` out of commits.

Local demo credentials are generated under `.runtime/` on first run. Never copy them into Wrangler variables, GitHub, screenshots, handover output, or chat. Use fictional-only local test accounts.

## Preserve the approved product

- Preserve the exact existing MAREVERE · SBJR logo, header/footer use, typography, layout, images, and videos. Do not redraw or replace approved branding.
- Preserve the public collection, vessel dossiers, buyer account/saved vessels, seller proposals, support flows, administrator inventory/status/visibility/evidence/audit functions, and the marine services/shop/community surfaces already in source.
- Preserve the **three-tier acquisition model**; Tier 2 has two proposed configurations, making four configurations total. Keep the terms labelled proposed/unapproved until the three directors and counsel decide them. No buy/deposit/checkout CTA for research listings.
- Keep listing states and sale authority honest. The three present records are research leads, not verified MAREVERE sale offers; ARISTARCHOS I is recorded as sold historically. No seller mandate/title/availability can be invented.
- Keep director approvals separate from routine administrator listing management. Do not create director accounts, identities, sign-offs, or quorum rules without the owner's confirmed details.
- No real payments, escrow, ownership transfer, binding contracts, or production customer data in staging.

## Required architecture work before Wrangler deployment

The current `backend/app.py` runs only on loopback and stores local data in SQLite. Wrangler does not run it as a Cloudflare Worker. Keep the current UI intact while implementing a server-backed Worker with explicit API routes and a D1-compatible data layer; do not replace the app with a static mock or visual-only preview.

1. Inventory every current API route, role check, session/CSRF control, audit event, and UI caller. Map each to Worker behavior before porting.
2. Build an ES-module Worker and serve the existing site assets through the Worker/asset binding. Keep private files outside the public asset directory.
3. Port schemas and migrations deliberately to Cloudflare D1. Validate each migration against a local D1 database before any remote apply; the existing SQLite database file itself is not a migration.
4. Use separate `staging` environment bindings. Keep secrets in Cloudflare Worker secrets or the desktop's ignored `.dev.vars`; never in `wrangler.jsonc`, Git, or command output.
5. Design staging access control before publishing a URL. Use fictional accounts/data, restrict access to the owner and only explicitly authorized reviewers, disable indexing, and verify unauthenticated access is blocked. Do not expose a public `workers.dev` endpoint with admin/demo controls left open.
6. Keep inventory media in private object storage with allowlisted API delivery and authorization. Only move media to R2 after the owner confirms rights for the intended staging audience; never deploy the private research workbook, source URLs, or rights manifest as public static assets.
7. Add only the integrations required for this phase. Do not imply payments, live support, email verification, director approvals, or seller verification work when those systems are absent.

## Wrangler workflow

Use Cloudflare's official Wrangler documentation and the signed-in desktop account. Dashboard sign-in and Wrangler CLI authorization are distinct: begin with `npx wrangler whoami`. If CLI authorization is missing, use the official `npx wrangler login` flow in the desktop and let the account owner complete any browser confirmation. Never request or paste a token into chat.

After the Worker implementation and local checks are ready:

1. Install Wrangler locally in the project as a development dependency and commit the lockfile; avoid an unpinned global install.
2. Run local Worker checks with `npx wrangler dev --env staging` using local D1/R2 emulation first. Complete the relevant project tests and actual browser flows against that local Worker.
3. Inspect the Cloudflare account/plan before creating remote resources. D1/R2 and other services can have usage or billing implications. Stop and report the exact resource and cost exposure if a paid plan, billing method, or charge is required; do not upgrade or add payment details.
4. Create only resources named for **staging**, bind them only to the staging environment, and apply D1 migrations to the named staging database. Confirm the environment/database name before every remote migration.
5. Deploy only after staging access control is in place and all required local checks pass. Use the explicit staging environment, e.g. `npx wrangler deploy --env staging`, after inspecting the final config. Capture the returned URL and deployment ID and verify the deployed worker, routes, roles, and media protections.
6. Run the handover's browser, security, accessibility, and responsive acceptance matrix against the deployed staging site. Record passes, failures, and untested areas. A successful CLI upload alone does not prove a working feature.
7. Keep production publication, custom-domain/DNS changes, public indexing, payment enablement, real inventory publication, and director/legal decisions as separate release gates.

Cloudflare primary references:

- Wrangler commands: <https://developers.cloudflare.com/workers/wrangler/commands/>
- Wrangler configuration: <https://developers.cloudflare.com/workers/wrangler/configuration/>
- D1 migrations: <https://developers.cloudflare.com/d1/reference/migrations/>
- D1 Wrangler commands: <https://developers.cloudflare.com/d1/wrangler-commands/>
- R2 pricing and allowances: <https://developers.cloudflare.com/r2/pricing/>

## Checks already known

The local project snapshot previously recorded Phase 6.19/6.20 API, media, and inventory checks. A later isolated run of the current public-source copy passed the catalogue (38/38), public media (42/42), and inventory (45/45) checks. Two older security/smoke scripts could not start in that environment because the Python `requests` package was missing. Browser access to the isolated loopback server also failed. These are local prototype results only; they are **not** Wrangler, cloud, Android, or live-browser verification.

## Completion report required

When a protected staging build is actually verified, report the repo commit, exact staging URL, Wrangler/Worker version, D1 migration state, access-control check, test results, responsive screenshots, unresolved rights/approval gates, and anything not tested. Keep a change log. If a deployment or integration remains blocked, name the blocker and leave the site at an honest NO-GO state.
