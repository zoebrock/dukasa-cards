# Dúkasa Dispensary — digital business cards

Static site, no build step. Each card is a folder so the URL is clean:

| Card | Path | Printed QR points to |
|---|---|---|
| Aspa Dukas | `/aspa/` | https://dukasa.com.au/aspa |
| Helena Cangadis | `/helena/` | https://dukasa.com.au/helena |

```
aspa/index.html, aspa/aspa.vcf        # card page + "Save contact" file
helena/index.html, helena/helena.vcf
assets/fonts/                          # Kommuna (names), ABC Favorit Medium (all other text) — licensed, web use
assets/logo-pill.png                   # rotating capsule (white, transparent)
assets/logo-wordmark.png               # static wordmark (white, transparent)
qr/                                    # print-ready QR PNGs (2050px, white on clay #927150)
index.html                             # redirects to dukasa.com.au
```

## Instructions for Claude Code

1. Create a GitHub repo (e.g. `dukasa-cards`), commit this folder as the repo root, push to `main`.
2. Enable GitHub Pages: Settings → Pages → Deploy from branch → `main` / root.
3. **Domain — important.** The QR codes encode `https://dukasa.com.au/aspa` and `/helena`, i.e. paths on the main website. GitHub Pages can't serve just two paths of a domain that's hosted elsewhere, so pick one:
   - **Recommended:** host this repo on a subdomain, e.g. `cards.dukasa.com.au` (add a `CNAME` file containing that host, plus a DNS CNAME record → `<github-user>.github.io`). Then on the main dukasa.com.au site add 301 redirects: `/aspa` → `https://cards.dukasa.com.au/aspa/` and `/helena` → `https://cards.dukasa.com.au/helena/`.
   - Or copy the `aspa/`, `helena/` and `assets/` folders into the main website's hosting so they're served at those exact paths.
4. After deploying, scan both QR codes on iPhone and Android and tap every link, including Save contact.

## Editing

- Contact details live directly in each `index.html` and matching `.vcf`; keep them in sync.
- To add a person: duplicate a folder, rename the slug, update the name/title/email in both files, and generate a new QR for `https://dukasa.com.au/<slug>`.
- Brand: clay `#927150`, white only. Motion respects `prefers-reduced-motion`.
