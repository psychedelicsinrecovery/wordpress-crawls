# PIR Site Archive — Index

55 pages archived so far (33 main site, 22 service site) — still not full coverage. See
`README.md` in this directory for scope, purpose, and how to extend this.

**2026-09-20 pass — direct-SQL gap fill.** Christopher flagged that several submenu pages
(Meetings, Donate, Blog, Newsletter, etc.) were missing despite being real nav items. Both
`emcp-tools-list-pages` (silently omits some real pages — confirmed missing Meetings/post_id 2,
no error) and `firecrawl_map` (sitemap-only, misses real unlisted pages) had already been shown
unreliable, so this pass instead queried `wp_eup8um_posts` directly
(`SELECT ID, post_title, post_type, post_name FROM wp_eup8um_posts WHERE post_status = 'publish'
AND post_type = 'page'`) — the real WordPress table prefix on this site is `wp_eup8um_`, not the
default `wp_`. That returned all 48 real published pages, the authoritative source of truth this
index is now reconciled against. 8 new pages added: Meetings, Online Meetings, In-Person Meetings,
Blog, Common Prayers, Navigating New Challenges, Donate (`/7th-tradition/`), Public Relations,
Newsletter.

**Real scope, now enumerated (was previously only estimated):** a full `firecrawl_map` of both
sites on 2026-09-20 found **~100 individual blog/series posts** on the main site — not the
"~40" estimated in earlier notes. That map result is the actual complete URL inventory; treat any
older "~40" reference elsewhere as superseded by this count.

## psychedelicsinrecovery.org (main site)

