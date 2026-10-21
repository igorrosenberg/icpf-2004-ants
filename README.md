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
- `docs/maxi.html` — design essay: the ANT language as an assembler, and MAXI, a
  higher level language of composable behaviors and strategies
  (https://igorrosenberg.github.io/icpf-2004-ants/docs/maxi.html)

## References

The 2004 ICFP Programming Contest, "Dinner with Ambiants", was run by the
University of Pennsylvania PL Club. Teams wrote the brain of an ant, a finite
state machine shared by every ant in a colony, to find food, bring it home,
defend the nest and fight a rival colony. Ants sense nearby cells, move, turn,
pick up and drop food, and leave chemical markers to guide each other. Many of
the sites below date from 2004 and some have gone offline.

### Task and contest

- [Dinner with Ambiants](https://cis.upenn.edu/~plclub/contest/ants.html), the
  official task page at UPenn (often unreachable).
- [Task specification PDF](https://paucasedmatura.alvb.in/files/imgs/2013-03_icfp-contest-2004-rules.pdf)
  (version 4, 5 June 2004), a third-party mirror. It is byte-identical to the
  copy this simulator was built from.
- [Task specification, HTML transcription](https://claude.ai/artifact/Md8uujKp6WVQg6grD7mN4S)
  of the same rules.
- [ICFP Contest Archive, 2004](https://icfpcontest.github.io/contest/2004/), an
  unofficial archive of past contests. Its 2004 page only links back to the
  UPenn site.
- [Contest announcement](https://lwn.net/Articles/82455/) on LWN.net.
- [Final results, archived](https://web.archive.org/web/20111002133032/https://alliance.seas.upenn.edu/~plclub/cgi-bin/contest/results.php)
  (Wayback Machine copy of the UPenn results page).
- [ICFP Programming Contest](https://en.wikipedia.org/wiki/ICFP_Programming_Contest)
  on Wikipedia, with a summary of the 2004 task and its winners.

The official `sample.ant` used to live at `http://icfpcontest.org/sample.ant`,
which now returns 404. `samples/sample.ant` here is the short example from the
task description.

### Entries and write-ups

- **Red Team** (Tom Rokicki, John Dethridge, Lars Backstrom and others):
  [write-up](https://tomas.rokicki.com/icfp2004/), with the
  [final submission](https://tomas.rokicki.com/icfp2004/Red_Team_Submission_Final.tar.gz)
  and the
  [lightning submission](https://tomas.rokicki.com/icfp2004/Red_Team_lightning_submission.tar.gz).
  Their final ants come from `rmdm4_outer_encloseZ.antc` (traps in the home
  base, surrounding the enemy base) and `surround_2.antc` (traps around the
  enemy base). They wrote their own simulator, visualizer and an "ant calculus"
  compiler.
- **ANTisocial** (Martin Jambon):
  [write-up "My Ants"](https://mjambon.github.io/mjambon2016/icfpcontest2004.html),
  with the
  [final submission](https://mjambon.github.io/mjambon2016/icfpcontest2004/submission-ANTisocial.tar.gz)
  and a
  [fixed submission](https://mjambon.github.io/mjambon2016/icfpcontest2004/submission-ANTisocial.fixed.tar.gz)
  that repairs a last-minute bug in its `wait` function. The ant is generated
  from OCaml combinators; it draws six marked lines from the anthill corners
  and guards the corners.
- **Linepithema humile** (Peter Sewell and others, Cambridge):
  [write-up](https://www.cl.cam.ac.uk/~pes20/icfp-contest-2004/). It placed
  13th of 361 ants in the main division and is written in an OCaml DSL. Its
  brain is bundled here as `samples/linepithema-humile.ant`.
- **Mario Storti** (CIMEC):
  [entry notes](https://amcaonline.org.ar/foswiki/Main/Cimec/ICFPContestEntry),
  with a Perl macro compiler for ant code and ants split into species that use
  one marker each.

### Discussion

- [ICFP 2004 Programming Contest Results](https://tech.slashdot.org/story/04/09/21/021253/icfp-2004-programming-contest-results)
  on Slashdot.
- [2004 ICFP Contest Spinoff Game](https://developers.slashdot.org/story/04/09/12/1450257/2004-icfp-contest-spinoff-game)
  on Slashdot, about Ant Wars, the game adapted from the task.

### Where to start

1. Read the specification for the ant instruction set and the simulation rules.
2. Load the Red Team final brain to study a strong strategy.
3. Compare it with the ANTisocial fixed brain.
4. Look inside the archives for the source code and build notes behind each brain.
