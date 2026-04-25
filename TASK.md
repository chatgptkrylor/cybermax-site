# TASK: Fix Cybermax Site for GitHub Pages

## Problem
The site at https://chatgptkrylor.github.io/cybermax-site/ is broken because all asset paths are absolute (e.g., `/dist/css/bootstrap.min.css`, `/images/logo.png`). On GitHub Pages with a subpath, these resolve to `https://chatgptkrylor.github.io/dist/css/bootstrap.min.css` instead of `https://chatgptkrylor.github.io/cybermax-site/dist/css/bootstrap.min.css`.

## Original Site
https://www.cybermaxsolutions.com/ — this is how it should look.

## Deployed (Broken) Site
https://chatgptkrylor.github.io/cybermax-site/

## What to Fix
1. **ALL HTML files** — Change absolute paths to relative paths:
   - `href="/dist/` → `href="dist/`
   - `src="/dist/` → `src="dist/`
   - `href="/css/` → `href="css/`
   - `src="/js/` → `src="js/`
   - `href="/images/` → `href="images/`
   - `src="/images/` → `src="images/`
   - `href="/blog/` → `href="blog/`
   - Any other absolute path starting with `/` that refers to local assets
2. **CSS files** — Check for absolute URL references to images/fonts and fix similarly
3. **JS files** — Check for any absolute path references
4. **Internal links** — All `href="/page.html"` should become `href="page.html"` or `href="./page.html"`

## Important
- Do NOT change external URLs (https://..., http://...) — those are fine
- Do NOT change the `url` field in the JSON-LD schema
- The `www.cybermaxsolutions.com` subdirectory in the repo can be deleted — it's a duplicate
- Test after fixing by checking paths in a few HTML files

## Files in Repo
All HTML files are at repo root: index.html, aboutus.html, services.html, etc.
Assets: dist/, css/, js/, images/, blog/

## How to Verify
After fixing, open https://chatgptkrylor.github.io/cybermax-site/ and compare with https://www.cybermaxsolutions.com/ — they should look identical.