| Page | Local file |
|---|---|
| [Home](https://www.psychedelicsinrecovery.org/) | `psychedelicsinrecovery-org/index.md` |
| [Vision](https://www.psychedelicsinrecovery.org/vision/) | `psychedelicsinrecovery-org/vision.md` |
| [History](https://www.psychedelicsinrecovery.org/history/) | `psychedelicsinrecovery-org/history.md` |
| [12 Steps](https://www.psychedelicsinrecovery.org/12-Steps/) | `psychedelicsinrecovery-org/12-steps.md` |
| [Safety and Ethics](https://www.psychedelicsinrecovery.org/safety-and-ethics/) | `psychedelicsinrecovery-org/safety-and-ethics.md` |
| [Inclusivity and Diversity](https://www.psychedelicsinrecovery.org/inclusivity-and-diversity/) | `psychedelicsinrecovery-org/inclusivity-and-diversity.md` |
| [FAQ](https://www.psychedelicsinrecovery.org/faq/) | `psychedelicsinrecovery-org/faq.md` |
| [Service](https://www.psychedelicsinrecovery.org/service/) | `psychedelicsinrecovery-org/service.md` |
| [Crisis Resources](https://www.psychedelicsinrecovery.org/crisis-resources/) | `psychedelicsinrecovery-org/crisis-resources.md` |
| [Library](https://www.psychedelicsinrecovery.org/library/) | `psychedelicsinrecovery-org/library.md` |
| [About](https://www.psychedelicsinrecovery.org/about/) | `psychedelicsinrecovery-org/about.md` |
| [Book](https://www.psychedelicsinrecovery.org/book/) | `psychedelicsinrecovery-org/book.md` |
| [Our Lineages](https://www.psychedelicsinrecovery.org/our-lineages/) | `psychedelicsinrecovery-org/our-lineages.md` |
| [Member Materials](https://www.psychedelicsinrecovery.org/member-materials/) | `psychedelicsinrecovery-org/member-materials.md` |
| [WhatsApp](https://www.psychedelicsinrecovery.org/whatsapp/) | `psychedelicsinrecovery-org/whatsapp.md` |
| [Contact](https://www.psychedelicsinrecovery.org/contact/) | `psychedelicsinrecovery-org/contact.md` |
| [Privacy Policy](https://www.psychedelicsinrecovery.org/safety-and-ethics/privacy-policy/) | `psychedelicsinrecovery-org/safety-and-ethics/privacy-policy.md` |
| [Need for Safe Spaces](https://www.psychedelicsinrecovery.org/safety-and-ethics/need-for-safe-spaces/) | `psychedelicsinrecovery-org/safety-and-ethics/need-for-safe-spaces.md` |
| [Curious About Integrating Psychedelics?](https://www.psychedelicsinrecovery.org/integrating-psychedelics/) | `psychedelicsinrecovery-org/integrating-psychedelics.md` |
| [Indigenous Lineages](https://www.psychedelicsinrecovery.org/indigenous-lineages/) | `psychedelicsinrecovery-org/indigenous-lineages.md` |
| [2026 PIR® Convention](https://www.psychedelicsinrecovery.org/convention-2026/) | `psychedelicsinrecovery-org/convention-2026.md` |
| [Convention Program update](https://www.psychedelicsinrecovery.org/convention-program/) | `psychedelicsinrecovery-org/convention-program.md` |
| [Happy Birthday Albert Hofmann!](https://www.psychedelicsinrecovery.org/happy-birthday-albert-hofmann/) | `psychedelicsinrecovery-org/happy-birthday-albert-hofmann.md` |
| [Website Re-Launch](https://www.psychedelicsinrecovery.org/website-re-launch/) | `psychedelicsinrecovery-org/website-re-launch.md` |
| [Resources](https://www.psychedelicsinrecovery.org/resources/) | `psychedelicsinrecovery-org/resources.md` |
| [Meetings *ALL*](https://www.psychedelicsinrecovery.org/meetings/) | `psychedelicsinrecovery-org/meetings.md` |
| [Online Meetings](https://www.psychedelicsinrecovery.org/meetings/online-meetings/) | `psychedelicsinrecovery-org/meetings/online-meetings.md` |
| [In-Person Meetings](https://www.psychedelicsinrecovery.org/meetings/in-person-meetings/) | `psychedelicsinrecovery-org/meetings/in-person-meetings.md` |
| [Blog](https://www.psychedelicsinrecovery.org/blog/) | `psychedelicsinrecovery-org/blog.md` |
| [Common Prayers](https://www.psychedelicsinrecovery.org/common-prayers/) | `psychedelicsinrecovery-org/common-prayers.md` |
| [Navigating New Challenges](https://www.psychedelicsinrecovery.org/navigating-new-challenges/) | `psychedelicsinrecovery-org/navigating-new-challenges.md` |
| [Donate (7th Tradition)](https://www.psychedelicsinrecovery.org/7th-tradition/) | `psychedelicsinrecovery-org/7th-tradition.md` |
| [Public Relations](https://www.psychedelicsinrecovery.org/public-relations/) | `psychedelicsinrecovery-org/public-relations.md` |
| [De Vine Newsletter](https://www.psychedelicsinrecovery.org/newsletter/) | `psychedelicsinrecovery-org/newsletter.md` |

**`/Resources` — corrected, the earlier "does not exist" note was wrong.** It's a real, published
page (WordPress `post_id: 24`, slug `resources`, permalink matches exactly) — confirmed directly via
`emcp-tools-get-post`, not a crawler. It's simply **not in the XML sitemap `firecrawl_map` reads**,
so the earlier full-site map missed it even though it's live. Now archived above.

**Pattern worth carrying into the next pass:** since one page turned out to be real despite being
sitemap-invisible, `firecrawl_map`'s output should be treated as *sitemap coverage*, not *full site
coverage*. `/convention-2026-schedule` below is the other page hitting this same gap — checking it
via `emcp-tools` (`list-pages` or a direct `get-post` if the ID is known) rather than another
`firecrawl_map` attempt is the more reliable next step.

**`/convention-2026-schedule`** — still unresolved. Linked from both `/convention-2026` and
`/convention-program`'s content (as "coming soon" / a "View Full Schedule" link), but absent from
`firecrawl_map`'s output — likely the same sitemap-visibility gap `/Resources` just turned out to
have, not evidence it's actually missing. Check via `emcp-tools` directly, not another map attempt.

**Not yet archived — ~96 individual posts remain**, out of the ~100 the full site map found. This
pass archived 2 of them (Happy Birthday Albert Hofmann, Website Re-Launch) plus both real convention
pages, prioritized for their announcement/event value. The bulk of what's left falls into a few
clear clusters, useful for whoever picks this up next to work through by theme rather than
alphabetically:

- **The "10 Different Models of Psychedelic Integration" series** — 10 numbered parts
  (`/visionary-plant-medicine-integration-by-coder...` through
  `/10-the-nature-relatedness-model-by-gandy-et-al-2020...`), plus its series-intro post
  `/the-diversity-of-psychedelic-integration-models-a-journey-through-10-unique-approaches`.
- **The "Hero's Journey" series** — ~13 stage posts (`/stage-one-the-ordinary-world...` through
  `/stage-twelve-return-with-the-elixir...`, plus `/meeting-the-mentor-...`), mapping the psychedelic
  recovery experience to Campbell's hero's-journey structure.
- **AA/Bill Wilson psychedelic history** — a cluster of ~15 posts on Bill Wilson's LSD experiments,
  the Oxford Group, early AA meetings, Ibogaine, MK-Ultra-adjacent history, etc. (e.g.
  `/bill-wilson-a-letter-discussing-lsd-therapy`, `/the-narcotics-farm-of-lexington-...`,
  `/the-first-treatment-program-to-use-lsd-and-aa`).
- **Personal stories / essays** — ~15 first-person posts (e.g.
  `/i-take-psychedelic-drugs-and-im-in-recovery`, `/a-mothers-fear-...`,
  `/rejected-by-my-aa-community-...`, `/the-untethered-journey-scotts-story-...`).
- **Book reviews and miscellaneous essays** — the remainder (~30-40 posts), covering topics from
  DMT types to Thanksgiving/indigenous-tradition reflections to tradition-10 commentary.

Also not yet archived: `/meetings/in-person-meetings-2` (a real content page, not a blog post —
missed by earlier passes' page-vs-post triage, worth catching next time).

**Resolved this pass, from the authoritative 48-page SQL list:**
- **"Privacy Policy" (post_id 3, slug `privacy-policy`) is NOT a duplicate.** Its real permalink,
  confirmed via `emcp-tools-get-post`, is `/safety-and-ethics/privacy-policy/` — same page already
  archived at `psychedelicsinrecovery-org/safety-and-ethics/privacy-policy.md`. WordPress's flat
  `post_name` field doesn't show the parent-page path, which is what made it look like a second,
  root-level page in the raw SQL output.
- **`/notifications/` is a 301 redirect, not a page.** Confirmed via
  `wp_eup8um_redirection_items`: `/notifications/` → `/subscribe-general/` (the Brevo email
  signup form). Linked from both Meetings and Online Meetings as "sign up for the weekly digest" —
  not archived separately since it has no content of its own.
- **"Announcements" is still unresolved.** Linked from Public Relations
  (`/announcements/`) but absent from the 48-page list — likely a category/tag archive of
  `post`-type content, not a standalone page. Needs direct verification, not assumption.
- **"Events" is confirmed NOT a page** — it's the `tribe_events` custom post type (The Events
  Calendar plugin), via `emcp-tools-list-post-types`. Needs a `list-posts`/`query` call with
  `post_type=tribe_events` to enumerate, not `get-post`. Not yet archived.

**Also found in the 48-page list, not yet archived (lower priority, utility/legacy pages):**
Common Prayers, Navigating New Challenges, Donate, Public Relations, and Newsletter are now done
(above). Still open: Legacy article-style pages `1950s Psychedelic Research in Addictions`
(post_id 9975), `12-steps From AA to Psychedelics in Recovery` (9977, likely a near-duplicate of
the already-archived `12-steps.md` — check before archiving), `Harm Reduction over pure
Abstinence` (9981), `Clinical Advances in Trauma work` (9984), `From Phantasticants to Entheogens`
(10089). Utility/form pages intentionally skipped as low-value for full-content archiving: Thank
you (241), Submitpost (9143), ThemeNcode PDF Viewer ×2 (9880, 9881, plugin infrastructure), Search
(12891), 5 Private Meeting Subscribe pages (Zoom-registration forms), 2 Subscribe General pages
(488, 12067, the Brevo signup form `/notifications/` redirects to), In-Person-2 Elementor draft
(11983).

The full raw URL list this pass's `firecrawl_map` call returned is not re-saved anywhere separately
— re-run `firecrawl_map` on `https://www.psychedelicsinrecovery.org` (limit 300) to regenerate it
rather than assuming this index's prose summary above is exhaustive down to the individual URL.

## service.psychedelicsinrecovery.org (service site)

| Page | Local file |
|---|---|
| [Service Home](https://service.psychedelicsinrecovery.org/) | `service-psychedelicsinrecovery-org/index.md` |
| [501 Board](https://service.psychedelicsinrecovery.org/board/) | `service-psychedelicsinrecovery-org/board.md` |
| [Board of Directors](https://service.psychedelicsinrecovery.org/board-of-directors/) | `service-psychedelicsinrecovery-org/board-of-directors.md` |
| [Tech Committee](https://service.psychedelicsinrecovery.org/tech-committee/) | `service-psychedelicsinrecovery-org/tech-committee.md` |
| [Literature Committee](https://service.psychedelicsinrecovery.org/literature-committee/) | `service-psychedelicsinrecovery-org/literature-committee.md` |
| [PR Committee](https://service.psychedelicsinrecovery.org/pr-committee/) | `service-psychedelicsinrecovery-org/pr-committee.md` |
| [Book Committee](https://service.psychedelicsinrecovery.org/book-committee/) | `service-psychedelicsinrecovery-org/book-committee.md` |
| [GSR Committee](https://service.psychedelicsinrecovery.org/gsr-committee/) | `service-psychedelicsinrecovery-org/gsr-committee.md` |
| [GSR](https://service.psychedelicsinrecovery.org/gsr/) | `service-psychedelicsinrecovery-org/gsr.md` |
| [Finance](https://service.psychedelicsinrecovery.org/finance/) | `service-psychedelicsinrecovery-org/finance.md` |
| [Committees (index)](https://service.psychedelicsinrecovery.org/committees/) | `service-psychedelicsinrecovery-org/committees.md` |
| [Contact](https://service.psychedelicsinrecovery.org/contact/) | `service-psychedelicsinrecovery-org/contact.md` |
| [12 Step Committee](https://service.psychedelicsinrecovery.org/12-step-committee/) | `service-psychedelicsinrecovery-org/12-step-committee.md` |
| [Convention Committee](https://service.psychedelicsinrecovery.org/convention-committee/) | `service-psychedelicsinrecovery-org/convention-committee.md` |
| [Intergroup](https://service.psychedelicsinrecovery.org/intergroup/) | `service-psychedelicsinrecovery-org/intergroup.md` |
| [Tech](https://service.psychedelicsinrecovery.org/tech/) | `service-psychedelicsinrecovery-org/tech.md` |
| [Former Committees](https://service.psychedelicsinrecovery.org/former-committees/) | `service-psychedelicsinrecovery-org/former-committees.md` |
| [About (demo placeholder)](https://service.psychedelicsinrecovery.org/about-2/) | `service-psychedelicsinrecovery-org/about-2.md` |
| [Committee Emails and Setup](https://service.psychedelicsinrecovery.org/committee-email/) | `service-psychedelicsinrecovery-org/committee-email.md` |
| [Services (demo placeholder)](https://service.psychedelicsinrecovery.org/services/) | `service-psychedelicsinrecovery-org/services.md` |
| [ForaPIR](https://service.psychedelicsinrecovery.org/forapir/) | `service-psychedelicsinrecovery-org/forapir.md` |
| [Service Structure Working Group](https://service.psychedelicsinrecovery.org/service-structure-working-group/) | `service-psychedelicsinrecovery-org/service-structure-working-group.md` |

**Former-committee sub-pages — actually resolved, an earlier pass's note here was confused.**
Christopher confirmed directly: the pages reached from the "Former Committees" submenu are
**Intergroup, Service Structure Working Group, ForaPIR, and 12 Step Committee** — all four are
already in the table above, archived in an earlier pass. A later pass's `firecrawl_map` sweep found
"zero additional URLs" and mistakenly read that as an open gap, without recognizing the pages it was
looking for were the ones already sitting in this same index a few rows up. No further work needed
here.

**New pages found this pass, not yet archived:** `/literature` (distinct from "Literature
Committee" — worth checking whether it's a duplicate or genuinely different content before
archiving both), `/calendar-service`, `/first-test-forapir-blog-post` (a real, if minor, blog post),
`/service-calendar` (a redirect stub pointing to `/calendar-service`, probably not worth archiving
as its own file), `/demo-page` and `/sample-page` (WordPress/theme demo placeholders, Lorem-ipsum,
same category as the already-archived `about-2`/`services` stubs).

Note: `about-2` and `services` are unfinished WordPress theme-demo placeholder pages (Lorem-ipsum
filler content, not real PIR copy) — archived as-is for completeness; flagged in each file.
