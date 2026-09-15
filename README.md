# 🍽️ Random Lunch Generator

A simple, single-page web app that randomly picks a lunch idea for you at the click of a button — complete with a matching Font Awesome icon.

**Course project for LLM4RecSys.**

## Features

- One-click random lunch selection from 12 dishes
- Animated "thinking" loading state before revealing the result
- Smooth fade-in animation when a new dish appears
- Fully responsive layout (mobile-friendly)
- Automatically suggests a lunch on page load

## Live Demo

🔗 https://gogolev1307.github.io/random-lunch-generator/


## How It Works

The app keeps a `lunchMenu` array of 12 dishes, each with a `name` and a Font Awesome `icon` class. When the **Generate Lunch!** button is clicked:

1. The display briefly shows a spinning "Thinking..." state.
2. After a 500ms delay, a random index into `lunchMenu` is picked with `Math.random()`.
3. The dish name and its icon are rendered into the page, with a CSS fade-in animation.

The same function also runs once automatically on page load, so a dish is already shown before the user clicks anything.

## Bug Fix

**Bug:** When the randomly selected dish was **Pasta**, **Soup**, or **Ramen**, no icon appeared — only the dish name was visible.

**Root cause:** The `lunchMenu` array referenced Font Awesome class names that don't exist in Font Awesome **Free 6.4.0** (the version loaded via the CDN link in `<head>`):

| Dish  | Broken class        | Problem                                   |
|-------|----------------------|--------------------------------------------|
| Pasta | `fas fa-pasta`       | This icon does not exist in Font Awesome   |
| Soup  | `fas fa-bowl`        | This icon does not exist in Font Awesome   |
| Ramen | `fas fa-bowl-hot`    | Not part of the Free 6.4.0 icon set        |

Since these classes don't map to any real icon glyph, the browser rendered an empty `<i>` element — no visible icon, just blank space.

**Fix:** Each broken class was swapped for a real Font Awesome Free 6.4.0 Solid icon with a similar meaning:

| Dish  | Fixed class            |
|-------|--------------------------|
| Pasta | `fas fa-plate-wheat`     |
| Soup  | `fas fa-bowl-food`       |
| Ramen | `fas fa-bowl-rice`       |

**How to verify:** Open the app and click **Generate Lunch!** repeatedly (or reload the page a few times) until each of Pizza, Sushi, Burger, Salad, Tacos, Ramen, Sandwich, Pasta, Curry, Steak, Soup, and BBQ has appeared at least once. Every dish should show both its name and an icon — no blank icon slots.

## Project Structure

```
random-lunch-generator/
├── index.html   # All markup, styles, and logic (single file)
└── README.md    # This file
```

## Usage

### Run locally
1. Clone or download this repository.
2. Open `index.html` directly in any modern browser (no build step or server required).

### Deploy on GitHub Pages
1. Push this repository to GitHub.
2. Go to **Settings → Pages**.
3. Under **Build and deployment → Source**, select **Deploy from a branch**.
4. Choose the `main` branch and `/ (root)` folder, then click **Save**.
5. Wait a minute or two, then visit the URL GitHub gives you.

## License

This project is licensed under the [MIT License](https://opensource.org/licenses/MIT).
