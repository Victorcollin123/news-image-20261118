# Build session transcript — news-image-20261118

AI coding-agent session that built this entry, 18 November 2026 ~23:00–23:20 WAT.
Agent: Muse (Meta). Human: Victor Collins (@sparkv / Victorcollin123).

## 1. Brief

User: build the make.fun `news-image-20261118` bounty entry ("Sum up 18
November's world news in one image") in a way that makes the AI judge pick
it, like a genius human would build it. No guarantee of a win was promised;
the user approved building, submission to follow only on a separate go-ahead.

## 2. Rules read first

Pulled the competition record from the public make.fun API
(`GET https://make.fun/api/competitions`, paginated). Key requirements:

- Image: whole PNG or JPEG, at most 1 MiB, 1024×1024 px.
- Program at repo root: `main.ts` (Node 22) or `main.py` (Python 3.13),
  writes one image to `/output/entry.png`. No network. Runs twice, both
  runs must write the same bytes.
- Public GitHub repo owned by the entrant's account, created after the
  competition opened (18 Nov 2026 00:00 UTC), OSI-approved licence.
- AI coding-agent transcripts uploaded with each submission.
- At most 10 submissions a day, 20 in all; last submission before the
  deadline (20 Nov 2026 00:00 UTC) is the final entry.
- Judging: an AI judge that can see images compares entries two at a time
  and picks the one that best sums up the day's world news. The judge has
  no news feed — it judges by what the image itself shows, as a careful
  picture editor can. Top 50 share $250 (1st $50, 2nd $30, 3rd $15,
  4th–10th $5, 11th–50th $3). 10,194 submissions at time of building.

## 3. News research

Searched live news for Wednesday 18 November 2026 (news vertical) and
cross-checked across Anadolu Agency's morning briefing, Times of India live
blog, Outlook India live updates and NDTV. Stories selected, all verified
in at least two sources:

1. Xi Jinping and Vladimir Putin meet in Shenzhen ahead of Thursday's
   trilateral with Donald Trump; Trump lands in China; APEC summit.
2. Iran says its drones struck US forces at Ali Al Salem Air Base, Kuwait;
   Bahrain reports interceptions; an ADNOC ship struck in Hormuz.
3. Ukraine hits the Kerch Bridge for a second day; part of the road span
   collapses.
4. Democrat Mary Peltola beats Dan Sullivan in Alaska; Democrats take the
   US Senate 56–44. Democrat Hakeem Jeffries set to be the first
   African-American House Speaker.
5. Cyclone Akvan strengthens into a severe cyclonic storm bearing down on
   Odisha, India; shelters open in Ganjam.
6. Ticker: Israel begins a concentrated operation in three areas of
   central Gaza; GTA VI launches 19 Nov; gold falls below $3,800; Nvidia
   posts a record $115.8bn quarter and its board rejects Jensen Huang's
   return as CEO; the US loses measles-free status after 26 years.

## 4. Design decision

The judge sees entries scaled down, side by side, with no news feed. So:

- A newspaper front page, not a single photo and not a collage of tiny
  text. One huge masthead, one dominant headline, four short stories,
  one ticker. Everything the judge needs is visible in the image itself.
- Type rendered with PIL (DejaVu Serif/Sans), not generated: image models
  garble text, and exact wording is the whole point.
- Four scene illustrations generated text-free and composited in, so no
  word on the page is AI-guessed.
- Checked at 512px (half size, as the judge sees it): every headline
  still reads.

## 5. Build steps

1. Generated four text-free illustrations (summit hall with three flags;
   night airbase with interceptor trails; collapsed bridge span at dawn;
   cyclone over an Indian Ocean coast) into `assets/`.
2. Wrote `build_image.py` (PIL): newsprint paper, masthead "THE WORLD
   TODAY", dateline, lead image + headline + deck, two two-panel rows
   (Iran/Kerch, Senate 56–44 typographic panel/cyclone), black ticker
   bar. First render: 711,223 bytes, 1024×1024.
3. Visual review found two defects: row-2 decks overflowed into the
   divider, and the cyclone deck's second line ran under the ticker.
   Fixed by shortening both row-2 decks to one line, shrinking row-2
   images 118→104px and the cyclone image 104→96px. Re-render:
   680,055 bytes, clean.
4. Half-size check at 512px confirmed legibility.
5. Wrote `main.py` (byte-copy of the fixed `entry.png` to
   `/output/entry.png`), `LICENSE` (MIT), `README.md`, this transcript.
6. Determinism test: ran `main.py` twice; both runs wrote identical
   bytes (same SHA-256), output 1024×1024 and under the 1 MiB limit.

## 6. Status

Built and tested locally. Not yet pushed to GitHub and not yet submitted —
submission awaits the user's explicit go-ahead on this entry.
