# davidriascos-site

Personal webpage, live at [davidriascos.com](https://davidriascos.com).

## How it deploys

Every push to `main` goes live automatically.

```
edit files → commit to main → GitHub notifies Hostinger → Hostinger copies the repo into public_html
```

- **Host:** Hostinger shared hosting (hPanel → Websites → davidriascos.com → Advanced → Git)
- **Connection:** Hostinger GitHub App, with access limited to this repo only
- **Branch:** `main` | **Target folder:** `public_html`
- **Manual redeploy:** the Redeploy button on the hPanel Git page

## Files

| File | What it is |
|---|---|
| `index.html` | The whole page |
| `styleDR.css` | Styles (loaded with a `?v=` version tag to break browser cache, so bump it after CSS changes) |
| `images/` | Photos used by the page |

## Decisions (what and why)

- **2026-10-16: Moved from editing files in Hostinger's File Browser to GitHub auto-deploy.**
  Why: version history for every change, easy rollback, and Claude can edit the repo directly.
  Trade-off: the repo is now the source of truth. Anything uploaded only through File Browser can be overwritten by the next deploy.
- **Left out of the repo on purpose:** `__MACOSX/`, `.textClipping`, `davidRiascosCv.zip` and the old `DavidRiascosCv/` folder.
  Why: Mac zip leftovers and an older version of the site that the current page doesn't link to. A copy is in the `public_html` backup taken before the first deploy.
- **Workflow:** small fixes go straight to `main`. Bigger changes go on a branch and are merged after review, since merging is what publishes.
