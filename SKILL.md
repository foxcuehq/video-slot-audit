---
name: video-slot-audit
description: Audit which buyer questions in a category or for a site show a video result on Google (a video block/carousel, or a video linked inside the AI Overview), and who holds each video slot right now (channel or site, plus video URL). Uses only real SERP data from a SERP API, an SEO tool such as Ahrefs, or a manual check, and records the source and date of every row. Use when someone asks where video shows up in search for their market, who owns those video results, or which questions are worth a video.
---

# Video slot audit

Find the buyer questions where Google shows a video, and record who holds each video slot today. Every row in the output comes from a SERP snapshot you actually pulled, with its date. If you can't see the SERP, you don't report it.

This is a snapshot of what search results showed on given dates. SERPs change often and vary by location, device and personalization. Don't present the audit as a forecast, and don't promise that any video will appear or rank.

## Inputs

- **Required:** a category (e.g. "teleprompter app", "field service software") or a site (e.g. `example.com`).
- **Optional:** country (default US), language (default English), number of questions (default 10–20), and known competitors.

## Data options (pick one; say which you used)

Video slots are a SERP-level fact, so you need a source that records the actual results page. Check the provider's current docs, because field names change.

| Method | Can it see video slots? | What you need | Notes |
|---|---|---|---|
| **SERP API** (e.g. SerpApi, DataForSEO SERP API, or similar) | Yes, if the provider returns video blocks and AI Overview references with URLs. Many do; check the docs for the video and AI Overview fields. | **Your own API key** and usually a paid plan. | Live or near-live results for the location you set. Store the raw JSON and request time. Some providers need a second request to expand AI Overview references. |
| **Ahrefs** (web app, API v3, or MCP) | Yes, from stored snapshots. Keyword tools report SERP feature flags per keyword (`video`, `video_th`, `ai_overview`, `ai_overview_sitelink`, …). The SERP overview returns each position's `type`, `url`, `title` and `update_date`, so YouTube URLs in the video block or among AI Overview links are visible. | An Ahrefs plan with API/MCP access. Calls use API units. | **Not live**: each keyword's snapshot has its own date (`serp_last_update` / `update_date`), often days or weeks old. Doesn't return the YouTube channel name, so resolve it separately (see step 5). |
| **Other SEO suites** (e.g. Semrush, SE Ranking, or similar) | Often a SERP-feature flag ("video", "AI Overview"). Some don't show which URL holds the slot. | Your own account. | Use one only if it exposes the video URL. A bare flag tells you a slot exists, not who owns it. |
| **Manual check** | Yes, for that one moment and place. | A browser, logged out or in a private window, with location set (e.g. `&gl=us&hl=en`). | Slow, and results are personalized and location-dependent. Record the date, time, location and device, and save a screenshot per query. Keep it to a handful of queries. |

**Methods that can't see Google video slots. Don't use them for this:**
- Google Search Console shows only your own site's appearances, never who holds other slots.
- Google Keyword Planner and Google Trends have no SERP layout data.
- YouTube search shows YouTube's own ranking, not Google's results page.
- An LLM's memory or a chatbot's answer isn't a SERP.
- Automated scraping of Google outside an API is against Google's terms. Use a SERP API instead.

If none of the usable methods is available, stop and say so. Don't produce a table.

## Process

1. **Build the buyer-question list (10–20).** Start from the category term or the site's main product terms. Add buyer modifiers: "best …", "free …", "… for <platform/industry>", "… vs …", "… alternative", "how to … with …", "is … worth it". Prefer real keyword data (a keyword tool's matching terms or questions) over guessing. Record where each question came from. Keep the list modest so API usage stays small.
2. **Pull SERP features for each question.** Record the feature list and the snapshot date for each keyword. If a keyword has no SERP data, mark it `n/a (no SERP data)`. Never assume.
3. **Mark video presence**, exactly as the data shows it:
   - `video block`: a SERP position whose type is video (a video carousel or pack).
   - `video in AI Overview`: a video URL (usually `youtube.com/watch`) among the AI Overview's linked sources, or a video-thumbnail flag attached to an AI Overview link.
   - Report the provider's raw labels too, so readers can check your mapping.
4. **Pull the full SERP for the questions with video.** Do this for all of them, or the highest-volume 5–10 if budget is tight. For every video slot, record the position, the slot type, the video URL as returned, the title as returned, and the snapshot date.
5. **Resolve owners.** For YouTube URLs, look up the channel through YouTube's public oEmbed endpoint (`https://www.youtube.com/oembed?url=<video URL>&format=json`, fields `author_name` and `author_url`) or the YouTube Data API with your own key. For other hosts, the owner is the site/domain. If the lookup fails, write `owner: n/a`; don't guess from the title.
6. **Summarize.** Count how many questions show any video, and which channels or sites hold the most slots across the set. Only state counts you can tally from the table.
7. **Self-check** (below), then return.

## Output format

```markdown
# Video slot audit: <category or site> (<country>)

**Data source:** <tool + endpoint/report>, pulled <date/time + zone>. SERP snapshot dates per row.
**Owner lookup:** <method>, run <date/time + zone>
**Questions checked:** <n> · **With any video:** <n> · **No SERP data:** <n>

## 1. Questions and video presence
| # | Question | Volume (if available) | Video block | Video in AI Overview | Raw feature flags | SERP snapshot date |

## 2. Who holds each video slot
| Question | Slot | Position | Video URL | Title (as returned) | Owner (channel/site) | Snapshot date |

## 3. Summary
- <counts tallied from the table, e.g. "Channel X holds a video-block slot on 4 of 5 SERPs checked">

## Limitations
- <snapshot age, location, sample size, label mapping, anything not checked>
```

## Rules

- **Real data only.** Every row traces to a pull you made, with its date. Never fill a row from memory, a likely guess, or an example.
- **Report what the data shows.** Use the provider's labels and explain your mapping. If the provider can't tell carousel from single video, or AI Overview citation from thumbnail, say so.
- **Dates on everything.** Snapshot dates vary per keyword in stored-SERP tools. Show them, and convert to the reader's time zone if you give times.
- **No promises.** Don't claim a video will get a slot, get cited, or rank. Don't describe the audit as a ranking or citation strategy. It's an observation of current results.
- **Owner = what the data or lookup returns.** No inferring brand affiliations or relationships between channels and products.
- **Keep usage modest.** 10–20 questions, full SERPs only for those with video.

## Self-check

- [ ] Data source, endpoint/method and pull date are stated.
- [ ] Every question row has a snapshot date or `n/a`.
- [ ] Every video slot has a URL and snapshot date taken from the raw response. Spot-check 3 against the saved output.
- [ ] Every owner came from a lookup; failed lookups say `n/a`.
- [ ] Summary counts match the table when recounted.
- [ ] Limitations list snapshot age, location, sample size and label mapping.
- [ ] No ranking, citation or traffic promises anywhere.
