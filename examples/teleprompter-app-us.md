# Video slot audit: "teleprompter app" buyer questions (US)

A real run of the `video-slot-audit` process. Nothing here is estimated or filled in. Every row comes from the Ahrefs responses described below.

**Data source:** Ahrefs API v3 via the Ahrefs MCP connector, pulled 2026-10-24 about 09:58 EDT (America/Toronto):
- `keywords-explorer-matching-terms`: `keywords="teleprompter app"`, `country=us`, `match_mode=terms`, `order_by=volume:desc`, `limit=15`, columns `keyword, volume, serp_features, serp_last_update, intents`
- `serp-overview`: `country=us`, columns `position, type, url, title, update_date`, for 5 of the keywords (section 2)

**Important:** Ahrefs returns stored SERP snapshots, not live results. Each keyword's snapshot has its own date (shown below, converted to EDT). Some are several weeks old.

**Owner lookup:** YouTube public oEmbed endpoint (`https://www.youtube.com/oembed?url=…&format=json`, fields `author_name`, `author_url`), run 2026-10-24 09:59 EDT. All 8 lookups succeeded.

**Questions checked:** 15 · **With a video block (`video` flag):** 13 · **No video flag:** 1 · **No SERP data:** 1

## 1. Questions and video presence

How to read the flags (Ahrefs' raw labels):
- `video` = a video result position on the SERP (a video block/carousel). This is the "Video block" column.
- `ai_overview` = the SERP has an AI Overview.
- `video_th` = a video thumbnail. In the SERP overviews pulled below, it appeared on AI Overview links pointing to YouTube videos. That makes it the closest keyword-level signal for "video in the AI Overview", but the keyword-level flag alone doesn't prove it. Section 2 checks it at the URL level for 5 questions.

| # | Question | US volume (Ahrefs) | Video block | `video_th` flag | AI Overview | Raw `serp_features` | SERP snapshot (EDT) |
|---|---|---|---|---|---|---|---|
| 1 | teleprompter app | 5,400 | yes | no | yes | `ai_overview`, `ai_overview_sitelink`, `image_th`, `question`, `sitelink`, `video` | 2026-10-17 15:47 |
| 2 | free teleprompter app | 2,300 | yes | yes | yes | `ai_overview`, `ai_overview_sitelink`, `video_th`, `image_th`, `question`, `sitelink`, `video` | 2026-10-02 06:03 |
| 3 | teleprompter app for iphone | 1,200 | yes | no | yes | `ai_overview`, `ai_overview_sitelink`, `image_th`, `question`, `sitelink`, `video` | 2026-10-23 11:42 |
| 4 | teleprompter app for mac | 600 | yes | no | yes | `ai_overview`, `ai_overview_sitelink`, `image_th`, `sitelink`, `question`, `video` | 2026-10-08 09:38 |
| 5 | best teleprompter app | 600 | yes | yes | yes | `ai_overview`, `ai_overview_sitelink`, `image_th`, `video_th`, `video`, `question`, `discussion`, `sitelink` | 2026-10-22 02:45 |
| 6 | teleprompter app free | 450 | no | no | yes | `ai_overview`, `ai_overview_sitelink`, `image_th`, `question` | 2026-09-10 21:48 |
| 7 | best teleprompter app for iphone | 400 | no | no | yes | `ai_overview`, `ai_overview_sitelink`, `image_th`, `question`, `sitelink`, `discussion` | 2026-09-17 12:17 |
| 8 | free teleprompter app for iphone | 400 | yes | no | yes | `ai_overview`, `ai_overview_sitelink`, `sitelink`, `question`, `video` | 2026-10-12 22:46 |
| 9 | teleprompter app for ipad | 350 | yes | no | yes | `ai_overview`, `question`, `sitelink`, `video` | 2026-10-01 23:16 |
| 10 | best free teleprompter app | 350 | yes | yes | yes | `ai_overview`, `ai_overview_sitelink`, `image_th`, `video_th`, `question`, `video`, `sitelink` | 2026-10-24 01:23 |
| 11 | teleprompter app for windows | 300 | yes | yes | yes | `ai_overview`, `ai_overview_sitelink`, `image_th`, `video_th`, `question`, `video` | 2026-10-12 13:48 |
| 12 | ipad teleprompter app | 250 | yes | no | yes | `ai_overview`, `ai_overview_sitelink`, `image_th`, `question`, `sitelink`, `video` | 2026-10-05 04:44 |
| 13 | best teleprompter app for ipad | 200 | yes | yes | yes | `ai_overview`, `ai_overview_sitelink`, `video_th`, `image_th`, `question`, `video`, `discussion`, `sitelink` | 2026-09-29 03:29 |
| 14 | teleprompter app for android | 200 | yes | yes | yes | `ai_overview`, `ai_overview_sitelink`, `image_th`, `video_th`, `video`, `question`, `sitelink` | 2026-10-02 06:54 |
| 15 | macbook teleprompter app | 200 | n/a | n/a | n/a | none returned (no SERP data) | n/a |

Note: row 1 has no `video_th` flag, but its SERP overview still lists a YouTube URL among the AI Overview links (flagged `image_th` there). See section 2. Keyword-level flags can miss what the full SERP shows.

## 2. Who holds each video slot (5 SERPs pulled in full)

"Video block" = positions with type `video`. "AI Overview link" = positions with type `ai_overview_sitelink` whose URL is a YouTube video. Where the same video appeared twice in one AI Overview (with and without a `&t=` timestamp), it's listed once.

| Question | Slot | Position | Video URL (as returned) | Title (as returned) | Owner (oEmbed `author_name`) | Snapshot (EDT) |
|---|---|---|---|---|---|---|
| teleprompter app | Video block | 9 | https://www.youtube.com/watch?v=Oy-bKu-54Ts | Best Teleprompter Apps For iPhone & Android in 2026 | Justin Brown - Primal Video (@PrimalVideo) | 2026-10-17 15:47 |
| teleprompter app | Video block | 9 | https://www.youtube.com/watch?v=bH2RUCSMbio&vl=en | BEST FREE Teleprompter App For YouTube Videos (Mobile & ... | Entrepreneur Nut (@entrepreneurnut) | 2026-10-17 15:47 |
| teleprompter app | AI Overview link (`image_th`) | 1 | https://www.youtube.com/watch?v=AFw-cO8qsEM | Best 100% free teleprompter app with voice scrolling in 2026 just got better | Konstantin Suvorov (@kosuvorov) | 2026-10-17 15:47 |
| best teleprompter app | Video block | 4 | https://www.youtube.com/watch?v=Oy-bKu-54Ts | Best Teleprompter Apps For iPhone & Android in 2026 | Justin Brown - Primal Video (@PrimalVideo) | 2026-10-22 02:45 |
| best teleprompter app | AI Overview link (`video_th`) | 1 | https://www.youtube.com/watch?v=0-FZ00E05ww&vl=en&t=52 | BEST FREE Teleprompter Apps in 2026 (Plus How To Use) | Ken Ang Wee Kien (@kenangwk) | 2026-10-22 02:45 |
| free teleprompter app | Video block | 8 | https://www.youtube.com/watch?v=Oy-bKu-54Ts | Best Teleprompter Apps For iPhone & Android in 2026 | Justin Brown - Primal Video (@PrimalVideo) | 2026-10-02 06:03 |
| free teleprompter app | Video block | 8 | https://www.youtube.com/watch?v=bH2RUCSMbio&vl=en | BEST FREE Teleprompter App For YouTube Videos (Mobile & ... | Entrepreneur Nut (@entrepreneurnut) | 2026-10-02 06:03 |
| free teleprompter app | AI Overview link (`video_th`) | 1 | https://www.youtube.com/watch?v=0-FZ00E05ww&vl=en&t=52 | BEST FREE Teleprompter Apps in 2026 (Plus How To Use) | Ken Ang Wee Kien (@kenangwk) | 2026-10-02 06:03 |
| free teleprompter app | AI Overview link (`video_th`) | 1 | https://www.youtube.com/watch?v=Oy-bKu-54Ts&t=2 | Best Teleprompter Apps For iPhone & Android in 2026 | Justin Brown - Primal Video (@PrimalVideo) | 2026-10-02 06:03 |
| free teleprompter app | AI Overview link (`video_th`) | 1 | https://www.youtube.com/watch?v=AFw-cO8qsEM&t=79 | Best 100% free teleprompter app with voice scrolling in 2026 just got better | Konstantin Suvorov (@kosuvorov) | 2026-10-02 06:03 |
| best free teleprompter app | Video block | 6 | https://www.youtube.com/watch?v=Oy-bKu-54Ts | Best Teleprompter Apps For iPhone & Android in 2026 | Justin Brown - Primal Video (@PrimalVideo) | 2026-10-24 01:23 |
| best free teleprompter app | Video block | 6 | https://www.youtube.com/watch?v=bH2RUCSMbio&vl=en | BEST FREE Teleprompter App For ... | Entrepreneur Nut (@entrepreneurnut) | 2026-10-24 01:23 |
| best free teleprompter app | AI Overview link (`video_th`) | 1 | https://www.youtube.com/watch?v=AFw-cO8qsEM&t=79 | Best 100% free teleprompter app with voice scrolling in 2026 just got better | Konstantin Suvorov (@kosuvorov) | 2026-10-24 01:23 |
| best free teleprompter app | AI Overview link (`video_th`) | 1 | https://www.youtube.com/watch?v=0-FZ00E05ww&vl=en&t=52 | BEST FREE Teleprompter Apps in 2026 (Plus How To Use) | Ken Ang Wee Kien (@kenangwk) | 2026-10-24 01:23 |
| teleprompter app for windows | Video block | 4 | https://www.youtube.com/watch?v=UiBBWJhkcWY | The Best Virtual Teleprompter for Windows!!? | myteamslab (@myteamslab) | 2026-10-12 13:48 |
| teleprompter app for windows | Video block | 4 | https://www.youtube.com/watch?v=ghFjcZ4HiZg | How To Turn Your Computer Into A Teleprompter | Riverside (@Riversidefm) | 2026-10-12 13:48 |
| teleprompter app for windows | AI Overview link (`video_th`) | 1 | https://www.youtube.com/watch?v=vbh1L8y4beE&t=24 | How to use Microsoft Word as a Teleprompter for free | Jeremy Chapman (@DeployJeremy) | 2026-10-12 13:48 |
| teleprompter app for windows | AI Overview link (`image_th`) | 1 | https://www.youtube.com/watch?v=-Q-huchwCS4 | Teleprompter for Mac & Windows - Speakflow Desktop | Speakflow (@speakflow) | 2026-10-12 13:48 |

All video URLs in these 5 SERPs were on youtube.com. No non-YouTube video host appeared.

## 3. Summary (tallied from the tables above)

- 13 of 15 questions have a `video` (video block) flag. 1 has none ("teleprompter app free"); 1 has no SERP data ("macbook teleprompter app").
- All 5 full SERPs pulled have both a video block and at least one YouTube video among the AI Overview links.
- **Justin Brown - Primal Video**, video `Oy-bKu-54Ts`, holds a video-block slot on 4 of 5 SERPs. All four are the general queries; it isn't on "teleprompter app for windows". It's also an AI Overview link on "free teleprompter app".
- **Entrepreneur Nut**, video `bH2RUCSMbio`, holds a video-block slot on 3 of 5.
- **Ken Ang Wee Kien**, video `0-FZ00E05ww`, is an AI Overview link on 3 of 5 ("best", "free", "best free").
- **Konstantin Suvorov**, video `AFw-cO8qsEM`, is an AI Overview link on 3 of 5 ("teleprompter app", "free", "best free").
- "teleprompter app for windows" has a different set of owners: myteamslab and Riverside in the video block; Jeremy Chapman and Speakflow among the AI Overview links.
- The video blocks returned at most 2 video positions each, at organic positions 4–9.

## Limitations

- **Stored snapshots, not live SERPs.** Snapshot dates range from 2026-09-10 to 2026-10-24 (EDT). Today's live results may differ.
- **One location.** US, Ahrefs' default device and language. No mobile/desktop split was requested.
- **Small sample.** 15 keyword ideas from one seed term, sorted by volume. Only 5 SERPs were pulled in full. The other 10 were checked by flag only, so owners for those aren't listed.
- **Label mapping is mine.** I treat `video` as the video block, and `ai_overview_sitelink` with a YouTube URL as a video in the AI Overview, based on the type labels Ahrefs returned. Ahrefs may show fewer carousel items than a browser would (2 per block here).
- **Owner = oEmbed `author_name`.** These are the channels that uploaded the videos. This audit doesn't check any affiliation between a channel and an app.
- Ahrefs usage: 1 keyword-ideas call (15 rows) and 5 SERP-overview calls.
