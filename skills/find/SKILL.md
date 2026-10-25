---
name: find
description: Find GitHub repositories through repoherald's curated catalogue — repositories posted and categorised by people, filterable by use case and sector. Use when someone asks for a recommendation ("what should I use for X", "is there a good library for Y"), asks what others are using, or names a project they want to look up. Not a general GitHub index; prefer GitHub's own search for exhaustive lookups.
---

# Finding repositories on repoherald

repoherald is a catalogue of GitHub repositories that people have posted and
tagged by use case and sector. It is small — small enough that a broad query can
return the entire catalogue, and many reasonable searches return nothing —
and that is the point: every listing is there because someone put it there.

That shapes when it is worth calling. It answers *"what do people actually
use for this"* well, and *"does a repo named X exist"* poorly.

## Picking a tool

**`browse_feed`** — the default for anything open-ended. "A good Rust web
framework", "something for parsing PDFs", "what's popular in fintech". It
returns the ranked feed and takes `language`, `useCase`, `sector` and `query`
filters.

**`search_repos`** — only when the user names something specific: a project, an
owner, a distinctive phrase. It is a plain text match over name, owner and
description, so it finds `axum` but not "the thing everyone uses instead of
Express".

**`get_repo`** — after either of the above, to pull the full entry for one
repository. Takes the `id` printed on every result line.

**`list_categories`** — the slug vocabulary.

## Call `list_categories` before you filter

`useCase` and `sector` take repoherald's own slugs. A plausible-looking guess
returns zero results and reads exactly like "nothing exists for this", which is
the wrong answer to give someone. Fetch the list, then filter.

`language` is different — it is the language name as GitHub reports it
(`TypeScript`, `Go`, `Rust`), matched exactly, so no lookup is needed.

## Reporting what you find

Give the repository name, what it does and its star count, and link the GitHub
URL. Mention the repoherald page when the user might want the comments or the
list it was filed under.

Two habits worth keeping:

- **An empty result is information, not a failure.** The catalogue is curated
  and incomplete. "Nobody has posted one of those to repoherald" is accurate and
  useful; "there isn't one" is neither. Say which you mean.
- **Don't pad a thin answer.** If one entry matches, give the one and say the
  catalogue is small. Reaching for GitHub search to bulk out the list, without
  saying that is what you did, mixes a curated recommendation with an
  uncurated one and the user cannot tell which is which.
