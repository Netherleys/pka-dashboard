# PKA Dashboard — GitHub Pages Mirror (Chromebook target)

This is **not** the source of truth for the PKA Dashboard. The real, live
dashboard lives locally at `Project Build\PKA Dashboard\index.html` inside
the OneDrive-synced `PKA MANAGEMENT` folder, and is what the PC and Win11
laptop use directly via `file://` through the New Tab extension.

This repo exists only because ChromeOS cannot reach that `file://`
location the same way Windows can (see `Project Build\PKA Dashboard\_chrome-newtab-extension\SETUP.md`
for the full investigation) — so the Chromebook's New Tab extension points
here instead, at a hosted `https://` copy.

## What's different about this copy

Built by `PKA-Infra\build_pka_dashboard_mirror.py` from the real
`index.html`, with all hardcoded sensitive/local-only data stripped:
Bookmarks seed data, personal nav-link folders, two Quick Links tiles
(Master Sales Tracker, Owner's/Team Inbox), Team Actions data, and every
`obsidianLog` internal file path. **Bookmarks still work** — they load
live at runtime from the same PkaSync Apps Script backend the PC/laptop
use, same as always. **Team Actions section will be empty on this
mirror** — no sync channel exists yet for that data's content (only for
its dismissed-state), so it isn't included here. Not a bug.

`robots.txt` and a `noindex` meta tag are both in place — this page is
not intended to be discoverable via search, only reachable by a device
that already has the direct URL configured.

## Updating this mirror after a real dashboard edit

This does **not** update automatically — unlike the PC/laptop's `file://`
copy, which always reflects the live file instantly. See the "Chromebook
mirror update workflow" section in
`Project Build\PKA Dashboard\_chrome-newtab-extension\SETUP.md` for the
exact steps.
