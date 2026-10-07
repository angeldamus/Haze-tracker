# Haze Watch

Live haze (PSI) and weather for Singapore, plus an ASEAN city comparison.

- Singapore PSI by region: NEA via data.gov.sg (`api-open.data.gov.sg`)
- Weather and regional air quality: Open-Meteo

It is a static site: one `index.html`, no build step, no dependencies, no API keys. The browser calls both data sources directly (both allow cross-origin requests).

## Deploy to Vercel

### Option A: Vercel CLI

```bash
npm i -g vercel
cd vercel-haze-watch
vercel          # first run: answer the prompts, accept the defaults
vercel --prod   # publish to production
```

When asked, leave the build command and output directory empty. Framework preset: **Other**.

### Option B: Git

1. Put this folder in a Git repository and push it to GitHub, GitLab or Bitbucket.
2. In Vercel, choose **Add New > Project** and import the repository.
3. Framework preset: **Other**. Leave Build Command and Output Directory empty. Deploy.

## Run locally

Any static server works:

```bash
npx serve .
# or
python3 -m http.server 8000
```

Opening `index.html` directly from disk also works.

## Notes

- `vercel.json` sets a Content-Security-Policy that allows only the three API hosts and Google Fonts. If you add another data source or script host, add it to `connect-src` or `script-src` there.
- NEA publishes PSI hourly. The page refreshes every 10 minutes and has a Refresh button.
- ASEAN cities show the US AQI from Open-Meteo (modelled data). It is not the same scale as Singapore's PSI.
- Edit the city list in the `CITIES` array near the top of the script in `index.html`.
