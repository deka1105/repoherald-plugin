# repoherald for Claude Code

Search and browse [repoherald](https://repoherald.com) — a human-curated
catalogue of GitHub repositories, categorised by use case and sector — without
leaving your session.

## Install

```bash
claude plugin marketplace add deka1105/repoherald-plugin
claude plugin install repoherald@repoherald
```

Or in one command inside a session:

```
/plugin install repoherald --marketplace deka1105/repoherald-plugin
```

## Use

Ask for a recommendation and Claude reaches for the catalogue on its own:

> what are people using for background jobs in Go?

Or invoke the skill directly:

```
/repoherald:find a self-hosted analytics tool
```

## What it adds

Four read-only tools, backed by the MCP server at
`https://repoherald.com/api/mcp`:

| Tool | What it does |
| --- | --- |
| `browse_feed` | The ranked feed, filterable by language, use case and sector |
| `search_repos` | Text search over name, owner and description |
| `get_repo` | Full detail for one repository |
| `list_categories` | The use-case and sector slugs the filters accept |

No account, no sign-in, no configuration. Everything these tools read is
already public on the website.

## What it doesn't do

Your own lists, saved repositories and credits are not reachable from here —
that needs an authenticated connection, which this version doesn't implement.
It also isn't a GitHub index: the catalogue is small on purpose, so use
GitHub's own search when you need exhaustive results.
