# NA306G — Assignment results (Spring 2026)

Static lookup page for student assignment results. Built on the `grade-lookup`
template from `lab-infrastructure/grade-lookup/`.

## How it works

- `index.html` prompts the student for an ID and fetches `results.json`.
- `results.json` is keyed by anonymous student ID (the same ID students used on
  their submission). It also carries `_meta.valid_until`, after which the page
  shows "Results are no longer available."
- `.github/workflows/auto-expiry.yml` runs daily and, once `valid_until` is past,
  replaces `results.json` with a minimal stub so the underlying data is no
  longer retrievable from the repository.

## Updating results during revisions

1. Edit `results.json` in this folder (or regenerate from
   `semesters/2026_Spring/build_final_results.py` and copy the output here).
2. `git add results.json && git commit -m "Update results" && git push`.
3. GitHub Pages redeploys within a minute.

## URL

After deployment: `https://<github-user>.github.io/<repo-name>/`
