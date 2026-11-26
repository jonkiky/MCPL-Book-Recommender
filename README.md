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
