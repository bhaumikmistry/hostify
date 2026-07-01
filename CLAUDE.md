# Hostify

A public repository that stores user-submitted HTML pages. Submissions arrive via pull requests, are validated by CI, and served through an external viewer at `bhaumikmistry.com/hostify/<username>/<title>`.

## Architecture

- **This repo is storage only.** It does not serve pages directly.
- HTML files are fetched at runtime by the viewer app using GitHub raw content URLs.
- The viewer renders content inside a sandboxed iframe (`sandbox="allow-scripts"`).

## Directory Structure

```
submissions/<username>/<title>/index.html
```

Each submission is a single `index.html` file placed in a folder named by the submitting user and their chosen title. Titles must be URL-safe (lowercase alphanumeric and hyphens).

## Submission Rules

1. One `index.html` per submission (max 500KB).
2. No iframes within submissions, no redirects off-domain.
3. No credential harvesting forms, crypto miners, or tracking scripts.

## Validation

The GitHub Action at `.github/workflows/validate-submission.yml` runs on every PR:
- Checks file structure matches `submissions/<username>/<title>/index.html`
- Validates file size
- Checks for known malicious patterns (iframes, redirects, crypto miners)

PRs that pass validation auto-merge. Flagged PRs require manual review.

