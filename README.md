# GridPlayer Connectors

A growing collection of [GridPlayer](https://gridplayer.app) connectors —
JSON documents describing how to talk to a media server or metadata
catalog's API — for sources beyond the one GridPlayer ships built in
(Jellyfin).

The format itself, plus a JSON Schema and the bundled Jellyfin reference
connector, lives in a separate repository:
[gridplayer-connector-format](https://github.com/gorkemg/gridplayer-connector-format).
Start there if you're writing a new connector.

## Using a connector from this repo

In GridPlayer's server settings, add a custom server and point its
"Connector URL" field at the raw GitHub URL of the connector file you want.
For a self-hosted server (Plex), the "Server URL" field is your own
instance's address; for a metadata-only catalog (TMDB, TheTVDB), it's that
service's fixed API base URL — see the notes below for the exact value each
one needs. Either way, you supply your own API key/credentials in
GridPlayer's own settings; nothing here embeds one.

## Available connectors

- [`plex.json`](plex.json) — Plex Media Server
- [`tmdb.json`](tmdb.json) — [TMDB](https://www.themoviedb.org) (title
  metadata only, no browsing). Server URL: `https://api.themoviedb.org/3`.
  API key: a personal, free "Developer" API key from your own TMDB account's
  Settings → API — the *v4 Read Access Token*, not the shorter v3 API key.
- [`thetvdb.json`](thetvdb.json) — [TheTVDB](https://www.thetvdb.com) (title
  metadata only, no browsing). Server URL: `https://api4.thetvdb.com/v4`.
  API key: a personal API key from your own TheTVDB account, requested at
  <https://www.thetvdb.com/api-information>.

Both TMDB and TheTVDB require every application using their API to display
attribution — this connector format supports declaring that as data (see
`attribution` in [SPEC.md](https://github.com/gorkemg/gridplayer-connector-format/blob/main/SPEC.md#attribution)),
and both files here already declare their provider's required wording, so
GridPlayer shows it automatically. Don't remove or reword it if you fork
either file.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) — including this repository's scope.
