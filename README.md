# Bachelor Book — web (static site)

Static three-page site for Bachelor Book: marketing landing, privacy policy,
terms of service. Hosted on GitHub Pages; gives Google Play a real HTTPS URL
for the privacy policy the moment it's needed.

## Files

- `index.html` — landing page (also the root of the site)
- `privacy.html` — privacy policy
- `terms.html` — terms of service
- `.nojekyll` — tells GitHub Pages to serve files as-is (so the pages don't
  go through Jekyll's front-matter rules; optional but harmless)

## Deploy to GitHub Pages (5 minutes)

1. **Create a new GitHub repo** named `bachelor-book-web`
   - Public
   - No README, no .gitignore (we already have files)
2. **Push these files** to the `main` branch.
3. **Settings → Pages**
   - Source: **Deploy from a branch**
   - Branch: `main`, folder: **/(root)**
   - Save
4. Wait ~1 minute. Your URLs become:
   - Landing — `https://lzytourist.github.io/bachelor-book-web/`
   - Privacy — `https://lzytourist.github.io/bachelor-book-web/privacy.html`
   - Terms — `https://lzytourist.github.io/bachelor-book-web/terms.html`

## Push commands

```bash
cd bachelor-book-web
git init
git add index.html privacy.html terms.html .nojekyll README.md
git commit -m "Initial static site: landing, privacy, terms"
git branch -M main
git remote add origin git@github.com:lzytourist/bachelor-book-web.git
git push -u origin main
```

Then enable Pages in the repo settings as described above.

## Wire it up

- **Play Console** → App content → Privacy policy → paste the privacy URL.
- **Mobile app** — add a "Privacy policy" link in mess settings that opens the URL in a custom tab.
- **In-app sign-in screen** — the existing subtitle can link to privacy too.

## Local preview

```bash
python3 -m http.server 8000
# open http://localhost:8000
```

## Custom domain (optional)

If you have `bachelorbook.app` and want a real domain:
- Add a `CNAME` file containing the domain (e.g. `app.bachelorbook.app`)
- Point a DNS `CNAME` from that subdomain to `lzytourist.github.io`
- In Pages settings, set the custom domain and tick "Enforce HTTPS"
