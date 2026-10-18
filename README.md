# H2O

A minimal water tracker built around one picture: your bottle, with mL markings. Drag the water line down as you drink, tap **Refill** when you top it up, and it works out how much you've had and whether you're on pace for your daily target.

## Put it on your iPhone with GitHub Pages

1. On GitHub, create a new **public** repository, for example `h2o`. (GitHub Pages is free for public repositories. Your drinking data never goes into the repo; it stays on your phone.)
2. Click **Add file → Upload files**, drag in every file from this folder, and click **Commit changes**.
3. Open the repository's **Settings → Pages**. Under **Build and deployment**, set **Source** to **Deploy from a branch**, choose the **main** branch and the **/ (root)** folder, then click **Save**.
4. After a minute or two the site is live at `https://YOUR-USERNAME.github.io/h2o/`. The link also appears at the top of the Pages settings.
5. On your iPhone, open that link in **Safari**, tap **Share**, then **Add to Home Screen**. Open H2O from your Home Screen from now on, so it runs full screen and keeps its own data.

Prefer the command line? From this folder:

```sh
git init
git add .
git commit -m "H2O"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/h2o.git
git push -u origin main
```

Then do step 3 above.

## How it works

- **Each morning** the bottle shows full and asks you to confirm. Tap **Yes, full**, or **Set level** if it isn't.
- **Drinking:** drag the water line down. It snaps to 50 mL steps, and every change gets an **Undo**.
- **Refilling:** tap **Refill**, or drag the line up. Refills never count as drinking.
- **Other drink:** for anything outside your bottle (a can, a glass, sparkling water bought out). Tea and coffee count too.
- **Active day:** one tap adds 500 mL to today's target only. Change the amount in Settings.
- **Today's log:** tap the big number to see or remove today's entries.
- **History:** the chart icon shows the last 7 or 30 days, your average, days on target and your streak.
- **Bottle sizes:** 500 mL, 1 L, 1.5 L or a custom size, in Settings.

## The daily target

Settings asks for sex (female or male), age, weight and activity level. Your daily energy use is estimated with the Henry (Oxford) equations, and the target allows about 1 mL of water per kcal, with roughly 80% of that coming from drinks and the rest from food. For an average adult with moderate activity, that matches the European Food Safety Authority's reference intakes of 2.0 L a day for women and 2.5 L for men (food and drinks together). From age 60 the target never drops below that reference. Under **Pregnant or breastfeeding** (available once you choose Female), choosing Pregnant adds 300 mL a day and Breastfeeding adds 700 mL a day, the extra amounts EFSA advises (breastfeeding needs more because of the water that goes into breast milk). You can always type your own target instead.

This is an estimate, not medical advice. If a doctor has told you to limit fluids, follow that advice instead.

## Reminders

Your target is spread across your waking hours and pacing stops 90 minutes before bed. When you fall behind, the status line turns amber and the bottle wobbles when you open the app.

A web app can't schedule notifications on its own, so there are no lock-screen alerts yet. Two ways to add them later:

- **A native iPhone version** built in Xcode, which can schedule smart local notifications.
- **A small push service** that sends web push notifications to the Home Screen app (supported on iOS 16.4 and later).

## Your data

Everything is saved on your phone, in the app's own storage. Nothing is sent anywhere. Removing the app from your Home Screen can delete its data.

## Updating

Upload changed files to the repository. The app picks up the new version the next time you open it (occasionally it takes a second launch). If you add or rename files, also change `CACHE` at the top of `sw.js`, for example to `h2o-v4`.

## Making it yours

- **Name:** `manifest.webmanifest`, plus the `<title>` and `apple-mobile-web-app-title` in `index.html`.
- **Colours:** the CSS variables at the top of the `<style>` block in `index.html`, for light and dark mode.
- **Icon:** replace the PNG icons, keeping the same file names. iPhone rounds the corners itself, so use a square image with no transparency.
