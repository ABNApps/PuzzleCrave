# PuzzleCrave website

The public website for **PuzzleCrave: Brain Games**, an Android puzzle game published on Google Play by ABN Apps Team.

Served by GitHub Pages at <https://abnapps.github.io/PuzzleCrave/>.

| Page | Address | What it is for |
|---|---|---|
| `index.html` | `/` | Landing page describing the game |
| `privacy.html` | `/privacy.html` | The privacy policy. This is the URL given to Google Play |
| `support.html` | `/support.html` | Support and contact page, and answers to common questions |
| `assets/site.css` | | The whole stylesheet for all three pages |
| `assets/icon.png` | | The Google Play store icon, used as the logo and favicon |

The pages are plain HTML and CSS. They load no fonts, scripts, cookies, or trackers from anywhere, on purpose: a privacy policy for a game played by children should not itself be a way to watch people read it.

## Do not edit privacy.html by hand

Google Play requires the policy published here to say the same thing as the copy players read inside the app. To keep them identical, `privacy.html` is generated from the app's own policy text and should never be edited directly.

The game lives in a separate repository (Azure DevOps). From the root of that repository, run:

```
python .agents/handoff/play-store-release/publish-privacy-policy.py D:/Code/GitHub/ABNApps/PuzzleCrave
```

That reads `Unity/PuzzleCrave/Assets/PuzzleCrave/App/Resources/App/Legal/privacy-policy.txt`, refuses to run while the policy still has any `[placeholders]`, and rewrites `privacy.html`. Commit and push the result here.

So the order of work is always: change the policy in the game repository, rebuild the app, run the script, then push this repository.

## Turning on GitHub Pages

In this repository on GitHub: **Settings > Pages > Build and deployment**, source **Deploy from a branch**, branch **main**, folder **/ (root)**. The site appears at the address above a minute or two later.

`.nojekyll` tells GitHub Pages to publish the files exactly as they are instead of running Jekyll over them.
