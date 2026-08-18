# Weltrade Africa — Partner Summit Qualification Tournament Leaderboard

Static, single-file leaderboard. No build step, no backend. Hosted on GitHub Pages.

## What this shows

54 partners, each with two achievement percentages (FTD and Spread) against their own individually approved target. No absolute FTD or Spread numbers are ever stored or displayed, only percentages. This matches the tournament's privacy rule: a partner with a small target and a partner with a large target render identically on this page.

**Scoring is compensatory**, unlike a strict pass/fail gate: Tournament Score = (FTD% × 50%) + (Spread% × 50%). A partner does not need to hit 100% on both metrics separately, they can offset one against the other. Reaching a Tournament Score of 100% qualifies a partner for leaderboard consideration; it does not by itself secure a Summit seat.

## First publication

1. Go to **github.com** and sign in.
2. Click **New repository**. Name it something like `maldives2026`. Set it to **Public**, GitHub Pages does not serve private repos on free accounts.
3. On the empty repository page, click **uploading an existing file**.
4. Drag in `index.html` and this `README.md`. Both go in the root, not in a folder.
5. Write a commit message like `initial leaderboard` and click **Commit changes**.
6. Go to **Settings → Pages**.
7. Under **Source**, choose **Deploy from a branch**. Branch: `main`. Folder: `/ (root)`. Click **Save**.
8. Wait two or three minutes, then refresh the Settings → Pages screen. The live URL appears at the top: `https://<user>.github.io/<repository>/`
9. Open the URL on a phone before sharing it with anyone.

**Important:** the file must be named exactly `index.html`, lowercase.

## Daily update routine

This tournament requires a **daily** refresh (not weekly). Do this in the same order every day:

1. Pull the current period's FTD and Spread totals per partner from the reporting system.
2. In your private targets sheet (kept separately, never in this file), compute each partner's two achievement percentages:
   ```
   ftd = (actual FTD in the window / that partner's FTD target) × 100
   spr = (actual Spread in the window / that partner's Spread target) × 100
   ```
   Round to whole numbers. Values above 100 are correct and expected.
3. Open `index.html` on GitHub and click the pencil icon to edit in the browser.
4. **First**, copy today's about-to-be-replaced rank into each partner's `prev` field. Do this before changing anything else, if you update the percentages first, the ranking recalculates and every movement arrow shows flat.
5. Then update `ftd` and `spr` for every partner in the `DATA` array.
6. Update `CONFIG.updateDate` and `CONFIG.daysElapsed` at the top of the script.
7. Commit. The live page refreshes within a minute or two.

Nothing else needs touching. Ranking, chips, arrows, the cut line, and the missing-percentage text all recalculate automatically from the two numbers you enter per partner.

## Before sharing the link

- Search the page source for any number that looks like a real target (e.g. a partner's actual FTD count or spread volume). If you find one, the privacy rule was broken, do not publish until it's removed.
- Confirm the participant count matches your official list (54).
- Temporarily set one partner's `ftd` to `150` and `spr` to `50`. Their score should compute to exactly 100 (150×0.5 + 50×0.5), and they should show as qualified with `+0`. This confirms the compensatory scoring is working, not a strict AND-gate.
- Set another partner to `ftd:100, spr:100`. They must show `+0`.
- Open the link on a phone. Rows should stack cleanly, nothing should overflow sideways.

## Known gap

Partner `country` fields are currently blank in the `DATA` array. Fill these in from the CRM/backoffice Partner ID → Country mapping once available, this is a cosmetic fix only and does not affect scoring or ranking.
