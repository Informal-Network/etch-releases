# Release policy: continuous canary

Mandatory for every Etch repo (owner, 2 Nov 2026, Linear WEA-2767).

Etch releases at any time. Nothing waits for a time gate.

## The rules

1. **No time gates on cutting a release.** There is no cooldown between releases, no release window, no soak that blocks the next cut, no scheduled "release day", and no GitHub environment wait timer. When the change is reviewed and the checks are green, it can ship.
2. **Every release goes out behind a canary.** A new release reaches a small share of installs, users or traffic first, then a wider share, then everyone. Health gates decide each advance: crashes, errors, adoption and halts. A hold inside a canary only decides how fast one release widens. It never stops the next release being cut.
3. **The newest release takes over the canary.** When a newer release is verified, it replaces the release that was ramping and starts its own canary from the first stage. A halted release stays paused.
4. **Fix forward.** A failed health gate halts that release at 0 % and pauses it. The fix goes out as the next release, through the same canary, at once.
5. **Gates that are not about time stay.** Review on every PR, green required checks, signed and verified tags, crash and error gates, adoption gates and halts all still apply. Removing a time gate never removes one of these.

## What this means per kind of repo

- **Shipped clients (desktop app, CLI, MCP server):** releases are cut on demand. The update channel rolls each release out in stages (5 %, 25 %, 100 % for the desktop app) and a newer release supersedes a ramping one.
- **Services (sync server, admin, portal):** deploy on merge to a canary slice, widen on health, and let the next deploy supersede it.
- **Sites and docs (website, docs, brand and design repos):** deploy on merge. A preview deploy is the canary; there is no hold before production.
- **Kits and assets (dither editor, social dither, brand lab, releases):** publish a release whenever its contents change. Consumers pin a version, so a new release is their canary.

## Where it lives

- etch-app: `ops/desktop-release/` (the coordinator) and its README.
- This page is copied into each Etch repo's docs and wiki. Change the policy in all of them together.
