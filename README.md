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
| Censored releases | `JUSD-813.mp4`, `sqte00425.mp4`, `022JKSR-505.mp4` |

Separators can be `-`, `_`, space or `.`; extra text such as `[site]`, `-1080p`, `-FHD`, `-C` or `hhb` is ignored.

Bare ids without a studio name: `MMDDYY-NNN` is Caribbeancom and `MMDDYY_NN` is 10Musume. `MMDDYY_NNN` is used by
1Pondo, Caribbeancom Premium and PacoPacoMama, and the same id often exists on more than one of them, so a bare
`MMDDYY_NNN` is only filled in automatically when exactly one studio has it. Otherwise add the studio name to the
file name, or use scene search to pick from the matches.

Not covered: FC2-PPV and other amateur platforms.

## Install

1. Copy `scrapers/JAVMania/` into your Stash `scrapers` folder
   (for example `~/.stash/scrapers/JAVMania/`).
2. In Stash: **Settings → Metadata Providers → Scrapers → Reload scrapers**.
3. The Stash server needs Python 3.8+ (no extra packages). Stash looks for `python`/`python3` on its own `PATH`;
   if it can't find it (common for Windows services and some Docker images), set **Settings → System →
   Python executable path**.

## Use

- **Scrape by URL**: paste a `jav-mania.net/movies/…`, `jav-mania.net/jav/…` or `avhinban.com/works/…` URL.
- **Scrape with… → JAV Mania** on a scene: uses the scene's URL, code, title, then its file name.
- **Scene search** in the scrape dialog: type a code such as `paco 101416_183` or `JUSD-813`, or a performer
  name or title words in Japanese (e.g. `吉岡ひより`) to pick from up to 20 matches.

Censored releases: AV品番 covers about 600,000 FANZA and MGS titles and records where each one is also sold.
For titles found on JAV Mania it fills in what the English page lacks (series, director, studio, release date).
The scene also gets the plain store pages on FANZA, MGS, DUGA and Sokmil (no affiliate or tracking parameters).

The scraper only contacts jav-mania.net and avhinban.com (usually 1 to 4 requests per scene, never following
redirects to other sites) and gives up after 60 seconds. A miss returns nothing rather than a guess.

## Performers

- **Scrape by URL**: a JAV Mania `jav-mania.net/actress/…` page or an AV品番 `avhinban.com/performers/…` page.
- **Search by name** in English (`Yui Hatano`, matched on JAV Mania) or Japanese (`大槻ひびき`, matched on AV品番).
- **Scrape with… → JAV Mania** on a performer uses her JAV Mania / AV品番 URL, then her name.

Fields: name, the other-language name as alias (English ⇄ Japanese) plus other spellings, gender, career start and
end years, height, measurements (e.g. `88E-59-85`), birthday, and both site URLs. Profiles cover about 6,000
performers. Scraped scenes carry the profile and page URL on each performer, so performers created from a scene are
filled in too.

## Scene fields

Title, code, description, release date, duration, studio (for censored releases the label, with its maker as the
parent studio), series (group), director, tags, performers, cover image and URLs: the JAV Mania and AV品番 pages
plus the plain FANZA, MGS, DUGA and Sokmil store pages.

## License

MIT
