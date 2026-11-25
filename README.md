# 🌿 Paradise Nursery

A plant-shop web app built with React, Redux Toolkit, and Vite. You can browse aromatic and medicinal plants, add them to a cart, and change quantities with live totals. I built it to practice global state management in React.

<img width="1611" height="892" alt="Paradise Nursery screenshot" src="https://github.com/user-attachments/assets/1895c2f0-d9ec-4721-b1a6-35bf8c414930" />

## Features
- Landing page with a hero banner and a "Shop Now" button
- 8 plants in two categories: aromatic (Lavender, Rosemary, Mint, Jasmine) and medicinal (Aloe Vera, Tulsi, Neem, Ashwagandha)
- Add to cart, where adding the same plant again increases its quantity instead of creating a duplicate row
- Increase, decrease, remove, or clear items in the cart
- Navbar badge that shows the total item count
- Order total and an empty-cart message
- Responsive product grid with CSS Grid

## Built With
React 19, Redux Toolkit, React Router v7 (`HashRouter`), Vite, plain CSS, ESLint, GitHub Pages

## What I Learned
- Managing cart state in one Redux slice, so the navbar, product cards, and cart page stay in sync
- Setting up client-side routing, and why `HashRouter` works on GitHub Pages
- Splitting an app into pages and reusable components
- Deploying a Vite app to GitHub Pages with `gh-pages`

## Run It
```bash
git clone https://github.com/Syeda-Fiza-Gilani/nursery-app.git
cd nursery-app
npm install
npm run dev
```
Then open `http://localhost:5173/nursery-app/` (the `base` path in `vite.config.js` adds the `/nursery-app/` part).

Use `npm run deploy` to publish to GitHub Pages.

## Next Up
- Keep the cart after a page refresh (`localStorage`)
- Checkout flow
- Search, filter, and sorting
- Tests for the cart reducers

Built by [Syeda Fiza Gilani](https://github.com/Syeda-Fiza-Gilani) · MIT License
