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

## Status as of 2026-09-20

**Second pass, still not full coverage.** 42 pages archived — 20 on the main site (core
identity/values pages plus About, Book, Our Lineages, Member Materials, WhatsApp, Contact, Privacy
Policy, Need for Safe Spaces, Integrating Psychedelics, Indigenous Lineages) and 22 on the service
site (Home, Board, and nearly all committee/governance pages: Board of Directors, Tech, Literature,
PR, Book, GSR (both `/gsr` and `/gsr-committee`), Finance, Committees index, Contact, 12-Step,
Convention, Intergroup, Former Committees, Committee Emails, ForaPIR, Service Structure Working
Group, plus two unfinished theme-demo placeholder pages, `about-2` and `services`, flagged as such
in their files). Not yet archived: convention pages (`/convention-2026*`), ~40+ individual blog
posts on the main site, and the individual "former committee" sub-pages linked from a submenu on
the service site. The `/Resources` page referenced in earlier notes could not be found under any
checked slug and may be stale. See `INDEX.md`'s "Not yet archived" notes for specifics.

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
