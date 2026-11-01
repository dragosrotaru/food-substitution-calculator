# Food substitution calculator

A small web calculator built for Absolute Coaching, a nutrition coaching business, in 2017. Clients pick a food from their meal plan, enter its weight, and get a list of substitutes ranked by how closely their macronutrients match, plus the amount of the substitute that provides the same calories.

> Archived: no longer maintained. Kept for reference.

## How it works

- `data.csv` holds a food list with fat, protein, carbs and calories per gram and a category. It was built from USDA nutrient data (`USDA.csv` / `USDA.xlsx`) and a list of foods specified by the client.
- `mainscript.js` loads the CSV with Papa Parse and drives the UI: searchable dropdowns, gram/ounce units and a reset button.
- When a food is chosen, every other food is scored by the sum of absolute differences in protein, carbs and fat per gram. Foods in the same category get their score halved, and the substitute list is sorted by score.
- The result is the substitute weight with equal calories: `amount x (cal/g of original) / (cal/g of substitute)`.

`script.js` is an earlier version that searched foods live through the USDA NDB API instead of a local CSV. It is not loaded by `index.html`. It needs an api.data.gov key in place of `YOUR_USDA_API_KEY`, but the NDB API it calls has since been retired, so it no longer works as-is.

## Tech stack

Plain HTML, CSS and JavaScript, with Papa Parse for CSV parsing. No build step.

## Running locally

Serve the folder with any static server, for example:

```sh
python3 -m http.server
```

Note that `mainscript.js` fetches `data.csv` from the original hosted URL (`absolutecoachingcalculator.rotaru.co`). To run it locally, change that path to `data.csv`.

## Context

Client project for Absolute Coaching, built in March-April 2017 with dataset and style updates through September 2017. It was hosted as a standalone page linked from the client's site.
