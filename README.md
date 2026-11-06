# Life in Weeks

A "Your Life in Weeks" calendar in a single HTML file. Enter your birthday and see your whole life laid out as a grid: each row is a year, each box is a week. Weeks you've lived are filled in, and the current week is highlighted.

## Features

- 52 weeks across, one row per year, grouped into 4-week blocks and 5-year bands
- Configurable birthday and number of years shown (default 80)
- Hover any box to see your age, week number, and the date that week starts
- Stats: weeks lived, weeks remaining, percentage of the grid filled, and current age in years + weeks
- Automatically fits the window width, and supports light and dark mode
- Installable as an app (PWA) from the browser's install option; works offline after the first visit
- No build step, no dependencies, no server: just static files

## Usage

Open `index.html` in a browser, or host it with GitHub Pages:

1. Push this repository to GitHub.
2. In the repo, go to **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, select `main` and `/ (root)`, and save.
4. The calendar will be live at `https://<your-username>.github.io/<repo-name>/`.

## Installing and offline use

When served over HTTPS (e.g. GitHub Pages), the page includes a web app manifest and a service worker, so browsers offer to install it as an app. The service worker is **network-first**: it always fetches the latest version when online and falls back to the cached copy when offline. (The service worker doesn't run when opening `index.html` directly as a file.)

## How settings are stored

Your birthday and year count are saved in the browser, never sent anywhere:

- They are written to both `localStorage` and IndexedDB.
- The page asks the browser for **persistent storage** (`navigator.storage.persist()`), so the data isn't evicted automatically. A note on the page shows whether the browser granted it.
- Clearing the browser cache won't remove them. Clearing "cookies and site data" will.

Storage is tied to the site's origin, so settings saved when opening the local file won't appear on the GitHub Pages site (and vice versa), and each browser or device keeps its own copy.
