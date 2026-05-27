# Aytza M&A Rationale Dashboard

Static dashboard for the enriched 2025-2026 M&A rationale workbook.

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
