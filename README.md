# "La mia Italia" 2027 tour website

A single-page site built from the final Canva brochure (`~/Downloads/Tour 2027.pdf`) and the
26 photographs in `~/Downloads/Final Brochure/`.

## Run it

Just open `index.html` in a browser. Nothing to install, no build step.

To serve it locally instead:

    python3 -m http.server 8787 --directory website

## Where it lives

Live at https://anitalianaffairtours.com, served by GitHub Pages from the `main` branch of
https://github.com/rightin2/anitalianaffairtour. DNS is at Cloudflare: four A records for `@`
to GitHub's addresses and a `www` CNAME to `rightin2.github.io`, all DNS only (grey cloud).
To update the site, commit in this folder and `git push`; it is live within about a minute.

## Publish it elsewhere

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
to the gathering in Venice, a scroll-driven route map (three region bands, private transfers on
the line, the Cinque Terre day trip as a spur onto the water; a vertical version on phones), counters, chapter covers with parallax and
kinetic titles, photo mosaics with a custom cursor and a swipeable lightbox, side thread
navigation on wide screens, a full-screen menu on phones, and a music button bottom left with a fade in and out.

## Layout system

One set of tokens in `:root` drives every dimension, so proportions stay consistent at any size:

- `--maxw` 1240px content column, `--pad` the side padding, `--gut` the leftover gutter.
- The nav and the hero controls use the same column as the body text, so the logo lines up
  with the first word of every paragraph at every width.
- Vertical rhythm is width-based (`vw`), never height-based, so a short laptop screen and a
  tall monitor get the same proportions rather than different ones.
- Long-form columns are capped at `34rem` (about 64 characters) for readability.
- The side thread sits in the gutter and only appears at 1348px and above; its labels only
  at 1560px and above, where they fit beside the column without touching it.

## Updating the availability line

The hero carries a small pill under the countdown: "6 spots sold, 4 left". It is plain text in
`index.html` (search for `id="spots-line"`), so change the two numbers there and push. The tour
takes eight to ten travellers, so the pair should add up to ten.

That one line is also the only thing to edit. A returning visitor whose browser remembers a
lower number sees a notice in the top right (bottom of the screen on a phone): "Since your last
visit, N places have been taken, leaving M." It reads the figure straight out of the pill, stores
it in that browser's local storage, and stays silent on a first visit or when nothing has moved.
It dismisses on the cross or after fourteen seconds.

## Ambient background

A fixed layer (`#amb`) behind every section runs a slow playlist of four studies that cross-fade:
a still rest, warm drifting blooms (golden hour), dappled olive-grove light, and pollen turning
on the air. Adapted from the AMAPP background engine, re-tuned for a light page: the studies use
`mix-blend-mode: multiply` in the brand palette instead of `screen` on navy.

The playlist is driven by the wall clock, so reopening the page carries on where the loop is
rather than restarting. The tinted sections are slightly translucent (76 to 84 per cent) so the
motion reads through them; photographs and the olive contact panel stay opaque. Only one study
runs at a time, the canvas loop stops when the tab is hidden, and `prefers-reduced-motion`
pins a single still study.

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
