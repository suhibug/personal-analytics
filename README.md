# Personal Analytics

I instrumented my own products the way a marketing team would, then used the data to make them better.

**Products tracked**
- [My portfolio](https://suhibug.github.io/)
- [Trail Prep](https://suhibug.github.io/trail-prep/), my free hike planner

**Setup guide:** [SETUP.md](SETUP.md)

**Dashboard:** _Looker Studio link goes here once it is live_

## The stack (all free)

| Question | Tool |
|---|---|
| How many people visit, from where, and what do they click? | Google Analytics 4 |
| Which link brought them (resume, LinkedIn, Reddit...)? | UTM links ([utm-links.csv](utm-links.csv)) |
| What do people actually read, and where do they stop? | Microsoft Clarity heatmaps (portfolio only) |
| How do people find me on Google? | Google Search Console |
| One place to see it all | Looker Studio |
| YouTube, Instagram, LinkedIn numbers | YouTube connector + monthly CSV exports into Google Sheets |

## What I track, and what I don't

- **Portfolio:** page views, scrolls, outbound clicks (LinkedIn, Trail Prep, videos), country, device, and which UTM link brought the visit. Clarity heatmaps show what people read.
- **Trail Prep:** only actions (planned a day hike, imported a GPX file, saved a trip) and the state or country. Never the trail, place, date, or anything typed. No screen recordings, because people type trail names.
- No ad features: Google Signals and ad personalization are off.

## UTM naming

`utm_source` = where the link lives (resume, linkedin, reddit), `utm_medium` = the kind of place (pdf, social, community, email), `utm_campaign` = why it exists (job-search-2026, trail-prep-launch). Lowercase, dashes, no spaces, so Looker Studio groups them cleanly.

## What I learned

_Filled in from real data after the first 4 weeks. See [weekly-log.md](weekly-log.md)._

1.
2.
3.

## Changes I made because of the data

| Date | What the data showed | What I changed | Result |
|---|---|---|---|
| | | | |
