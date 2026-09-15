# 🍽️ Random Lunch Menu Generator

Tired of deciding what to eat for lunch? This web app eliminates the daily dilemma by randomly generating a lunch idea for you! Say goodbye to endless scrolling and "I don't know, what do you want?" conversations.

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-222222?style=for-the-badge&logo=githubpages&logoColor=white)

## ✨ Features

*   **Randomized Selection:** Get a completely random lunch suggestion with a single click.
*   **Visual Appeal:** Each suggestion is paired with a relevant Font Awesome icon for a better experience.
*   **Simple & Fast:** Lightweight and loads instantly. No ads, no sign-ups.
*   **Mobile-Friendly:** Responsive design that works perfectly on your desktop, tablet, or phone.

## 🚀 Live Demo

Check out the live application hosted on GitHub Pages:  
👉 **[LIVE DEMO](https://gogolev1307.github.io/random-lunch-generator/)** 👈

## 🛠️ How It Works

The core logic is simple:
1.  The app keeps a `lunchMenu` array of 12 dishes, each paired with a Font Awesome icon class (e.g., `{ name: "Pizza", icon: "fas fa-pizza-slice" }`).
2.  When the user clicks the **"Generate Lunch!"** button, a JavaScript function is triggered.
3.  This function picks a random index into `lunchMenu` using `Math.random()`.
4.  The selected dish's name and icon are dynamically displayed on the page, with a short "Thinking..." loading state and a fade-in animation.

## 🐛 Bug Fix

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

## 📁 Project Structure

```
random-lunch-generator/
├── index.html          # All markup, styles (in <style>), and logic (in <script>) — single file
└── README.md           # This file
```

## 🧩 Installation & Local Development

Want to run this locally? Follow these steps:

1.  **Clone the repository**
    ```bash
    git clone https://github.com/gogolev1307/random-lunch-generator.git
    ```
2.  **Navigate to the project directory**
    ```bash
    cd random-lunch-generator
    ```
3.  **Open it!**  
    Simply open the `index.html` file in your web browser. No complex build processes required!

## 🎯 How to Use

1.  Go to the live demo page or open `index.html` locally.
2.  Click the **"Generate Lunch!"** button.
3.  Watch as a random lunch idea appears on the screen.
4.  Can't decide? Just click the button again!

## 🤝 Contributing

Found a bug or have a great idea for a new feature? Contributions are welcome!
1.  Fork the Project.
2.  Create your Feature Branch (`git checkout -b feature/AmazingFeature`).
3.  Commit your Changes (`git commit -m 'Add some AmazingFeature'`).
4.  Push to the Branch (`git push origin feature/AmazingFeature`).
5.  Open a Pull Request.

Please feel free to add more menu items to the `lunchMenu` array in `index.html`!

## 📝 License

This project is licensed under the [MIT License](https://opensource.org/licenses/MIT).

## 🙏 Acknowledgments

*   Icons provided by [Font Awesome](https://fontawesome.com/).
*   Inspiration from the eternal question: "What do you want for lunch?"
