# Precision Floor Care

One-page site and printable business card for a commercial floor care business
serving Southeast Michigan.

**Live:** https://tnler.github.io/precision-floor-care/

## Contact on the site

- Phone: (248) 565-5255
- Email: noah.jaron@icloud.com

## What's here

    index.html    the entire site — no build step, no dependencies
    og.png        1200x630 link-preview image (regenerate with the command below)

Everything is inline: styles, script, and an SVG favicon as a data URI. There is
no framework and nothing to install. Editing `index.html` and pushing is the
whole deploy process — GitHub Pages serves it within a minute or so.

## The before/after graphic

The hero comparison is not a photo. It's a perspective VCT floor drawn twice on
`<canvas>` from the same seeded tile layout — once worn (scuff arcs, yellowed
haze) and once restored (light tile, specular reflections of ceiling fixtures).
A seeded PRNG keeps the layout stable across resizes so the floor doesn't
reshuffle. Drag the handle, or tab to it and use arrow keys.

If you swap in real before/after photos later, replace the two `<canvas>`
elements with `<img>` tags — the wipe logic works the same, it just clips
whatever is inside `.wipe`.

## Printing the business card

Ctrl+P (Cmd+P) on the live page. A print stylesheet hides everything except the
two card faces and sizes them to a true 3.5 x 2 inch card. Turn on **Background
graphics** in the print dialog or the black face prints white.

Brand colors for a print shop:

| Role   | Hex       |
|--------|-----------|
| Black  | `#0A0D0B` |
| Green  | `#2FCE71` |
| Orange | `#FF6B1A` |

## Regenerating og.png

The link-preview image is a headless screenshot of the hero:

```powershell
& "C:\Program Files\Google\Chrome\Application\chrome.exe" --headless=new --disable-gpu `
  --no-sandbox --hide-scrollbars --virtual-time-budget=4000 --window-size=1200,630 `
  --screenshot="og.png" "file:///C:/Users/tyler/projects/precision-floor-care/index.html"
```

Re-run it after any change to the hero, or the preview goes stale.

## Custom domain

GitHub Pages supports one for free. Buy the domain, add a `CNAME` file to this
repo containing just the domain, then point DNS at GitHub:

    A     185.199.108.153
    A     185.199.109.153
    A     185.199.110.153
    A     185.199.111.153

Then update the four absolute URLs in `index.html` — `link rel=canonical`,
`og:url`, `og:image`, `twitter:image` — and the `url` in the JSON-LD block.

## Handing this to Noah

When he has a GitHub account, transfer the repo: **Settings -> General ->
Danger Zone -> Transfer ownership**. The Pages URL changes to his username
unless a custom domain is already attached.
