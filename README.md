# 🌿 Paradise Nursery

> A responsive plant-shop web app built with **React 19**, **Redux Toolkit** and **Vite**. Browse aromatic and medicinal plants, add them to a cart, and manage quantities with live totals.

<img width="1611" height="892" alt="image" src="https://github.com/user-attachments/assets/1895c2f0-d9ec-4721-b1a6-35bf8c414930" />



## Overview

Paradise Nursery is a single-page e-commerce front end for a plant nursery. Visitors land on a hero page, browse plants grouped by category, and build a cart. Cart state is managed globally with Redux Toolkit, so the navbar counter, product cards and cart page always stay in sync.

The project shows how to structure a small React app with client-side routing, a centralized store, reusable components and static deployment to GitHub Pages.

## Features

- **Landing page** with a hero banner and a "Shop Now" call to action
- **Product catalog** with 8 plants in two categories:
  - 🌸 **Aromatic:** Lavender, Rosemary, Mint, Jasmine
  - 🌿 **Medicinal:** Aloe Vera, Tulsi (Holy Basil), Neem, Ashwagandha
- **Add to cart** from any product card. Adding the same plant again increments its quantity instead of duplicating the row.
- **Cart management:** increase and decrease quantity (never below 1), delete an item, or clear the whole cart
- **Live cart badge** in the navbar showing the total number of items
- **Order total** calculated from the cart contents
- **Empty-cart state** with a friendly message
- **Responsive layout** using CSS Grid (`auto-fit` / `minmax`) for the product grid
- **GitHub Pages ready** with `HashRouter` and a configured Vite base path

## Tech stack

| Area | Technology |
|---|---|
| UI library | React 19 |
| Build tool | Vite 7 |
| State management | Redux Toolkit + React-Redux |
| Routing | React Router v7 (`HashRouter`) |
| Styling | Plain CSS (Flexbox and Grid) |
| Linting | ESLint 9 (react-hooks, react-refresh) |
| Deployment | GitHub Pages via `gh-pages` |

## Routes

| Path | Page |
|---|---|
| `/` and `/home` | Landing page |
| `/products` | Product listing |
| `/cart` | Shopping cart |

`HashRouter` is used so client-side routes work on GitHub Pages without server-side rewrites (URLs look like `.../#/products`).

## State management

The cart lives in a single Redux slice (`src/redux/cartSlice.js`). Each item is `{ name, img, quantity }`.

| Action | Effect |
|---|---|
| `addToCart` | Adds a new item with `quantity: 1`, or increments it if it already exists |
| `increaseQuantity` | Increments an item's quantity |
| `decreaseQuantity` | Decrements an item's quantity, with a floor of 1 |
| `removeFromCart` | Removes an item |
| `clearCart` | Empties the cart |

The navbar reads the total item count with `useSelector`, and the cart page derives the order total from the same state.

## Project structure

```
paradise-nursery/
├── public/
├── src/
│   ├── assets/               # Plant photos and background images
│   ├── pages/
│   │   ├── LandingPage.jsx   # Hero section and CTA
│   │   ├── ProductListing.jsx# Categories and PlantCard component
│   │   └── CartPage.jsx      # Cart items, totals, actions
│   ├── redux/
│   │   ├── cartSlice.js      # Cart reducers and actions
│   │   └── store.js          # configureStore
│   ├── App.jsx               # Router and routes
│   ├── Navbar.jsx            # Navigation with live cart count
│   ├── main.jsx              # Entry point, Redux Provider
│   └── styles.css            # Global styles
├── index.html
├── vite.config.js            # base: '/nursery-app/'
└── package.json
```

## Getting started

**Prerequisites:** Node.js 20.19+ (or 22.12+) and npm.

```bash
# 1. Clone the repository
git clone https://github.com/Syeda-Fiza-Gilani/paradise-nursery.git
cd nursery-app/paradise-nursery

# 2. Install dependencies
npm install

# 3. Start the dev server
npm run dev
```

Because `vite.config.js` sets `base: '/nursery-app/'`, the dev server is served at **http://localhost:5173/nursery-app/**.

### Available scripts

| Command | Description |
|---|---|
| `npm run dev` | Start the Vite dev server with HMR |
| `npm run build` | Create a production build in `dist/` |
| `npm run preview` | Preview the production build locally |
| `npm run lint` | Run ESLint |
| `npm run deploy` | Build and publish `dist/` to GitHub Pages |

## Deployment (GitHub Pages)

1. In `vite.config.js`, set `base` to `'/<your-repo-name>/'`.
2. Run:
   ```bash
   npm run deploy
   ```
   The `predeploy` script builds the app and `gh-pages -d dist` publishes it to the `gh-pages` branch.
3. In the repository, go to **Settings → Pages** and select the `gh-pages` branch as the source.

## Roadmap

- [ ] Persist the cart across refreshes (`localStorage` or `redux-persist`)
- [ ] Move products into a data model with a `price` field, instead of a flat per-plant price
- [ ] Functional checkout flow (form and order summary)
- [ ] Search, category filter and sorting on the product page
- [ ] Toast feedback and disabled states on "Add to Cart"
- [ ] Unit tests for the cart reducers (Vitest) and component tests (React Testing Library)
- [ ] Accessibility pass (focus states, aria-labels on quantity buttons)

## Author

Built by Syeda Fiza Gilani.

## License

MIT
