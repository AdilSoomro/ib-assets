# ib-assets

Royalty-free background-music catalog for the **Imagitor** video editor
(Android/iOS). Serves as an over-the-air music library, same pattern as
[ImagitorBase](https://github.com/AdilSoomro/ImagitorBase) (fonts/templates).

## Contents

- `music_list.json` — the catalog the apps fetch. Font-base-style schema:
  `version`, `categories[]`, and `tracks[]` with `name`, `artist`, `category`,
  `duration` (seconds), `download` (absolute raw URL), `size`, `premium`.
- `music/<category>/<slug>.m4a` — AAC 128 kbps, `+faststart` (streamable for
  in-app previews), cover-art stripped.

## Provenance & license

All tracks are **CC0 1.0 (public domain)** from [FreePD.com](https://freepd.com)
— composers include Kevin MacLeod, Bryan Teoh, Alexander Nakarada and others
(per-track `artist` field preserved from ID3 tags). Files were bulk-sourced from
the community mirror [0lhi/FreePD](https://github.com/0lhi/FreePD) (branch
`stream`), re-encoded from 320 kbps MP3 to 128 kbps M4A for mobile-data-friendly
size. CC0 requires no attribution and permits commercial redistribution.

Source categories `Horror` and `Zoned` (long ambient/loops) were excluded.
Category mapping: Romance→Romantic, Scoring→Cinematic, Comedy→Fun,
Miscellaneous→Misc; Upbeat/Epic/Electronic/World kept as-is.

## Rules

- **Do not use Git LFS** — the apps hotlink `raw.githubusercontent.com` URLs;
  LFS bandwidth is quota-billed, plain git blobs are not.
- Bump `version` in `music_list.json` whenever tracks are added/changed and
  update the cache-buster in ImagitorBase `update-changelog.json` accordingly.
- Regenerate the catalog with the build script rather than hand-editing track
  entries (hand-editing `premium` flags is fine).
