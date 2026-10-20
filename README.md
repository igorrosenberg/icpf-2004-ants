# icpf-2004-ants

ICFP 2004 programming contest ("Dinner with Ambiants"): an ant colony simulator.

A static HTML5 app that runs two ant brains against each other on a hex world
(drawn as a square grid with every odd row shifted half a cell), with
forward/back replay, stats, fog of war (per-colony view) or god view, and zoom.
Brains, worlds and settings are saved in the browser's `localStorage`; nothing
is sent to a server.

## Run locally

Open `index.html` in a browser, or serve the folder:

```sh
python3 -m http.server 8000
```

## GitHub Pages

`.github/workflows/pages.yml` deploys the site on every push to `main`.
One-time setup: in the repo go to **Settings → Pages → Build and deployment**
and set **Source** to **GitHub Actions**. The site is then served at
https://igorrosenberg.github.io/icpf-2004-ants/.

## Layout

- `index.html` — the whole simulator (engine + UI), self-contained
- `samples/` — sample brains and worlds from the contest spec
