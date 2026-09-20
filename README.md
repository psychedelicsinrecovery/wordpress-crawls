# PIR Site Archive

A Markdown archive of both PIR WordPress sites, for three purposes: (1) self-serve context for the
agent fleet without needing live WordPress access, (2) a rebuild-from-scratch source if WordPress
hosting is ever lost, (3) a content backup.

**Format decision:** plain Markdown, not `.tsx`/React — this repo isn't a frontend framework
project, so introducing a build toolchain here would add complexity with no rendering benefit. What
mattered was organization: directories mirror each site's actual URL structure, every page carries
`url`/`title`/`crawl_date` frontmatter so it's self-describing on its own, and `INDEX.md` +
`index.json` tie it all together — human-readable and machine-readable respectively.

## Structure

```
site-archive/
  README.md          — this file
  INDEX.md            — human-readable table of contents
  index.json           — machine-readable: {site, url, path, title, crawl_date}[]
  psychedelicsinrecovery-org/          — main site, one .md per page, named by URL slug
  service-psychedelicsinrecovery-org/  — service site, same pattern
```

## Status as of 2026-09-20 (fifth pass — direct-SQL gap fill)

**Still not full coverage — but the real scope is now known, not just estimated.** 55 pages
archived — 33 on the main site (core identity/values pages, About, Book, Our Lineages, Member
Materials, WhatsApp, Contact, Privacy Policy, Need for Safe Spaces, Integrating Psychedelics,
Indigenous Lineages, both real convention pages, Resources, Meetings + its 2 sub-pages (Online,
In-Person), Blog, Common Prayers, Navigating New Challenges, Donate, Public Relations, Newsletter,
and 2 representative blog posts) and 22 on the service site (Home, Board, and nearly all
committee/governance pages).

This pass was triggered by Christopher noticing real submenu pages (Meetings, Donate, Blog,
Newsletter, etc.) were missing despite `emcp-tools-list-pages` and `firecrawl_map` both having been
used already. Both tools turned out to be unreliable for full enumeration: `list-pages` silently
omits some real pages (confirmed missing post_id 2, "Meetings," with no error), and `firecrawl_map`
only sees what's in the XML sitemap. The fix was going straight to the database:
`emcp-tools-query` against `wp_eup8um_posts` (the real table prefix on this site — not the default
`wp_`, found via `emcp-tools-list-tables`) returned all 48 real published pages directly, no
sitemap or crawler gaps possible. That list is now the authoritative source of truth this archive
is reconciled against — see `INDEX.md` for exactly what's resolved and what's still open
(`/announcements/` and `/events/` in particular are real nav items but not simple pages — see
`INDEX.md` for why).

A third pass ran a full `firecrawl_map` of both entire sites and found the main site actually has
**~100 individual blog/series posts**, not the "~40" earlier passes estimated — that number is now
corrected everywhere it appears. That pass also got two things wrong, both corrected in this pass:
it reported `/Resources` as not existing, when direct verification via `emcp-tools-get-post` found
it's real and published (WordPress `post_id: 24`) — just absent from the XML sitemap
`firecrawl_map` reads, so a crawler alone can miss a real page. It also treated the service site's
"former committee" sub-pages as unresolved, without recognizing those pages (Intergroup, Service
Structure Working Group, ForaPIR, 12 Step Committee) were already archived in an earlier pass —
Christopher confirmed the exact names directly. **Lesson for future passes:** when `firecrawl_map`
reports zero results, that means zero results *in the sitemap* — verify against `emcp-tools`
directly before concluding a page doesn't exist.

**Not yet archived:** ~96 of the ~100 main-site blog/series posts (grouped by theme in `INDEX.md`
for whoever picks this up next — a "10 Models of Integration" series, a "Hero's Journey" series, an
AA/Bill-Wilson-history cluster, personal stories, and book reviews/essays); `/convention-2026-schedule`
specifically (linked from two pages but absent from the sitemap — check via `emcp-tools` directly,
not another map attempt, per the lesson above); the service site's `/literature`, `/calendar-service`,
and `/first-test-forapir-blog-post`.
See `INDEX.md` for the full, current breakdown — it supersedes this summary if the two ever drift.

## How to extend this

Firecrawl MCP tools were used — `firecrawl_map` first (cheap, enumerates URLs without fetching
content) to get each site's real URL inventory, then `firecrawl_scrape` per page
(`onlyMainContent: true`, `formats: ["markdown"]`) since the batch `firecrawl_crawl` endpoint was
rate-limited (429) throughout this session even though single-page `firecrawl_scrape` worked fine.
The account's actual per-minute cap turned out to be ~11 requests/min (found empirically, not
documented) — pace scrape calls accordingly, in batches of ~10 with a pause between.

To add a page: scrape it, write the result as a new `.md` file in the right site's directory (named
by URL slug, frontmatter block first), then add its row to `INDEX.md` and its entry to `index.json`.

To refresh a page that's changed on the live site: same process, overwrite the existing file, update
its `crawl_date`.
