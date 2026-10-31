# ONE WORLD — media, science, culture & knowledge

A single-file, client-side platform: public television and radio from around the world, world news,
open-access books, an ancient-philosophy archive, open research and a world clock. No login, no
analytics, no third-party trackers.

Live: https://swami-prathmesh.github.io/one-world/

## Features

| Area | What it does |
|---|---|
| TV & Radio | Country-wise live channels from the open `iptv-org` index, category chips, search, multi-source automatic fallback |
| Player | In-page HLS playback, no redirects; optional captions, translation (35 languages) and spoken dub |
| News | Public RSS from BBC, Al Jazeera, DW, France 24, Guardian, The Hindu, Indian Express, NDTV, ScienceDaily, Nature, NASA, Space.com, ET, Mongabay + live ticker |
| Library | Project Gutenberg (Gutendex), Open Library, Internet Archive — covers, authors, EPUB/TXT/HTML links |
| Wisdom Archive | Sanatan Dharma, Jainism and Sikhism: original script, transliteration, English, Hindi, source reference, scholarly link; daily rotation + comparative philosophy |
| Science | NASA APOD, OpenAlex open research, portal directory (NASA, ESA, NOAA, USGS, World Bank, OWID, PubMed, arXiv, ISRO) |
| World Atlas | Country, capital, region, languages, live local time; jump to that country's channels |
| Global search | Fans out across countries, channels, wisdom entries, Gutenberg and OpenAlex |

## Technology stack

- Static HTML + CSS + vanilla JS — one file, no build step
- `hls.js` (CDN) for HLS playback
- `@xenova/transformers` (CDN, loaded on demand) for in-browser Whisper transcription
- Browser `SpeechSynthesis` for the spoken dub
- `localStorage` only for a channel cache and the optional NASA key

## API and data sources

| Source | Use | Key |
|---|---|---|
| iptv-org (`streams/<cc>.m3u`) | channel index | none |
| restcountries.com | country metadata | none |
| Gutendex | Project Gutenberg search | none |
| Open Library | book search | none |
| Internet Archive advancedsearch | texts | none |
| OpenAlex | open research | none |
| NASA APOD | picture of the day | `DEMO_KEY` (public demo key, rate-limited; set your own in localStorage) |
| Publisher RSS | news | none |

CORS-blocked feeds are fetched through public relays (`allorigins`, `codetabs`). No secret is
committed to this repository.

## Installation

```bash
git clone https://github.com/Swami-Prathmesh/one-world.git
cd one-world
python3 -m http.server 8000   # or just open index.html
```

## Deployment

GitHub Pages from `main` / root. Push to `main` and the site rebuilds automatically.
Any static host (Cloudflare Pages, Netlify, Vercel) works identically — there is no server code.

## Data licensing and copyright

- Channel metadata: `iptv-org`, MIT-licensed index. **A channel being listed is not proof that it is
  licensed in your country.** Streams belong to their broadcasters.
- Books: Project Gutenberg items are public domain in the US; Open Library and Internet Archive items
  may be lending-restricted or in copyright — those links open the provider's own reader, where their
  terms decide access. Never assume a book is public domain because it is online.
- Scripture passages: original-language text with reference and a link to a scholarly edition.
  English and Hindi renderings are project translations for orientation, not authoritative editions.
- News: headlines and links only; articles remain on the publisher's site.

## Privacy

No accounts, no analytics, no advertising, no fingerprinting. Nothing is stored beyond a local
channel cache. Third-party requests are limited to the sources above, which necessarily see your IP.

## Known limitations

- No interactive SVG world map yet (the World Atlas grid stands in)
- Scripture archive is a curated starter set, not a complete canon; expansion needs verified catalogues
- Some streams fail on CORS, geo-restriction or dead URLs; the player reports which
- In-browser transcription needs CORS-clean audio and a ~40 MB model download
- Daily Wisdom is deterministic by date, so it needs no scheduled job — but it also cannot "surprise"

## Contributing

Issues and pull requests welcome. For scripture or historical entries, cite the edition and page;
entries without a verifiable source will not be merged.
