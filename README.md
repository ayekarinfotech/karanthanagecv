# karan-thanage-cv

Open-source, single-file digital CV for **Karan D. Thanage** — Founder & CEO, Ayekar Infotech. Terminal-boot hero, a git-commit-styled experience log, and no build step: it's one `index.html`, ready for GitHub Pages.

**Live:** add your deployed URL here once connected.

---

## 1. Put it on GitHub

```bash
# from this folder
git init
git add .
git commit -m "Initial commit: digital CV"
git branch -M main
git remote add origin https://github.com/<your-username>/<repo-name>.git
git push -u origin main
```

If you'd rather it live at `<your-username>.github.io` directly (no `/repo-name/` in the URL), name the repository exactly `<your-username>.github.io`.

## 2. Turn on GitHub Pages

1. On GitHub, open the repo → **Settings → Pages**.
2. Under **Build and deployment → Source**, choose **Deploy from a branch**.
3. Branch: `main`, folder: `/ (root)` → **Save**.
4. GitHub gives you a URL like `https://<your-username>.github.io/<repo-name>/` — that's your CV, live, for free.

## 3. Connect your DigitalPlat free domain

DigitalPlat (freedomain.digitalplat.org) issues free subdomains such as `karanthanage.dpdns.org`. Point it at GitHub Pages like this:

**A. Tell GitHub about the domain**
In the repo → **Settings → Pages → Custom domain**, type your full domain (e.g. `karanthanage.dpdns.org`) and click **Save**. This writes a `CNAME` file into the repo root — don't delete it later.

**B. Point the domain at GitHub in the DigitalPlat DNS panel**
Since a DigitalPlat domain is a subdomain (not an apex/root domain), you only need a **CNAME record** — no A records needed:

| Type  | Host / Name              | Value / Points to      |
|-------|---------------------------|--------------------------|
| CNAME | `@` (or as DigitalPlat labels the record for your subdomain) | `<your-username>.github.io` |

If DigitalPlat's panel won't let a CNAME sit at the domain root, add a `TXT` verification record first (GitHub's **Settings → Pages → Add a domain → Verify** flow will generate the exact value to paste) — this is optional but recommended so no one else can claim the domain on GitHub.

**C. Wait and verify**
DNS can take anywhere from a few minutes to a few hours to propagate. Once it resolves, go back to **Settings → Pages** and tick **Enforce HTTPS** — GitHub issues a free TLS certificate automatically.

Check propagation any time with:
```bash
dig +short karanthanage.dpdns.org
```
It should eventually return `<your-username>.github.io`.

## 4. Local preview

No build tools required — just open `index.html` in a browser, or serve it:
```bash
python3 -m http.server 8000
# visit http://localhost:8000
```

## 5. Editing content

Everything lives in `index.html`:
- `#about` — summary
- `#ventures` — Ayekar Infotech / GoVerifAI / KaakaPOS cards
- `#arsenal` — skills
- `#log` — experience, styled as commits
- `#education` — academics & certifications
- `#connect` — contact links

Fonts (Space Grotesk, IBM Plex Sans, IBM Plex Mono) load from Google Fonts; colors and type scale are defined as CSS custom properties at the top of the `<style>` block if you want to retheme it.

## License

MIT — see `LICENSE`. Fork it, strip it down, make it yours.
