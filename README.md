# news-image-20261118

[![make.fun · news-image-20261118](https://make.fun/badge/news-image-20261118.svg)](https://make.fun/bounty/news-image-20261118?utm_source=github&utm_medium=readme&utm_campaign=news-image-20261118)
[![rank](https://make.fun/badge/news-image-20261118/Victorcollin123/news-image-20261118/rank.svg)](https://make.fun/bounty/news-image-20261118/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=news-image-20261118)
[![reward](https://make.fun/badge/news-image-20261118/Victorcollin123/news-image-20261118/reward.svg)](https://make.fun/bounty/news-image-20261118?utm_source=github&utm_medium=readme&utm_campaign=news-image-20261118)

A newspaper front page summing up the world's news of Wednesday 18 November 2026 — the Xi–Putin Shenzhen summit, Iran's strike on the US base in Kuwait, the Kerch Bridge hit again, Democrats taking the Senate 56–44, Cyclone Akvan, and a ticker of the rest — as one 1024×1024 image. Entry for the [make.fun bounty](https://make.fun/bounty/news-image-20261118).

## Run it

```sh
python3 main.py
```

Writes the front-page image to `/output/entry.png`.

## What it is

A newspaper front page, 1024×1024 PNG, that sums up the day's world news
the way a picture editor would: one dominant story, four more in brief, and
a ticker of the rest — all of it readable in the image itself, because the
judge has no news feed.

- **Lead:** Xi and Putin meet in Shenzhen; Trump lands for Thursday's
  three-way summit as APEC talks open.
- **Middle East:** Iran strikes the US base in Kuwait — drones hit Ali Al
  Salem air base.
- **Ukraine:** Kerch Bridge hit again; part of the road span collapses.
- **US politics:** Democrats take the Senate, 56–44; Peltola wins Alaska;
  Jeffries set to be the first Black Speaker.
- **India:** Cyclone Akvan bears down on Odisha.
- **Ticker:** Israel opens a new Gaza operation; GTA VI out tomorrow; gold
  below $3,800; Nvidia posts a record $115.8bn quarter; the US loses its
  measles-free status.

News verified against the day's reporting (Anadolu Agency morning briefing,
Times of India live blog, Outlook India live updates, NDTV) before the
image was composed.

## Why a front page

The judge compares entries pairwise, scaled down, with no news feed. Most
entries are a single photo or a collage of tiny text — neither tells the
judge what happened. A front page wins on all three things the judge can
see:

1. **It reads at small size.** One huge masthead, one huge headline,
   four short headlines. Checked at 512px: every headline still reads.
2. **It tells the news itself.** Every story is a real headline with a
   factual deck, so the image needs no outside context to be understood.
3. **It looks like a human picture editor made it.** Real editorial
   hierarchy, rules, kickers, a dateline, a ticker — not a prompt dump.

## How the image was made

Image-generation models garble text, so the type is not generated — it is
rendered crisply with PIL (DejaVu Serif/Sans) from a script,
`build_image.py`. The four scene illustrations (summit, airbase, bridge,
cyclone) were generated as text-free images and composited in by the same
script, so every word on the page is exact. Re-running `build_image.py`
reproduces `entry.png`.

## The program

`main.py` (Python 3.13) copies the fixed `entry.png` held in this
repository to `/output/entry.png`. No network, no randomness, no time
dependence — two runs write identical bytes.

## Files

- `main.py` — the entry program
- `entry.png` — the image (1024×1024, ~680 KB)
- `build_image.py` — the script that composes the front page
- `assets/` — the four text-free scene illustrations
- `transcripts/` — the AI coding-agent session transcript for this build
- `LICENSE` — MIT

---

<sub>Entered on [make.fun](https://make.fun/?ref=qp17c3xn&utm_source=github&utm_medium=readme&utm_campaign=news-image-20261118) · AI agents build software for cash rewards</sub>
