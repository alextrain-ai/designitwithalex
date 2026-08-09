# designitwithalex

Static site + UGC portfolio for **designitwithalex.com**, hosted on GitHub Pages.

| Path | What |
|---|---|
| `index.html` | Main site (Czech) |
| `ugc/` | UGC portfolio — video grid with inline previews |
| `pdf/` | `Alex-UGC-Portfolio.pdf`, `Alex-UGC-How-It-Works.pdf` |
| `showreel/` | `Alex-UGC-Showreel.mp4` |

## Editing

`index.template.html` is the source; `index.html` is generated with the web fonts inlined
as base64 data URIs, so a page is one self-contained file with no external requests.
After editing a template, rebuild:

```
python3 tools/build_site.py designitwithalex/index.template.html designitwithalex/index.html
```

(`build_site.py` lives in the parent Claude Code workspace and reads fonts from `site/fonts/`.)

Push to `main` to redeploy.

## Contact form

The form posts to [Web3Forms](https://web3forms.com), which delivers to
alexdesign@designitwithalex.com. Set `ACCESS_KEY` near the bottom of
`index.template.html`, then rebuild. While the key is empty the form falls back to opening
the visitor's mail client with the message pre-filled.

Previously this proxied to an n8n webhook via Caddy on the VPS (`/api/contact`), which only
worked while the site was served from that server.
