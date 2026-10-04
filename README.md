# Scroll-Driven Hero Section Animation

A premium scroll-driven hero section where a top-down car drives across the screen as the user scrolls.

The **car, green progress trail, spinning tyres, and text reveals are all controlled by scroll position rather than time-based autoplay**.

## Live Demo

[View Live Demo](https://sahileweb.github.io/scroll-hero-animation-itzfiz-/)

## Tech Stack

* HTML
* CSS
* JavaScript
* GSAP
* GSAP ScrollTrigger
* Tailwind CSS

GSAP and ScrollTrigger are loaded via CDN, with Tailwind CSS used for layout and typography.

## Features

### Scroll-Driven Animation

The hero section is pinned while the user scrolls through the animation.

A single GSAP timeline controls the main interaction using ScrollTrigger:

```js
scrollTrigger: {
  trigger: "#hero",
  start: "top top",
  end: () => "+=" + innerHeight * (innerWidth < 768 ? 1.2 : 1.8),
  pin: true,
  scrub: 1,
  invalidateOnRefresh: true
}
```

### Car Movement

The top-down car travels from the left side of the road to the right side as the user scrolls.

Scrolling back up smoothly reverses the animation.

### Green Progress Trail

A green trail grows behind the car according to scroll progress, creating a clear visual connection between the user's scroll position and the animation.

### Rolling Tyres

Four tyres are positioned behind the car image. Their tread animation progresses with the car's movement to create a rolling effect.

### Text Reveal

The text remains hidden initially and is progressively revealed as the car moves:

```text
WELCOME → 98% → 3x → ITZ → 45% → FIZZ → 120+
```

### Intro Animation

On page load, the car and road fade in subtly.

The main text remains hidden until the user begins scrolling, keeping the scroll interaction as the primary focus.

## Performance

* Uses `transform` and `opacity` for animations to minimize layout reflow.
* No custom scroll event listeners.
* ScrollTrigger handles scroll-based updates.
* `scrub` provides smooth interpolation between scroll position and animation progress.
* `prefers-reduced-motion` is respected, displaying the content without the animation for users who prefer reduced motion.

## Responsive Design

The animation adapts to different screen sizes:

* Responsive car sizing using CSS variables
* Shorter scroll distance on mobile
* Adjusted content positioning for smaller screens
* Car and road scale appropriately across breakpoints

## Project Structure

```text
.
├── index.html
├── README.md
└── assets/
    └── car.webp
```

## Run Locally

Clone or download the repository and open `index.html` in a browser.

For the best experience, use a local development server such as the **VS Code Live Server extension**.

Make sure the `assets` folder remains next to `index.html` so the car image loads correctly.

## Deploy to GitHub Pages

1. Push `index.html` and the `assets` folder to the root of a public GitHub repository.
2. Go to **Settings → Pages**.
3. Under **Build and deployment**, select **Deploy from a branch**.
4. Select the `main` branch and `/ (root)` folder.
5. Save the settings.
6. Open the GitHub Pages URL provided by GitHub.



**Created by Sahil**
