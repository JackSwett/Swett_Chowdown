# Swett Family Recipes

A plaintext recipe site built with [Jekyll](https://jekyllrb.com/) and [Tailwind CSS](https://tailwindcss.com/), hosted on GitHub Pages.

**Live site:** [recipes.swett.org](https://recipes.swett.org)

Forked from [clarklab/chowdown](https://github.com/clarklab/chowdown).

## Project Structure

```
_recipes/       # Recipe markdown files
_components/    # Sub-recipes used inside other recipes
_layouts/       # Page templates (default, recipe, post, page)
_includes/      # Shared HTML partials (head.html with nav)
images/         # Recipe photos
plugins/        # Jekyll search plugin
```

## Local Development

Requires Ruby 3.0+ and Bundler.

```bash
# Install dependencies (first time only)
bundle install

# Serve locally
bundle exec jekyll serve --watch --baseurl ""
```

View at [http://127.0.0.1:4000](http://127.0.0.1:4000)

> **Note:** The `--baseurl ""` flag is required. The production `baseurl` in `_config.yml` is set to the full site URL, which breaks local routing. The override makes links work on localhost.

## Deploying to GitHub Pages

Push to the `gh-pages` branch. GitHub Pages builds and deploys automatically.

```bash
git push origin gh-pages
```

## Adding a Recipe

Create a new `.md` file in `_recipes/` (or `_components/` for sub-recipes like sauces and fillings). See [`STYLE_GUIDE.md`](STYLE_GUIDE.md) for all formatting rules, examples, and conventions.