# Maximo Fieldnotes migration package

This package contains the Site source, dependency lockfile, static assets, build scripts, and an export of the live editions. The live edition export was read from `/api/editions` on 2026-11-19 and includes the current October 2026 archive.

## Before uploading to a new Site

1. Create or select the destination Site, then add its returned `project_id` to `.openai/hosting.json`. Use `.openai/hosting.json.template` as the starting point and retain the `DB` D1 binding.
2. Provision/configure the destination D1 binding and any runtime secrets required by the Site. Set a new `EDITOR_TOKEN` for the destination; do not reuse credentials from the original Site.
3. Import `content/current-production-editions.json` into the destination through its `/api/editions` content flow after deployment. Keep the original month and article IDs to preserve the archive.
4. Install dependencies from `package.json` and `pnpm-lock.yaml`, then build and publish using the new Site's own project settings.

The old `.git` history and old `.openai/hosting.json` identity are intentionally omitted. No Site tokens, Git credentials, environment files, or runtime state are included.
