# Hostify

Public storage for HTML pages submitted to [bhaumikmistry.com/hostify](https://bhaumikmistry.com/hostify).

## What is this?

Hostify is a drop box for single-page HTML creations. Submit your page via pull request, pass automated validation, and it goes live at:

```
https://bhaumikmistry.com/hostify/<username>/<title>
```

## Submitting a page

1. Fork this repo
2. Add your file at `submissions/<your-username>/<your-title>/index.html`
3. Open a pull request
4. CI validates your submission automatically
5. Once merged, your page is live

## Rules

- One `index.html` per submission (max 500KB)
- No iframes, no redirects, no form submissions to external URLs
- No crypto miners or tracking scripts
- Titles must be lowercase alphanumeric with hyphens (e.g. `my-cool-project`)

## How it works

This repo is a static file store. The viewer at `bhaumikmistry.com/hostify` fetches files from this repo using GitHub raw URLs and renders them in a sandboxed iframe. The iframe `sandbox` attribute restricts what submitted pages can do — scripts can run but cannot access the parent page, cookies, or navigate away.

