# Family Cookbook

A single-page cookbook for the dishes two people actually know how to cook. No build step, no dependencies — one self-contained HTML file per language, plus the recipes as JSON.

https://claude.ai/code/artifact/3054650e-5088-4c4c-b5c1-d02fbb25fe5c

## What it does

- **21 recipes**, each with an ingredient list, numbered method, and a short "what matters" note — the one or two details that decide whether the dish works (scrape the pith out of bitter melon; add lime juice to tom yum off the heat; never crowd roast potatoes).
- **Who cooks what.** Every dish is tagged to one cook or both. Two dishes overlap.
- **Filter and search** by cook, by kind (stir-fry, braise, soup, congee & noodles, dough & rice, steamed, oven), or by any word in a name, ingredient or step. The English page also matches the original Chinese names, so searching `酸菜` works.
- **Add a dish** to hold its place. It saves with a *recipe to come* marker until the method gets written up.
- **Light and dark**, and readable down to phone width.

## Repo layout

```
index.html              English edition — complete, self-contained page
zh/index.html           Chinese edition — same recipes, 中文
data/recipes.en.json    the recipes on their own
data/recipes.zh.json
docs/                   screenshots
```

Each HTML file carries its own CSS, JavaScript and recipe data. Open it from disk, host it anywhere static, or email it to someone — it works with no server.

## How saving works

The page has two modes, and it tells you which one it is in:

| Where it runs | What happens when you add a dish |
| --- | --- |
| Hosted on claude.ai as an Artifact | The page rewrites itself and publishes a new version. The dish is there on every device. |
| Anywhere else (GitHub Pages, local file) | The dish is kept in that browser's `localStorage`. It survives a refresh, but stays on that one device. |

In both modes the dish is written to `localStorage` *first*, so a failed save never loses it. On the next load, anything already baked into the page is pruned from the local copy, so nothing is ever duplicated.

## Editing recipes

Recipes live in a JSON block inside each HTML file (`<script type="application/json" id="data">`), mirrored in `data/`. One dish looks like this:

```json
{
  "id": "haoyou-caixin",
  "n": "Choy Sum in Oyster Sauce",
  "zh": "蚝油菜心",
  "w": "b",
  "c": "Stir-Fry",
  "t": "10 min",
  "i": ["400g choy sum", "…"],
  "s": ["Bring a pot of water to a boil with salt and a teaspoon of oil…", "…"],
  "p": ["Oyster sauce turns bitter if you cook it long — 20 seconds is the whole window."]
}
```

`w` is who cooks it: `b`, `d`, or `both`. `i` is ingredients, `s` is steps, `p` is the notes. A dish with an empty `s` renders as *recipe to come*.

## 中文

[English]((https://claude.ai/code/artifact/3054650e-5088-4c4c-b5c1-d02fbb25fe5c)) ·

21 道菜，每道带食材、分步做法，和一两条真正决定成败的窍门。可以按人、按分类筛，也能搜食材和做法。新加的菜会先存进浏览器，再尝试写回页面本身——两条路互为备份。

## License

MIT — see [LICENSE](LICENSE). The recipes are home cooking; do what you like with them.
