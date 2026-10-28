# Ugokin — showcase site

Static site (HTML + CSS, no build step, no JavaScript, no external requests).
Fonts (Geist, Geist Mono, SIL OFL 1.1) are self-hosted in `fonts/`.

```
index.html     content
style.css      design (palette = CSS variables at the top)
favicon.svg
fonts/         Geist + Geist Mono (latin) and their licences
CNAME          custom domain for GitHub Pages (ugokin.com)
```

## Preview locally

```bash
python3 -m http.server 8000   # then open http://localhost:8000
```

## Deploy on GitHub Pages with ugokin.com (domain at OVH)

1. **Repo**: create a repo (e.g. `ugokin-site`), push these files at the root of `main`.
2. **Pages**: Settings → Pages → Source: *Deploy from a branch* → `main` / `/ (root)`.
   Under *Custom domain*, enter `ugokin.com` and save (the `CNAME` file already contains it).
3. **OVH DNS** (Web Cloud → Domain names → ugokin.com → DNS zone):
   - Delete the existing `A` (and `AAAA`) records on the bare domain `ugokin.com`.
   - Add four `A` records on the bare domain:
     `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - Optional, four `AAAA` records:
     `2606:50c0:8000::153`, `2606:50c0:8001::153`, `2606:50c0:8002::153`, `2606:50c0:8003::153`
   - Add a `CNAME` for `www` → `<github-user-or-org>.github.io.` (with the trailing dot in OVH).
   - **Do not touch the `MX` records** (`mx3.mail.ovh.net`, `mx4.mail.ovh.net`) or the SPF `TXT`:
     they make `contact@ugokin.com` work.
4. **HTTPS**: wait for DNS to propagate (minutes to 24 h), then in Settings → Pages tick *Enforce HTTPS*.

Never use a wildcard (`*.ugokin.com`) DNS record with GitHub Pages.

## Edit

- Text: `index.html`.
- Accent colour: `--accent` and `--accent-rgb` in `style.css` (e.g. `#34d399` / `52 211 153`).
