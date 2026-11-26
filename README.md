# Forkify

A recipe app where you search over 1,000,000 recipes, adjust servings, bookmark favourites and upload your own. Built with **vanilla JavaScript (ES2022)** using the **MVC architecture**, bundled with **Parcel**.

**Live demo:** [forkify-beta-coral.vercel.app](https://forkify-beta-coral.vercel.app)

## Features

- **Search** recipes by ingredient or dish, with paginated results (10 per page).
- **Recipe details** with ingredients, cooking time and a link to the original directions.
- **Update servings.** All ingredient quantities are recalculated instantly.
- **Bookmarks** are saved in `localStorage` and survive page reloads.
- **Upload your own recipe** through a modal form. It's sent to the API with a personal key and appears in your search results, marked with a user icon.
- **URL hash routing.** Every recipe has its own `#id` URL, so you can share or reload it.
- **Error and loading states** for every network request, with a request timeout.

## Architecture

The app follows **Model–View–Controller** with a publisher–subscriber pattern for events:

| Layer | Files | Responsibility |
|---|---|---|
| **Model** | `model.js` | App state, API calls, bookmarks in `localStorage` |
| **Views** | `views/*.js` | One class per UI part, all extending a shared `View` base class with `render`, `update` (DOM diffing) and spinner/error helpers |
| **Controller** | `controller.js` | Connects user events to model updates and view rendering |
| **Helpers** | `helpers.js`, `config.js` | Generic `AJAX` function with timeout, constants |

![Architecture](forkify-architecture-recipe-loading.png)

## Tech stack

| | |
|---|---|
| Language | JavaScript (ES modules, classes, private fields, async/await) |
| Styling | Sass |
| Bundler | Parcel 2 |
| Polyfills | core-js, regenerator-runtime |
| API | [Forkify API v2](https://forkify-api.jonas.io) |

## Getting started

```bash
git clone https://github.com/Abdel-Fadeel/Forkify.git
cd Forkify
npm install
npm start
```

Then open http://localhost:1234.

| Command | What it does |
|---|---|
| `npm start` | Start the Parcel dev server |
| `npm run build` | Build for production into `dist/` |

## Project structure

```
src/
├── js/
│   ├── controller.js
│   ├── model.js
│   ├── config.js
│   ├── helpers.js
│   └── views/      # View base class + search, results, pagination, recipe, bookmarks, addRecipe
├── sass/
└── img/
```

## Author

**Abdel-Fadeel Hamdy**, Front-End Engineer · [GitHub](https://github.com/Abdel-Fadeel)
