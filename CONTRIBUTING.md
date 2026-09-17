# Contributing a connector

1. Read the format spec in
   [gridplayer-connector-format](https://github.com/gorkemg/gridplayer-connector-format/blob/main/SPEC.md).
2. Write your connector as `<server-name>.json`, lowercase, hyphenated (e.g.
   `plex.json`).
3. Validate it against the schema before opening a PR:

   ```bash
   npx ajv-cli validate \
     -s https://raw.githubusercontent.com/gorkemg/gridplayer-connector-format/main/schema/connector.schema.json \
     -d <server-name>.json
   ```

   The schema catches structural mistakes (missing required fields, wrong
   types) but can't verify your queries/paths actually match your server's
   real API — test that against a live instance yourself.
4. Open a PR. Include, in the description:
   - what server/software this targets, and a link to its own API docs if
     it has any
   - which capabilities you've tested (metadata lookup, browsing, login)
   - the GridPlayer version you tested against

## Scope

This repository hosts two kinds of connector:

- **General-purpose home media servers** — software built around organizing
  and streaming a personal video library (Jellyfin, Plex, Emby, and
  similar).
- **Metadata-only catalog sources** — a public database used purely for
  automatic title/cast/tag matching against files you already have, with no
  library of its own to browse or stream from (TMDB, TheTVDB, and similar).
  A connector in this category sets `metadataLookup` and omits `browse`
  entirely; see [`metadataLookup.rest`](https://github.com/gorkemg/gridplayer-connector-format/blob/main/SPEC.md#title-search-metadatalookuprest-v4-rest-only)
  for the title-search variant these typically need.

Connectors outside both categories won't be merged; open an issue first if
you're unsure whether your target qualifies. If the source has its own
terms requiring attribution, declare it via the connector's own
[`attribution`](https://github.com/gorkemg/gridplayer-connector-format/blob/main/SPEC.md#attribution)
field rather than assuming GridPlayer will show it any other way — that's
what makes such a source usable through this repo at all without
GridPlayer's own source needing to know about it. Merging here isn't
required for a connector to work: the format is fully open and documented
in
[SPEC.md](https://github.com/gorkemg/gridplayer-connector-format/blob/main/SPEC.md),
so any connector can be hosted and used independently of this repository.

## A connector is data, not code

Nothing in this format executes. If your server needs something the current
format can't express — a new auth flow, a response shape the interpreter
can't map — open an issue describing the gap rather than trying to work
around it; that likely means a format version bump, which needs a
GridPlayer-side change too.
