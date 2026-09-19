[Throne boss schedule
](https://jdestgermain.github.io/tnl-boss-schedule/)

## GitHub Pages and PWA

The site is deployed by `.github/workflows/static.yml` to GitHub Pages. Once the Pages deployment is live, open the site in a browser and use the browser's install or "Add to home screen" action. The app shell and embedded schedule remain available offline; live schedule refreshes when a connection is available.

## Recurring schedule overrides

Recurring corrections live in `ROTATION_OVERRIDES` in `index.html`. Keys are rotation-day numbers (`1` through `14`), and each nested key is the schedule time in Central time using 24-hour `HH:MM` format:

```js
const ROTATION_OVERRIDES = {
	10: {
		'13:00': 'Ascended Daigon | Grimturg',
		'20:30': 'Exodus !gpvp'
	}
};
```

The replacement applies every time that rotation day and time repeats. Use `|` to separate bosses and append `!gpvp` to a boss for Guild PvP. The replacement replaces the complete event group at that time, so include every boss that should remain. Boss names must match the schedule's display names; new names also need an entry in `OVERRIDE_BOSS_IDS`.

To request a future correction from an agent, provide the source date and local time, the current boss group, the desired boss group, and whether it repeats with the 14-day rotation. For example:

```text
Add this as a recurring 14-day schedule override:
Date/time: 2026-09-19 13:00 Central
Current: Ascended Daigon, Ascended Kowazan
Desired: Ascended Daigon, Grimturg
Guild PvP: no
```

The agent should convert the date/time to the matching rotation day and add or update `ROTATION_OVERRIDES`, then validate both the example date and another occurrence 14 days apart.

## Schedule editor

Open the site with `?editor=1` appended to the URL, for example `https://jdestgermain.github.io/tnl-boss-schedule/?editor=1`. The editor shows every source event in the 14-day rotation alongside its override fields. Use `Apply changes` to preview edits immediately, `Copy config` to copy the JavaScript configuration into `index.html`, and `Reset draft` to remove browser-local edits and restore the configured defaults. Browser-local drafts affect the calendar on that device until reset.
