# Setup, step by step

About a weekend. Everything is free. Where a step says "send Claude", paste it into the chat and the code gets updated for you.

## Part 1: Google Analytics 4 (20 min)

1. Go to https://analytics.google.com and sign in with your **personal** Google account, not ASU. You keep it after you graduate.
2. **Start measuring**, then fill these in:
   - Account name: `Suhitha`
   - Property name: `suhibug.github.io`
   - Time zone: **United States, Arizona**. Currency: USD.
   - Business details: any size, "Small". Objectives: "Understand web and/or app traffic".
3. Platform: **Web**. URL: `suhibug.github.io`. Stream name: `suhibug.github.io`. Keep **Enhanced measurement ON**: it records scrolls, outbound clicks and video plays with no extra code.
4. Copy the **Measurement ID** (`G-XXXXXXXXXX`). **Send Claude.**
   One ID covers both sites, because Trail Prep lives at `/trail-prep/` on the same domain. You'll see when someone goes from your portfolio to Trail Prep.
5. Settings that matter (all under **Admin**, the gear icon, bottom left):
   - **Data collection and modification, Data retention:** change 2 months to **14 months**. Otherwise old data is deleted.
   - **Data collection:** leave Google signals **off**.
   - **Data streams, your stream, Configure tag settings, Define internal traffic:** add a rule named `me`, IP address equals your IP (search "what is my ip"). Then **Data filters**, Internal traffic, set to **Active**, so your own visits don't count.
   - **Custom definitions, Create custom dimension:** name `Region`, scope Event, event parameter `region`. This shows which states people plan Trail Prep hikes in.
   - **Events:** once events start arriving (after about a day), mark `plan_day_hike`, `plan_backpacking` and `save_trip` as **Key events**. These are Trail Prep's "conversions".

## Part 2: Microsoft Clarity (10 min, portfolio only)

1. Go to https://clarity.microsoft.com and sign in (Google login works).
2. **New project**. Name: `Portfolio`. URL: `https://suhibug.github.io`.
3. Pick **Install manually**. The code shows `clarity.ms/tag/` followed by your ID (about 10 characters). Copy just the ID. **Send Claude.**
4. **Settings, Setup, Google Analytics integration:** connect it to the GA4 property. Then you can open recordings from GA4 segments.

Trail Prep does not get Clarity: recordings would show the trail names people type.

## Part 3: Publish (5 min)

After Claude adds the IDs, use GitHub Desktop:
- **suhibug.github.io:** commit "Add analytics", then Push.
- **trail-prep:** commit "Add GA4 counts", then Push.
- **personal-analytics:** File, Add local repository, `~/personal-analytics`, Publish (untick "Keep this code private").

Check it works: open your portfolio on your phone, then open GA4, **Reports, Realtime**. You should show up within a minute. Do this before turning on the internal traffic filter, or test on mobile data.

## Part 4: Google Search Console (10 min)

1. Go to https://search.google.com/search-console, **Add property**, **URL prefix**: `https://suhibug.github.io/`.
2. Verify with **Google Analytics** (one click, since GA4 is already on the page).
3. **Sitemaps:** submit `sitemap.xml`.
4. Search data takes a few days to appear.

## Part 5: UTM links (1 hour, spread out)

Open [utm-links.csv](utm-links.csv) and put each link where its first column says: resume header, email signature, LinkedIn Featured, Instagram bio, YouTube description, Substack, Behance, and Trail Prep posts on Reddit and Discord.
Need a new one? Copy a row and change `utm_source`. Keep everything lowercase, with dashes.
Never put UTMs on links between your own pages (portfolio to Trail Prep). That splits one visit into two.

## Part 6: Looker Studio dashboard (2 to 3 hours)

https://lookerstudio.google.com, **Blank report**, add data: **Google Analytics**, then your property.
Add a **date range control** at the top of every page (default: last 28 days).

| Page | Charts |
|---|---|
| 1. Overview | Scorecards: Active users, Sessions, Engagement rate, Average engagement time. Line chart: Active users by Date. |
| 2. Where they come from | Table: Session source / medium, Session campaign, Sessions, Engagement rate. Bar: Sessions by Session source. Filter control: Session campaign. |
| 3. Who | Geo map: Active users by Country. Table: City, Active users. Bar: Device category. |
| 4. What they do | Table: Page path, Views, Average engagement time. Table: Event name, Event count. Table: Link URL, Event count (filter: Event name = `click`; these are outbound clicks). |
| 5. Trail Prep | Filter: Page path contains `/trail-prep/`. Scorecards: plan_day_hike, plan_backpacking, save_trip, gpx_import counts. Table: Region, Event count. |
| 6. Search | Add data, **Search Console**, your site. Table: Query, Clicks, Impressions, CTR, Average position. |
| 7. Social | Add data, **YouTube Analytics** (free connector). For Instagram and LinkedIn, make a Google Sheet with columns `month, platform, followers, posts, impressions, engagements`, fill it monthly from each app's insights export, and add the Sheet as a data source. |

Then **Share, Manage access, Anyone with the link can view**. Paste the link into README.md.

## Part 7: The habit (10 min a week)

- **Every Monday:** add one row to [weekly-log.md](weekly-log.md).
- **Every month:** watch 5 Clarity recordings and check the heatmap. Where do people stop scrolling? What do they click that isn't a link?
- **Every month:** paste your YouTube and Reddit comments into Claude and ask "what do people like, what do they complain about?" Note it in the log.
- **After 4 weeks:** write "What I learned" in README.md from the log, plus one change you made and what happened.

Data notes:
- **Views vs sessions vs users:** one user can make many sessions, and one session can view many pages.
- **Engagement rate:** sessions that lasted 10+ seconds, viewed 2+ pages, or hit a key event. Bounce rate is the opposite.
- **"(not set)" or "(other)":** too little data, or Google hiding rare values for privacy.
