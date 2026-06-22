# Recipe Style Guide

Rules for writing and formatting recipes in this repository. Follow these conventions so the site renders consistently and search works correctly.

For anything not covered here, defer to the **AP Stylebook — Food Guidelines** section as the authoritative reference for recipe writing style.

---

## File Naming

- Use `snake_case.md` for filenames: `banana_bread.md`, `cinnamon_rolls.md`
- No spaces, no capital letters in filenames
- Place recipes in `_recipes/` and sub-recipes in `_components/`

## Frontmatter

Every recipe starts with YAML frontmatter between `---` fences. Keep a blank line after the opening `---`.

```yaml
---

layout: recipe
title: "Banana Bread"
image: banana-bread.jpg
imagecredit: https://example.com/photo
tags: [breakfast, baking]
yield: "1 loaf"
servings: 8
calories: 250

ingredients:
- 2 cups (240 grams) all-purpose flour
- 1/2 cup (100 grams) granulated sugar
- 2 large eggs

components:
- Bolognese Sauce
- Béchamel Sauce

directions:
- Preheat the oven to 350°F (175°C). Position a rack in the center of the oven.
- Mix dry ingredients in a large bowl.
- Bake for 55 to 60 minutes.

---
```

### Required Fields

| Field | Notes |
|-------|-------|
| `layout` | Always `recipe` |
| `title` | In double quotes. Title Case. |
| `tags` | YAML inline array: `tags: [breakfast, baking]`. Lowercase. |
| `yield` | In double quotes: `yield: "1 loaf"` or `yield: "12 cookies"` |
| `servings` | Integer. How many servings the recipe makes. |
| `ingredients` | List of strings |
| `directions` | List of strings |

### Optional Fields

| Field | Notes |
|-------|-------|
| `image` | Filename only (e.g. `banana-bread.jpg`). Photo goes in `images/`. |
| `imagecredit` | URL to the image source |
| `calories` | Integer. Calories per serving. Leave blank if unknown. |
| `components` | List of component recipe titles (must match titles in `_components/`) |
| `notes` | List of strings for tips, storage instructions, etc. |

## Tags

Tags are a **YAML inline array** — this is critical for the site to parse them correctly.

```yaml
# CORRECT — parsed as separate tags
tags: [breakfast, baking]

# WRONG — parsed as a single string "breakfast, baking"
tags: breakfast, baking
```

Use lowercase, short terms. Common tags:

- **Meal type:** `breakfast`, `lunch`, `dinner`, `dessert`, `snack`
- **Category:** `baking`, `bread`, `pasta`, `soup`, `salad`, `sauce`, `pastry`, `cookie`
- **Protein:** `meat`, `chicken`, `pork`, `seafood`, `vegan`, `vegetarian`
- **Cuisine:** `mexican`, `italian`, `french`, `american`

Reuse existing tags before inventing new ones.

## Fractions

Use **plain text fractions**: `1/2`, `1/3`, `1/4`, `3/4`, `2/3`.

Do NOT use unicode fractions (`¹/₂`, `³/₄`). They look nice but cause issues with search and copy-paste.

Mixed numbers: `1-1/2`, `2-1/4` (hyphen between whole number and fraction).

## Ingredients

### Ordering

List ingredients **in the order they are used in the directions**. If the dough calls for flour first, flour is listed first.

### Cross-Check Rule

**Every ingredient in the ingredient list must appear in the directions, and every ingredient mentioned in the directions must appear in the ingredient list.** Always double-check this before finalizing a recipe. Missing or phantom ingredients are the most common recipe error.

### Format

- One ingredient per line, starting with the quantity
- Format: `[quantity] [unit] [ingredient], [preparation]`
  - `1 medium onion (170 grams), finely diced`
  - `2 cups (240 grams) all-purpose flour`
  - `1 clove garlic, minced`
- Optional ingredients: prefix with `(optional)` — e.g. `(optional) 1 cup chopped walnuts`

### Specificity

Be explicit about ingredient attributes when they affect the outcome:
- `large eggs` not just `eggs`
- `unsalted butter` not just `butter`
- `all-purpose flour` not just `flour`
- `fine sea salt` or `kosher salt` not just `salt` (unless truly any salt works)
- `unsifted` or `sifted` when it matters

### Measurements and Units

**Volume** — Use US customary, always spelled out: `tablespoon`, `teaspoon`, `cup`, `quart`, `gallon` (never `tbsp`, `tsp`, `c`, `qt`, `gal`). Metric volume (milliliters) is also acceptable.

**Weight** — Use metric (grams, kilograms) for all weights. **Exception:** US pounds are acceptable for large quantities (e.g. `4 pounds russet potatoes`). Never use ounces for weight — use grams instead.

**Parenthetical equivalents** are encouraged when helpful:
- `2 cups (240 grams) all-purpose flour` — volume primary, metric weight secondary
- `450 grams peanut butter` — metric weight only is fine
- `1 pound (450 grams) ground beef` — pounds with metric equivalent

```
# CORRECT
- 1 medium onion (170 grams), finely diced
- 450 grams peanut butter
- 2 cups (240 grams) all-purpose flour
- 1 pound (450 grams) ground beef

# WRONG
- 6 oz tomato paste        (use grams, not ounces)
- 12 oz onion              (use grams, not ounces)
- 1 c flour                (spell out cup)
- 2 tbsp butter            (spell out tablespoon)
```

## Directions

- One step per list item
- Write in imperative mood: "Preheat", "Mix", "Bake" — not "You should preheat"
- Use full sentences with periods at the end
- Keep steps in chronological order
- Spell out all measurements in directions too: `tablespoon` not `tbs.`
- Remember the **cross-check rule**: every ingredient mentioned here must be in the ingredient list, and vice versa

### Temperatures

Always use the `°F` symbol with a Celsius equivalent in parentheses. No space before the degree symbol.

```
# CORRECT
Preheat the oven to 350°F (175°C).

# WRONG
Preheat the oven to 350 degrees F.
Preheat the oven to 350° F.
Preheat the oven to 350 degrees Fahrenheit.
```

### Oven Rack Position

Always state the rack position when using an oven:
- `Position a rack in the center of the oven.`
- `Adjust rack to lower third of the oven.`

### Time Ranges

Always **spell out** time ranges with "to" — never use a hyphen for ranges:

```
# CORRECT
Bake for 25 to 30 minutes.
Let rise for 1 to 2 hours.

# WRONG
Bake for 25-30 minutes.
Bake for 25–30 minutes.
```

## Body Content

Everything after the closing `---` is body content. It appears as the recipe description on the page.

- Use this for origin stories, tips, attribution, or personal notes
- Keep it brief — a sentence or two is ideal
- Example: `This recipe comes from Oma.`

## Images

- Place in the `images/` directory at the project root
- Use lowercase filenames with hyphens or descriptive names: `banana-bread.jpg`
- Prefer `.jpg` or `.jpeg` for photos
- No specific size requirement, but keep files reasonable (under 1 MB)

## Component Recipes

A component is a sub-recipe used inside another recipe (e.g. a filling or sauce).

- File goes in `_components/`
- Uses `layout: recipe` (same as regular recipes)
- The parent recipe references it by exact title in the `components` list
- The component title in `_components/` must exactly match the string in the parent's `components` list
