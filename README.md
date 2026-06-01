# Aytza M&A Rationale Dashboard

Static dashboard for the enriched 2025-2026 M&A rationale workbook.

Current build includes primary rationale taxonomy, product-expansion subcategories, explicit AI mention flags, buyer/acquired HQ geography, cross-border analysis, and an optional live Google Sheet override layer.

## Live Manual Overrides

The public dashboard tries to load the `Manual_Overrides` tab from [Aytza M&A Dashboard Manual Overrides](https://docs.google.com/spreadsheets/d/1ey7OBRkaaU9OnRqlPE7DGEvDOYwomV3OO2xvrcwMfy0/edit) at page load. If the tab is unavailable or not shared publicly/readable through Google Visualization, the dashboard falls back to the generated static dataset.

For the live layer to work on GitHub Pages, the override source should be a native Google Sheet and the tab must be readable by the browser, ideally shared as viewable by anyone with the link. Uploaded Excel files opened in Drive are not reliable as a live source.

Create a `Manual_Overrides` tab with these headers:

```text
Deal ID
Row
Acquirer Type Override
Buyer Segment Override
Primary Rationale Override
Product Expansion Override
AI Flag Override
AI Evidence Override
Buyer HQ Country Override
Acquired HQ Country Override
Rationale Theme Override
Source Type Override
Source URL Override
QA Status Override
QA Notes
Reviewer
Last Updated
```

Only `Deal ID` or `Row` plus the fields you want to override are required.

To test a different native Sheet without redeploying, add `?sheetId=<google-sheet-id>&sheet=Manual_Overrides` to the dashboard URL. To bypass the live layer, use `?overrides=off`.

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
