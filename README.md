# GB Driver Duty Clock

A single-page, offline web app for keeping a 12-hour van shift inside the **11-hour daily duty limit** of the GB domestic drivers' hours rules.

The day runs as three countdowns:

1. **Time until break**: counts down to the planned break (default 12:30).
2. **Break remaining**: the break starts automatically at the planned time. Tap *Back on duty early* if you're called back.
3. **Time until finish**: counts down to the latest legal clock-out:
   `clock-in + 11h + break actually taken`.
   Starting early or cutting the break short moves this earlier.

Anything that isn't a genuine break counts as duty, so the app works from the break you actually took, not the hour payroll deducts.

## Using it

- **Settings**: rota start/finish, break start and length, and optional company-rule warnings (max hours before a break, minimum break length). These warnings never mark a shift as illegal. Only the 11h duty limit does.
- **Today's times**: edit any time if you forgot to tap or the break started late. If the app's data was lost mid-shift, see Backups below.
- **Clock out** is press-and-hold so a stray tap can't end the shift. Every action can be undone from the bar at the bottom.
- **Logbook**: completed shifts with duty total, a weekly total, and CSV export.

## Backups (and browsers that clear data on exit)

Data is stored in the browser on your phone. Browsers like Brave can be set to wipe it on exit, so the app is built to cope with that:

- **Auto backup:** every time you clock out, a backup file goes straight to Downloads. You can turn this off in Settings. Downloads aren't touched when the browser clears its data.
- **After a wipe:** with an empty logbook the app shows **Restore logbook from backup**. Pick the newest `driver-clock-backup-….json` from Downloads.
- **Wiped mid-shift:** during rota hours the app offers **Already on shift? Clocked in at 07:00**, which is one tap. The break fills itself in if it's already passed. If you clocked in at another time, use the button below it.
- **Back up** can also be tapped any time. It opens the share sheet, e.g. to save a copy to Drive.

## Files

- `index.html`: the whole app.
- `sw.js`: service worker for offline use. The page loads from the network first, so updates arrive the next time you open the app with signal.
- `manifest.json`, `icon-*.png`, `apple-touch-icon.png`: install-to-home-screen metadata and icons.

Data saved by the first version of the app (logbook and any shift in progress) is migrated automatically.

*Not legal advice. Check the current rules on gov.uk and your employer's policy.*
