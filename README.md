# Tarablus

A minimal single-page site that displays one full-screen horizontal image.

## Structure

```
Tarablus/
├── index.html          # Page markup, loads the image
├── css/
│   └── style.css       # Full-screen responsive image styling
├── images/
│   └── feet.jpg        # The displayed image (currently a sample placeholder)
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

## Local preview

Open [index.html](index.html) directly in a browser, or serve the folder
with any static file server, e.g.:

```
npx serve .
```

## Publishing with GitHub Pages

Push this repository to GitHub named `tarablus`, then enable GitHub Pages
(Settings → Pages) for the `main` branch, root folder.
