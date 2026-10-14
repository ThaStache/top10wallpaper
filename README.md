# Top Ten Wall

Turn your Apple Music listening history into a desktop wallpaper of your 10 most played albums, for any year or all time. It's a static site with no server, no database, and no API keys, so it runs free on GitHub Pages.

## What's in this repo

| File | What it is |
| --- | --- |
| `index.html` | The wallpaper maker |
| `examples.html` | Gallery of example wallpapers in every layout and background |
| `examples-data.js` | The albums shown on the examples page (sample data until you replace it) |
| `about.html` | About page |
| `faq.html` | FAQ page |
| `.nojekyll` | Tells GitHub Pages to serve the files as-is |
| `.gitignore` | Keeps Mac `.DS_Store` files out of the repo |

## 1. Get the files onto your Mac

1. On your Mac, open this chat at claude.ai and download `top-ten-wall.zip`. It lands in your Downloads folder.
2. Double-click the zip to unzip it. You now have a `top-ten-wall` folder.
3. Move it somewhere permanent, like your Documents folder or a `Projects` folder.

Note: `.nojekyll` and `.gitignore` are hidden files. In Finder, press **Cmd + Shift + .** to see them. They're there even if you can't see them.

## 2. Preview it on your Mac

Open Terminal and run:

```
cd ~/Documents/top-ten-wall
python3 -m http.server 8000
```

Then visit http://localhost:8000 in your browser. Press **Ctrl + C** in Terminal to stop it.

## 3. Publish to GitHub Pages

### Option A: GitHub Desktop (no command line)

1. Install GitHub Desktop from https://desktop.github.com and sign in.
2. Choose **File > Add Local Repository**, select the `top-ten-wall` folder, and click **create a repository** when it offers to.
3. Click **Publish repository**. Uncheck **Keep this code private** (GitHub Pages is free for public repos).

### Option B: Terminal

1. Create an empty public repository at https://github.com/new named `top-ten-wall`. Don't add a README.
2. Run:

```
cd ~/Documents/top-ten-wall
git init -b main
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/YOUR-USERNAME/top-ten-wall.git
git push -u origin main
```

### Turn on Pages

1. In the repository on GitHub, go to **Settings > Pages**.
2. Under **Build and deployment**, set Source to **Deploy from a branch**, branch **main**, folder **/ (root)**. Save.
3. After a minute or two, the site is live at `https://YOUR-USERNAME.github.io/top-ten-wall/`.

## 4. Put your own albums on the examples page

The examples page ships with made-up sample albums. To show your real Apple Music history:

1. Open your site (or the local preview) with `?export` at the end of the address, for example `http://localhost:8000/?export`. This shows an extra **Export for examples page** button that regular visitors don't see.
2. Drop your Apple Music export onto the page.
3. Pick **Plays** or **Time listened**, hide anything you don't want public, and add any covers that are missing or wrong.
4. Click **Export for examples page**. It downloads a new `examples-data.js`, including your covers.
5. Replace `examples-data.js` in your `top-ten-wall` folder with the new one.
6. Publish the change. In GitHub Desktop, write a summary like "Use my albums for examples," then click **Commit to main** and **Push origin**. In Terminal:

```
git add examples-data.js
git commit -m "Use my albums for examples"
git push
```

Only your top 10 lists (album names, artists, and play counts) are included in the file. Your full listening history is never saved.

## 5. Optional: use your own domain

1. In **Settings > Pages**, enter your domain under **Custom domain** and save.
2. At your domain registrar, add DNS records:
   - For `www`: a **CNAME** record pointing to `YOUR-USERNAME.github.io`
   - For the bare domain: four **A** records pointing to `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, and `185.199.111.153`
3. Once DNS updates (minutes to a day), check **Enforce HTTPS** in Settings > Pages.

GitHub's own docs list the current IP addresses, so double-check them when you set this up.

## Before you publish

Replace `[YOUR-EMAIL]` in `about.html` and `faq.html` with the address you want visitors to use.

## Getting Apple Music data

1. Go to https://privacy.apple.com and sign in.
2. Choose **Request a copy of your data** and select **Apple Media Services information**.
3. Apple emails you when it's ready, usually within a few days. Drop the zip onto the site.

## Notes

- Album art comes from the iTunes Search API, with MusicBrainz and the Cover Art Archive as a fallback. Both are free and need no keys.
- Visitors' listening data never leaves their browser.
- Top Ten Wall isn't affiliated with Apple. Album artwork belongs to its artists and labels.
