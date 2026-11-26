# MCPL Book Recommender

An independent, general-purpose Agent Skill for discovering books for adults, teens and children using multiple recommendation sources, then checking Montgomery County Public Libraries (MCPL) for borrowing options. Not affiliated with MCPL.

## Quick start

Install or copy `skills/mcpl-book-recommender/` into your Agent Skills environment. No MCP server, database or API keys are required for the public-web workflow; the agent must have web access. Optional Python 3 scripts support Open Library, Google Books, NYT bestseller lists and LibraryThing when provider access is configured. See the [skill](skills/mcpl-book-recommender/SKILL.md) and [source registry](skills/mcpl-book-recommender/references/sources.md) for details.

Example prompts:

- Recommend 8 nonfiction books about American history, then check MCPL.
- Find science fiction similar to The Three-Body Problem.
- Build a reading path for AI agents, from beginner to advanced.
- Recommend early chapter books for a 7-year-old who loves animals.
- Discover new literary award winners available as audiobooks.

## How it works

The skill routes a request to relevant reviews, curated lists, literary awards and read-alike services, validates candidate identity, ranks by reader fit and evidence, and then checks MCPL (or another requested library). Availability is separate from recommendation quality. The workflow is read-only: no holds, renewals or account login.

## Tests and limitations

Run `python -m unittest discover -s skills/mcpl-book-recommender/scripts -p 'test_*.py'`. Tests exercise request construction and local error handling, not live provider responses. Web/API access and real-time MCPL availability depend on the running environment and provider permissions. Licensed services are optional; never commit credentials or personal information.

## Project website

A mobile-first, parent-friendly introduction to the recommender is in [docs/index.html](docs/index.html). It includes original SVG illustrations, a three-step explanation, the source-selection architecture, and an interactive reading-prompt builder. The site is a static introduction, not a live recommendation engine.

### Publish with GitHub Pages

1. Open the repository's **Settings > Pages**.
2. Under **Build and deployment**, select **Deploy from a branch**.
3. Select **main** and **/docs**, then save.
4. After the deployment succeeds, open the URL shown in the Pages settings.

This repository is private; publishing from a private repository requires an eligible GitHub plan. A Pages site may be publicly accessible even when its repository is private. This site has no personal-data forms, trackers, or credentials. The project repository link may require authorized access. See [GitHub Pages documentation](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site).

### Local preview

Open `docs/index.html` in a browser, or run `python -m http.server 8000 --directory docs`. No build, dependencies, or backend is required.
