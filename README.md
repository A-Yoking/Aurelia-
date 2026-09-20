# Aurelis: dark luxury landing page template

A responsive, dark-mode landing page built with plain HTML and CSS (no build step, no JavaScript), ready for GitHub Pages.

Sections: hero with one CTA, services showcase, social proof (quotes, stats, partners), and a minimal contact form.

## Repository structure

```
.
├── index.html          # All page content
├── css/
│   └── style.css       # All styling; design tokens at the top
├── assets/
│   └── favicon.svg
├── .nojekyll           # Tells GitHub Pages to serve files as-is
└── README.md
```

## Preview locally

Open `index.html` in a browser, or serve the folder:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Customize

1. **Brand and copy**: edit the text in `index.html`. Search for "Aurelis" to rename the brand.
2. **Colors and fonts**: change the variables in the `:root` block at the top of `css/style.css` (`--ink`, `--cyan`, `--gold`, `--font-display`, and so on).
3. **Testimonials, stats and partner names** are placeholders. Replace them with real, verifiable content before going live.
4. **Contact form**: GitHub Pages is static and cannot receive form posts on its own.
   - Create a free form at [Formspree](https://formspree.io) (or Basin, Web3Forms, Getform).
   - In `index.html`, replace `https://formspree.io/f/your-form-id` with your endpoint.
   - Test it once from the live site.
5. **Social preview and URL**: update the `og:url` meta tag in `index.html`.
6. **Fonts**: the page loads Instrument Serif and Manrope from Google Fonts. To avoid third-party requests, download the fonts, place them in `assets/fonts/`, and replace the `<link>` tags with `@font-face` rules.

## Deploy to GitHub Pages

### 1. Create the repository and push the files

Create an empty repository on GitHub (public, or private if your plan supports Pages on private repos), then from this folder run:

```bash
git init
git add .
git commit -m "Initial landing page"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPO.git
git push -u origin main
```

You can also drag the files into a new repo using GitHub's **Add file → Upload files**. Keep the `css/` and `assets/` folders intact.

### 2. Turn on Pages

1. Open the repository on GitHub and go to **Settings → Pages**.
2. Under **Build and deployment**, set **Source** to **Deploy from a branch**.
3. Under **Branch**, choose `main` and the folder `/ (root)`, then click **Save**.

### 3. Visit your site

After a minute or two, the Pages settings show your live URL:

- Project repo: `https://YOUR-USERNAME.github.io/YOUR-REPO/`
- If the repo is named exactly `YOUR-USERNAME.github.io`: `https://YOUR-USERNAME.github.io/`

Every push to `main` redeploys automatically.

### Optional: custom domain

1. In **Settings → Pages → Custom domain**, enter your domain and save.
2. At your DNS provider, add a `CNAME` record pointing `www` to `YOUR-USERNAME.github.io`. For an apex domain, add the four GitHub Pages `A` records listed in [GitHub's docs](https://docs.github.com/pages/configuring-a-custom-domain-for-your-github-pages-site).
3. Once DNS resolves, tick **Enforce HTTPS**.

## Troubleshooting

| Problem | Fix |
| --- | --- |
| 404 on the live URL | Confirm `index.html` is in the folder selected under Pages, and that the branch is correct. |
| Page loads with no styling | Paths must stay relative (`css/style.css`, not `/css/style.css`), and file names are case-sensitive. |
| Changes not showing | Wait for the Pages deployment to finish (Actions tab), then hard refresh. |
| Form does nothing | The `action` URL still contains the placeholder `your-form-id`. |

## Accessibility notes

Includes a skip link, semantic landmarks, visible keyboard focus, labelled form fields, and respects `prefers-reduced-motion`. Glass surfaces fall back to a solid tint in browsers without `backdrop-filter`.
