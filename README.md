# Scroll-Driven Hero Section Animation

A hero section where a top-down car drives across the screen as you scroll. The car, the green progress trail, the spinning tyres and the text reveal are all controlled by scroll position, not by time.

- **Live demo:** `https://sahileweb.github.io/scroll-hero-animation-itzfiz-/`

## Tech stack

- HTML, CSS, JavaScript
- [GSAP](https://gsap.com/) and ScrollTrigger (loaded from cdnjs)
- Tailwind CSS (CDN) for layout and typography

## How it works

All the scroll animation lives in one GSAP timeline with a single `ScrollTrigger`:

```js
scrollTrigger: {
  trigger: "#hero",
  start: "top top",
  end: () => "+=" + innerHeight * (innerWidth < 768 ? 1.2 : 1.8),
  pin: true,
  scrub: 1,
  invalidateOnRefresh: true,
}
```

- **Pinned hero:** the hero stays fixed while the user scrolls through the animation.
- **Scrub:** `scrub: 1` ties the timeline to scroll progress with about one second of smoothing. Scrolling back up reverses everything.
- **Car:** moves from the left end of the road to the right end (`xPercent` 0 to 100). The wrapper is exactly "road width minus car width" wide, so the car stops at the road's end at any screen size.
- **Green trail:** a bar that grows with `scaleX` on the same timeline, so it stays behind the car.
- **Tyres:** four tyres sit behind the car image. Their tread bars scroll in step with the distance travelled, so the tyres look like they are rolling. An amber marker bar makes the direction easy to follow.
- **Text reveal:** hidden at the start, then revealed in this order as the car moves:
  `WELCOME` → `98%` → `3x` → `ITZ` → `45%` → `FIZZ` → `120+`
- **Intro:** on page load only the car and road fade in. The text stays hidden until scroll reveals it.

## Performance

- Only `transform` and `opacity` are animated, so there is no layout reflow while scrolling.
- No custom scroll listeners. ScrollTrigger handles the updates.
- `prefers-reduced-motion` is respected: the animation is skipped and everything is shown.

## Responsive behaviour

- Car size is set with a CSS variable (`--car-w`) at three breakpoints.
- The scroll distance is shorter on mobile.
- Content is lifted above the car so the text never sits behind the tyres.

## Project structure

```
.
├── index.html
├── README.md
└── assets/
    └── car.webp      # top-view car, cropped and rotated to face right
```

## Run locally

Open `index.html` in a browser, or serve the folder with a local server (for example the VS Code Live Server extension). Keep the `assets` folder next to `index.html`, or the car image will not load.

## Deploy on GitHub Pages

1. Push `index.html` and the `assets` folder to the root of a public repository.
2. Go to **Settings → Pages**.
3. Set **Source** to **Deploy from a branch**, then choose branch `main` and folder `/ (root)`.
4. Open the link shown at the top of the Pages settings.

