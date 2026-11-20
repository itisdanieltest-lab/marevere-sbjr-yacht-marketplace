# MAREVERE · SBJR yacht marketplace

This is the public source repository for the MAREVERE · SBJR project. The imported website source is Phase 6.20, a local Python/SQLite integration prototype. **This repository is not a deployed site and is not production-ready.**

## Start here

1. Read [`CODEX_WRANGLER_EXECUTION_HANDOVER.md`](CODEX_WRANGLER_EXECUTION_HANDOVER.md).
2. Read [`START_HERE_FOR_CHATGPT_WORK.md`](START_HERE_FOR_CHATGPT_WORK.md) and every document in [`HANDOVER/`](HANDOVER/).
3. Preserve the approved MAREVERE · SBJR logo and the agreed features, including the complete three-tier acquisition model and administrator listing controls.

## Source and data boundary

The application source, SQL migrations, QA source files, current handover, and non-inventory design assets are tracked here. Scoped project review deliverables are now also tracked: see [`GITHUB_ASSET_REVIEW_README.md`](GITHUB_ASSET_REVIEW_README.md), [`GITHUB_WEB_UPLOAD_STATUS.md`](GITHUB_WEB_UPLOAD_STATUS.md), the updated workbook, source-rights manifest, inventory counts, and [`MAREVERE_SBJR_Review_Package_No_Video_Payloads.zip`](MAREVERE_SBJR_Review_Package_No_Video_Payloads.zip). The ZIP contains all 30 vessel photos, three illustrative yacht models, six Blender files, and three assembled/exploded review clips. One web-review transcode is stored separately at the repository root; three original videos and two larger transcodes are not committed. See the upload-status note for details.

Owner authorization confirmed in this conversation on 2026-11-19 is limited to MAREVERE · SBJR project use and GitHub repository review. It is not a general license and does not authorize public website, staging, or production use. It does not establish seller authority, vessel accuracy, price, availability, or director/commercial/legal approval. The original source archive remains the authoritative complete media package.

Generated local runtime state, including `.runtime/`, demo credentials, local SQLite databases, environment files, Wrangler secrets, and Cloudflare account credentials, must never be committed.

## Wrangler status

The current backend is Python's standard-library HTTP server with local SQLite and binds only to loopback. It is not a Cloudflare Worker. A Wrangler deployment requires the Worker/D1/R2 integration described in the handover and real local plus protected-staging verification. Do not treat `wrangler deploy` on the current Python source as a valid deployment.

## Current release position

The website release position remains NO-GO. The project/GitHub media authorization does not approve website use, staging, production, commercial terms, seller authority, inventory accuracy, pricing, availability, or director decisions. Keep these approval gates separate and do not present unverified commercial or vessel claims as confirmed.

## Get the working source checkout

Clone this repository, then extract `MAREVERE_SBJR_Wrangler_Staging_Desktop_Package.zip` into the cloned repository root. The archive contains the application source and full handover folder. Read `CODEX_WRANGLER_EXECUTION_HANDOVER.md`, `START_HERE_FOR_CHATGPT_WORK.md`, and every file in `HANDOVER/` before changing code.
