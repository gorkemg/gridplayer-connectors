# GridPlayer Connectors

A growing collection of [GridPlayer](https://gridplayer.app) connectors —
JSON documents describing how to talk to a self-hosted media server's API —
for servers beyond the one GridPlayer ships built in (Jellyfin).

The format itself, plus a JSON Schema and the bundled Jellyfin reference
connector, lives in a separate repository:
[gridplayer-connector-format](https://github.com/gorkemg/gridplayer-connector-format).
Start there if you're writing a new connector.

## Using a connector from this repo

In GridPlayer's server settings, point a server's "Connector URL" field at
the raw GitHub URL of the connector file you want.

## Available connectors

- [`plex.json`](plex.json) — Plex Media Server

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) — including this repository's scope.
