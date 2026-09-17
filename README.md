# "La mia Italia" 2027 tour website

A single-page site built from the final Canva brochure (`~/Downloads/Tour 2027.pdf`) and the
26 photographs in `~/Downloads/Final Brochure/`.

## Run it

Just open `index.html` in a browser. Nothing to install, no build step.

To serve it locally instead:

    python3 -m http.server 8787 --directory website

## Publish it

Upload the whole `website` folder to any static host (Netlify drop, Cloudflare Pages,
GitHub Pages, or an `anitalianaffair.com.au` subfolder). `index.html` must sit next to `img/`.

## What is in it

| File | Notes |
|---|---|
| `index.html` | Everything: markup, styles, scripts. No dependencies except Google Fonts. |
| `audio/music.m4a`, `audio/music.mp3` | The soundtrack, 128 kbps with a two-second fade at each end, from `Music for website.wav`. Safari takes the AAC, everything else the MP3. It autoplays where the browser allows sound before interaction, otherwise it starts on the visitor's first click, tap or key press; the button bottom left pauses and resumes it, and a pause is remembered for the session. |
| `img/*-xl.webp` | 3400 px long edge, for 4K screens. Full-bleed panels and the lightbox pick it via `srcset` when the screen warrants it. |
| `img/*-lg.webp` | 2000 px long edge, the default for full-bleed panels and large tiles. |
| `img/*-sm.webp` | 900 px long edge, for small tiles. |
| `img/logo.png` | The An Italian Affair mark, lifted from the brochure cover and keyed to transparency. |
| `img/mark.png` | The handwritten "La mia Italia" Tour lettering, same source. |
| `img/about-antonella.png` | The handwritten "About Antonella" heading from brochure page 2. |

## Copy

All body copy is the approved brochure wording, verbatim, including the About Antonella
panel and the Robert Browning quotation. Section headings and the six "In this chapter"
lists are the only new writing, and they are assembled from the brochure's own
Tour Highlights and Visit lists.

## Features

Intro veil, full-screen slideshow with Ken Burns drift and a no-dip crossfade, live countdown
to the gathering in Venice, animated route ribbon, counters, chapter covers with parallax and
kinetic titles, photo mosaics with a custom cursor and a swipeable lightbox, side thread
navigation on wide screens, a full-screen menu on phones, and a music button bottom left with a fade in and out.

## Design notes

Colours, type and shapes follow the brochure: sage `#d4e6c6` and `#eef5e9`, olive `#6b5733`,
terracotta `#b26432`, IBM Plex Sans throughout, and the arched photo frames from page 3.

## Known limits

- Three source photographs are small (about 1536 x 2040): the sunset hill town, the pasta making
  and the terrace above the valley. They are only used in small tiles, never full screen.
  Antonella's portrait (`img/antonella.webp`) is upscaled from the 173 px version in the PDF
  and shown small; replace that one file with a proper scan and nothing else changes.
- The logo and cover lettering are traced from the brochure PDF at 300 dpi and are crisp.
- Photographs are matched to regions by eye. Swap any `img` `src`, `srcset` and `data-full`
  trio to change a picture.
