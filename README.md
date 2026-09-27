# Tarablus

A minimal single-page site that displays one full-screen horizontal image.

## Structure

```
Tarablus/
├── index.html            # Page markup, loads the image
├── css/
│   └── style.css         # Full-screen responsive image styling
├── images/
│   └── feet.jpg          # The displayed image
├── icons/
│   ├── favicon-16x16.png
│   ├── favicon-32x32.png
│   ├── favicon-192x192.png
│   ├── favicon-512x512.png
│   └── apple-touch-icon.png
├── favicon.ico            # Multi-resolution (16/32/48px) favicon
├── site.webmanifest       # Icon metadata for PWA/mobile home-screen use
├── CNAME                  # Custom domain for GitHub Pages
└── README.md
```

## How the responsiveness works

`images/feet.jpg` is horizontally oriented (landscape). The `<img>` tag is
styled differently depending on screen orientation (via a CSS
`orientation` media query):

- **Horizontal (landscape) screens**: `object-fit: cover` sizes the image
  to `100vw` x `100vh`, filling the screen with no empty space. The full
  image is shown since the viewport's aspect ratio is close to (or wider
  than) the image's.
- **Vertical (portrait) screens**: the image is rotated 90° (`transform:
  rotate(90deg)`) so it lies flat in landscape orientation again, sized to
  `100vh` x `100vw` before rotation, then displayed with
  `object-fit: contain`. This shows the **entire image with no trimming**;
  any leftover space is letterboxed (filled with the black background)
  instead of cropping the image.

## Replacing the image

Replace [images/feet.jpg](images/feet.jpg) with the real horizontal image,
keeping the same filename (or update the `src` in
[index.html](index.html) if you rename it).

## Favicon / site icon

The browser tab icon (`favicon.ico` plus the PNGs in [icons/](icons)) is a
center-cropped square taken from [images/feet.jpg](images/feet.jpg). If you
replace the main image, regenerate the icons to match (any square-crop +
resize tool, or an online favicon generator, works with
`images/feet.jpg` as input) to produce:

- `favicon.ico` — multi-resolution (16/32/48px)
- `icons/favicon-16x16.png`, `icons/favicon-32x32.png`
- `icons/favicon-192x192.png`, `icons/favicon-512x512.png`
- `icons/apple-touch-icon.png` (180x180)

## Local preview

Open [index.html](index.html) directly in a browser, or serve the folder
with any static file server, e.g.:

```
npx serve .
```

## Publishing with GitHub Pages

Push this repository to GitHub named `tarablus`, then enable GitHub Pages
(Settings → Pages) for the `main` branch, root folder.

## Custom domain (www.tarablus.co.il)

The [CNAME](CNAME) file tells GitHub Pages to serve this site at
`www.tarablus.co.il`. To finish wiring it up:

1. At your domain's DNS provider, add a `CNAME` record:
   - Host/name: `www`
   - Value/target: `tarablusyuval-source.github.io`
2. (Optional but recommended) Make the bare domain `tarablus.co.il` redirect
   to `www.tarablus.co.il` too, by adding these `A` records for the apex
   (`@`) host, pointing to GitHub Pages' IPs:
   - 185.199.108.153
   - 185.199.109.153
   - 185.199.110.153
   - 185.199.111.153
3. In the GitHub repo, go to Settings → Pages → set "Custom domain" to
   `www.tarablus.co.il` and save. Wait for DNS check to pass, then enable
   "Enforce HTTPS".
