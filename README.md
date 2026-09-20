# `data/` — generated

Everything here is written by `npm run refresh` and overwritten by the next run.
Nothing in this folder is edited by hand; the hand-maintained half lives in
[`registry/`](../registry) and next to each adapter.

| File | What it is |
|---|---|
| `index.json` | one row per protocol version: its TVL, and which feeds have data |
| `protocols/<id>.json` | everything we collected about that version |
| `changelog.json` | append-only log of values that moved between runs |

The files are committed on purpose: that is what makes the history of a value
auditable after a feed edits its own page.

The frontend reads them **at runtime**, from wherever
`apps/web/public/config.json` points — the copy shipped with the site, or this
folder straight from GitHub:

```json
{ "dataUrl": "https://raw.githubusercontent.com/<org>/<repo>/main/data" }
```

The shape of one feed's entry is described by
[`adapters/feeds/feed-output.schema.json`](../adapters/feeds/feed-output.schema.json).
