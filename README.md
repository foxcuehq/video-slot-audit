# video-slot-audit

An agent skill that finds the buyer questions in a category where Google shows a video, and lists who holds each video slot right now: the channel or site, plus the video URL.

Give it a category ("teleprompter app") or a site. It builds 10–20 buyer questions and checks real SERP data for video blocks and for videos linked inside AI Overviews. It then looks up who owns each video and returns dated tables with a short summary. It works from real search data only, and says so when a data source can't see video slots.

## What you need

One of these data sources. The skill documents what each can and can't see:

- a **SERP API** (e.g. SerpApi or DataForSEO) with **your own API key**
- **Ahrefs** (or a similar SEO tool) with API/MCP access, which uses stored SERP snapshots, not live results
- a **manual check** in a private browser window, for a handful of queries

Search Console, Keyword Planner, Trends and YouTube search can't see who holds Google's video slots, so the skill doesn't use them.

## Install

The skill is a folder with a `SKILL.md` file (YAML frontmatter with `name` and `description`, then instructions). Copy the folder into the directory your agent loads skills from:

- **Claude Code:** `~/.claude/skills/` (personal) or `.claude/skills/` in a project
- **Other agents (Codex, Cursor, etc.):** the skills directory your tool's docs specify. Locations differ between tools and versions, so check the current docs.
- **Agents without skill support:** paste `SKILL.md` into the prompt.

```bash
mkdir -p ~/.claude/skills
cp -r video-slot-audit ~/.claude/skills/
```

## Usage

> Run a video slot audit for "teleprompter app", US, 15 questions, using Ahrefs.

> Which "field service software" buyer questions show a video on Google, and who owns those videos? Use my SerpApi key.

See [`examples/teleprompter-app-us.md`](examples/teleprompter-app-us.md) for a real run on Ahrefs data.

## What it isn't

It's a dated snapshot of search results, not a forecast. It doesn't promise that a video will appear, rank or be cited.

## License

MIT. See [LICENSE](LICENSE).

built by an 8-agent team trying to get 100 strangers on a waitlist in 7 days, foxcue.com
