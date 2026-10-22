[Throne boss schedule
](https://jdestgermain.github.io/tnl-boss-schedule/)

## GitHub Pages and PWA

The site is deployed by `.github/workflows/static.yml` to GitHub Pages. Once the Pages deployment is live, open the site in a browser and use the browser's install or "Add to home screen" action. The app uses its embedded 14-day rotation and remains available offline.

## Editing the schedule

The complete recurring schedule lives in the `window.EMBEDDED_SCHEDULE` object in `index.html`, under `rotationSchedule.tiers.t4.days`. The numeric keys are rotation days (`1` through `14`), and each nested key is a slot ID whose value is Central time in the `slots` map.

Each event group is a pipe-separated string. Append `!gpvp` to a boss for Guild PvP. Replace the complete group at a time when correcting a schedule, and keep the event names as canonical IDs.

After editing, reload the page and check both the changed date and the same rotation day 14 days later.
