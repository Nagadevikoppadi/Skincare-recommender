# Skincare-recommender
# ✦ Aura — Personalized Skincare Recommender

A single-file, client-side skincare recommender web app built with vanilla HTML, CSS (Tailwind CDN), and JavaScript. No backend, no build step — open the HTML file and it works.

---

## Features

- **Skin Type Quiz** — 5-question quiz that scores answers and recommends a skin type
- **Instant Recommendations** — select your skin type directly from the home page for immediate product recommendations
- **Personalized Routines** — curated AM/PM skincare routines with step-by-step guidance
- **Product Catalog** — browsable, filterable product collection with category filters and search
- **Expert Tips** — skin-type-specific expert advice shown alongside routines
- **Responsive Design** — mobile-first layout with a collapsible hamburger menu

---

## Tech Stack

| Layer | Technology |
|---|---|
| Markup | HTML5 |
| Styling | Tailwind CSS (CDN) + custom CSS |
| Fonts | Google Fonts — Cormorant Garamond, Inter |
| Logic | Vanilla JavaScript (no frameworks) |
| Routing | Single-page app with `display` toggling |

---

## Project Structure

```
index.html          # Entire application (single file)
│
├── <head>          # Tailwind config, custom CSS, font imports
├── <nav>           # Fixed navbar with mobile menu
│
├── #page-home          # Landing page with hero, skin type cards, features
├── #page-quiz          # 5-step quiz with progress bar
├── #page-recommendations   # Personalized AM/PM routine output
└── #page-products      # Full product catalog with filters
│
└── <script>        # All app data and logic
    ├── SKIN_TYPES[]        # 5 skin type definitions
    ├── PRODUCTS[]          # 19 product objects
    ├── TIPS{}              # Skin-type-specific expert tips
    ├── QUIZ_QUESTIONS[]    # Quiz question and option data
    ├── QUIZ_SCORING{}      # Answer-to-skin-type score mapping
    └── Functions           # Navigation, quiz, rendering, filtering
```

---

## Data Model

### Skin Types
Each skin type has: `id`, `name`, `icon`, `description`, `characteristics[]`

Supported: `oily` | `dry` | `combination` | `sensitive` | `normal`

### Products
Each product has: `id`, `name`, `brand`, `category`, `description`, `ingredients[]`, `suitableFor[]`, `benefits[]`, `price`, `rating`, `tags[]`

Categories: `cleanser` | `toner` | `serum` | `moisturizer` | `sunscreen` | `exfoliator` | `eye cream` | `mask`

### Quiz Scoring
Each answer maps to a skin type score object. The skin type with the highest cumulative score after all 5 questions wins.

---

## Key Functions

| Function | Purpose |
|---|---|
| `navigate(page, skinTypeId)` | SPA router — shows the target page, hides others |
| `initQuiz()` | Resets and starts the quiz |
| `quizSelect(qId, aId)` | Records an answer and re-renders the current step |
| `computeQuizResult()` | Tallies scores and returns the winning skin type ID |
| `initRecommendations(skinTypeId)` | Renders the routine page for a given skin type |
| `initProducts()` | Renders the full product catalog with filters |
| `filterProducts()` | Filters the product grid by category and search query |
| `renderProductCard(p)` | Returns HTML string for a single product card |

---

## Getting Started

1. Download or clone the repository
2. Open `index.html` in any modern browser
3. No installs, no server, no build step required

```bash
# Optional: serve locally for cleaner URL behaviour
npx serve .
# or
python -m http.server 8080
```

---

## Customisation

### Adding Products
Append a new object to the `PRODUCTS` array in the `<script>` block:

```js
{
  id: "p20",
  name: "My New Product",
  brand: "Brand Name",
  category: "serum",           // must match an existing category
  description: "...",
  ingredients: ["Ingredient A"],
  suitableFor: ["oily", "combination"],  // use skin type IDs or "all"
  benefits: ["Benefit 1"],
  price: 25.00,
  rating: 4.5,
  tags: ["new"]
}
```

### Adding a Quiz Question
Append to `QUIZ_QUESTIONS` and add a corresponding scoring key to `QUIZ_SCORING`. Update the `Step X of 5` label logic if the total count changes.

### Changing the Colour Scheme
All brand colours are defined in the `tailwind.config` block at the top of `<head>`. The primary accent colour is `#b07ba1` (mauve).

---

## Browser Support

Works in all modern browsers (Chrome, Firefox, Safari, Edge). No polyfills required.

---

## License

MIT — free to use, modify, and distribute.
