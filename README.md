# JAV Mania scraper for Stash

A [Stash](https://github.com/stashapp/stash) scene scraper that fills in English metadata for **uncensored JAV**
from [JAV Mania](https://www.jav-mania.net/), with censored titles covered by JAV Mania and
[AV品番 (avhinban.com)](https://avhinban.com/) as a Japanese-language fallback.

Most JAV metadata sources focus on censored studio releases. JAV Mania covers the uncensored sites with
English titles, descriptions, performer names (with their Japanese names as aliases), tags, release dates
and cover images.

## Supported sites

| Studio | File name examples |
|---|---|
| Caribbeancom | `carib-112426-001.mp4`, `112426-001.mp4` |
| Caribbeancom Premium | `caribpr 112426_001.mp4` |
| 1Pondo | `1pondo_112326_001.mkv`, `112326_001.mp4` |
| PacoPacoMama | `paco 101416_183.mp4` |
| 10Musume | `10mu-112426_01.mp4` |
| Muramura | `muramura 112126_1276.mp4` |
| HEYZO | `heyzo_hd_3970.mp4` |
| Kin8tengoku | `kin8tengoku-4278.mp4` |
| Nyoshin | `nyoshin n3424.mp4` |
| Heydouga (hgmo) | `hgmo 6608.mp4` |
| H4610 / C0930 / H0930 | `h4610-ki261027.mp4` |
| Pikkur | `pikkur 04727.mp4` |
| AV9898 | `av9898 2948.mp4` |
| Censored releases | `JUSD-813.mp4`, `sqte00425.mp4` |

Bare ids without a studio name are tried as Caribbeancom (`MMDDYY-NNN`), then 1Pondo, Caribbeancom
Premium and PacoPacoMama (`MMDDYY_NNN`), then 10Musume (`MMDDYY_NN`).

## Install

1. Copy `scrapers/JAVMania/` into your Stash `scrapers` folder
   (for example `~/.stash/scrapers/JAVMania/`).
2. In Stash: **Settings → Metadata Providers → Scrapers → Reload scrapers**.
3. Python 3 must be on the `PATH` of the Stash server. No extra packages are needed.

## Use

- **Scrape by URL**: paste a `jav-mania.net/movies/…`, `jav-mania.net/jav/…` or `avhinban.com/works/…` URL.
- **Scrape with… → JAV Mania** on a scene: uses the scene's title (or file name when the title is empty) or code.
- **Scene search** in the scrape dialog: type a code such as `paco 101416_183` or `JUSD-813`.

Requests go only to jav-mania.net and avhinban.com, one or two per scene.

## License

MIT
