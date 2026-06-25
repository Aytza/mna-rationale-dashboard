# Aytza M&A Rationale Dashboard

Live dashboard for the enriched 2025-2026 M&A rationale workbook.

Current build includes buyer segment mix, granular primary/secondary strategic-motion rationale, health-tech-vs-incumbent rationale comparison, explicit AI mention flags, buyer/acquired HQ geography, cross-border analysis, and a public Google Sheet data source.

## Live Google Sheet Source

The public dashboard loads the `Dashboard_Data` tab from [Aytza_MnA_Strategic_Motions_Full](https://docs.google.com/spreadsheets/d/1a6VBIqUISlTlemZ5qGnPt56QwB9IV39_NGfJn8nJzMc/edit) at page load. If the tab is unavailable or not shared publicly/readable through Google Visualization, the dashboard falls back to the generated static dataset and shows a blocked-feed warning.

Sheet edits appear in the dashboard after a browser refresh, the dashboard's `Refresh Live Data` action, or the automatic one-minute refresh while the page is open.

`Buyer Segment` is the dashboard's authoritative segment field. The dashboard only rolls up from `Acquirer Type` when `Buyer Segment` is blank. The article-facing rationale charts use `Strategic Motion (Primary)` and `Strategic Motion (Secondary)`, with `Other / unclear` ordered last.

For the live source to work on GitHub Pages, the source must be a native Google Sheet and the tab must be readable by the browser, ideally shared as viewable by anyone with the link. Uploaded Excel files opened in Drive are not reliable as a live source.

To test a different native Sheet without redeploying, add `?sheetId=<google-sheet-id>&sheet=Dashboard_Data` to the dashboard URL. To force the static fallback, use `?source=static`.

## Local Preview

```sh
python3 -m http.server 8765
```

Then open `http://127.0.0.1:8765/`.

## GitHub Pages

Deploy the contents of this `dashboard` folder as the Pages site root.

1. Create or open the target GitHub repository under the Aytza account.
2. Copy these files to the repository root, or to `/docs` if that is how the repository is configured.
3. In GitHub, open Settings -> Pages.
4. Set the source to the target branch and folder.
5. Keep `.nojekyll` in the deployed folder so GitHub Pages serves the static assets directly.

The dashboard is fully static and does not require an API key or server runtime.
