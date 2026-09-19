# dilet.dev

A plain HTML/CSS/JS personal site. No build step, no framework — every file
here is exactly what your browser loads.

## File map

```
dilet-site/
├── index.html                     Home page
├── about.html                     About page
├── resume.html                    Resume page (links to assets/resume.pdf)
├── contact.html                   Contact page
├── projects/
│   ├── index.html                 Projects list
│   ├── space-game.html
│   ├── competitive-programming.html
│   └── research.html
├── css/style.css                  All styles, one file
├── js/main.js                     Mobile nav toggle (the only JS on the site)
└── assets/                        Put images, your resume PDF, etc. here
```

Every page has a few `placeholder-note` boxes calling out exactly what to
replace (real email, GitHub/LinkedIn links, project media, resume file).
Search for `placeholder-note` across the project to find all of them before
you publish.

## 1. Preview it locally

You don't need a server for this to work, but a live-reloading preview makes
editing much less painful:

1. Open the `dilet-site` folder in VS Code (`File > Open Folder…`).
2. Install the **Live Server** extension (search for it in the Extensions
   panel, the puzzle-piece icon on the left sidebar).
3. Right-click `index.html` in the file explorer and choose
   **"Open with Live Server"**. It opens in your browser and refreshes
   automatically every time you save a file.

That's the whole loop: edit a file, save, look at the browser tab.

## 2. Put it on GitHub

1. Create a new **public** repo on GitHub (call it whatever you like — the
   repo name doesn't have to match the domain).
2. In the `dilet-site` folder, run:
   ```
   git init
   git add .
   git commit -m "Initial site"
   git branch -M main
   git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPO.git
   git push -u origin main
   ```

## 3. Deploy with GitHub Pages

1. On GitHub, go to the repo's **Settings → Pages**.
2. Under "Build and deployment", set **Source** to "Deploy from a branch",
   branch `main`, folder `/ (root)`. Save.
3. GitHub gives you a URL like `https://YOUR-USERNAME.github.io/YOUR-REPO/`
   within a minute or two — confirm the site loads there before moving on
   to the custom domain.

## 4. Point dilet.dev at it

Once you've registered `dilet.dev` (Porkbun, Namecheap, or Cloudflare
Registrar all work):

1. In the repo, create a file named `CNAME` (no extension) at the project
   root containing exactly:
   ```
   dilet.dev
   ```
   Commit and push it — GitHub Pages reads this file to know what domain
   to answer to.
2. In your registrar's DNS settings for `dilet.dev`, add:
   - Four **A** records for `@` pointing to GitHub Pages' IPs:
     `185.199.108.153`, `185.199.109.153`, `185.199.110.153`,
     `185.199.111.153`
   - One **CNAME** record for `www` pointing to
     `YOUR-USERNAME.github.io`
3. Back in the repo's **Settings → Pages**, enter `dilet.dev` as the custom
   domain and wait for the DNS check to go green (can take anywhere from a
   few minutes to a few hours), then enable **Enforce HTTPS**.

DNS propagation is the only genuinely slow part of this whole process —
if `dilet.dev` doesn't resolve right away, that's normal; give it some
time before troubleshooting further.

## Making changes later

Edit files locally, preview with Live Server, then:

```
git add .
git commit -m "Describe what changed"
git push
```

GitHub Pages automatically redeploys within a minute or two of every push
to `main` — no separate deploy step.
