# wplists

Automatically-updated snapshots of the WordPress.org plugin and theme directories, refreshed every 6 hours by [`wpscrapper`](https://github.com/souleater2023/wpscrapper) (private).

## Files

| File | Contents |
|---|---|
| `plugins.json` | Full plugin directory — JSON array of plugin records, sorted by slug, deduped |
| `plugins.txt`  | Unique plugin count (integer) |
| `themes.json`  | Full theme directory — JSON array of theme records, sorted by slug, deduped |
| `themes.txt`   | Unique theme count (integer) |

## Stable URLs

- https://raw.githubusercontent.com/souleater2023/wplists/main/plugins.json
- https://raw.githubusercontent.com/souleater2023/wplists/main/plugins.txt
- https://raw.githubusercontent.com/souleater2023/wplists/main/themes.json
- https://raw.githubusercontent.com/souleater2023/wplists/main/themes.txt

## Record schemas

**Plugin**: `name, slug, version, requires_wordpress, tested, requires_php, num_ratings, active_installs, downloaded, last_updated, added, download_link`

**Theme**: `name, slug, version, author_name, author_url, rating, num_ratings, requires_wordpress, requires_php, preview_url, screenshot_url, homepage, template, is_commercial, is_community`

## Update cadence

Every 6 hours — `00:00`, `06:00`, `12:00`, `18:00` UTC. The commit message records the per-run counts, so `git log plugins.txt` is a clean timeline of directory growth over time.

Counts are computed post-dedup (`[.[].slug] | unique | length`) so they accurately reflect the number of distinct plugins/themes, and the scraper runs multiple `browse=` variants to work around WP.org's unstable default pagination (the default browse mode only exposes ~58k plugins and ~8k themes; the full catalogue is ~63k plugins and ~14.5k themes).
