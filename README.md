# MAREVERE · SBJR yacht marketplace

This is the public source repository for the MAREVERE · SBJR project. The imported website source is Phase 6.20, a local Python/SQLite integration prototype. **This repository is not a deployed site and is not production-ready.**

## Start here

1. Read [`CODEX_WRANGLER_EXECUTION_HANDOVER.md`](CODEX_WRANGLER_EXECUTION_HANDOVER.md).
2. Read [`START_HERE_FOR_CHATGPT_WORK.md`](START_HERE_FOR_CHATGPT_WORK.md) and every document in [`HANDOVER/`](HANDOVER/).
3. Preserve the approved MAREVERE · SBJR logo and the agreed features, including the complete three-tier acquisition model and administrator listing controls.

## Source and data boundary

The application source, SQL migrations, QA source files, current handover, and non-inventory design assets are tracked here. The source's `inventory_private/` research workbook, raw broker photos/videos, per-asset rights manifest, and yacht-specific approximate 3D reconstructions are intentionally kept out of this public repository. The original source archive remains the authoritative copy. Do not upload or publish those files until the applicable rights and release gates in the handover are cleared.

Generated local runtime state, including `.runtime/`, demo credentials, local SQLite databases, environment files, Wrangler secrets, and Cloudflare account credentials, must never be committed.

## Wrangler status

The current backend is Python's standard-library HTTP server with local SQLite and binds only to loopback. It is not a Cloudflare Worker. A Wrangler deployment requires the Worker/D1/R2 integration described in the handover and real local plus protected-staging verification. Do not treat `wrangler deploy` on the current Python source as a valid deployment.

## Current release position

The handover records the current NO-GO gates, disputed research inventory, unverified seller authority, media licensing gaps, and missing director decisions. Do not describe commercial terms, inventory, payment, or director approvals as confirmed until evidence and approvals are recorded.


## Get the working source checkout

Clone this repository, then extract `MAREVERE_SBJR_Wrangler_Staging_Desktop_Package.zip` into the cloned repository root. The archive contains the application source and full handover folder. Read `CODEX_WRANGLER_EXECUTION_HANDOVER.md`, `START_HERE_FOR_CHATGPT_WORK.md`, and every file in `HANDOVER/` before changing code.
