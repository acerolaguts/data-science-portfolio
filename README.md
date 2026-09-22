# Data Science Portfolio — Andrew Davis

Plain HTML and one CSS file. No build step, no JavaScript, no dependencies.
GitHub Pages serves the files as they are:
<https://acerolaguts.github.io/data-science-portfolio/>

Edit a file, commit, push.

## Files

```
index.html               Home: intro, plus the project and writing lists
projects.html            Project list
blog.html                Post list
projects/*.html          One file per project write-up
blog/*.html              One file per post
404.html                 Shown for a bad URL
assets/css/style.css     All styling. Colors and fonts are the first block
.nojekyll                Tells GitHub Pages to serve the files as-is
```

## Adding a project or a post

Nothing is generated, so it's two steps.

**1. Copy an existing page.**

```bash
cp projects/nc-nursing-home-ratings.html projects/my-new-project.html
```

Open it and replace the `<title>`, the `<meta name="description">`, the
`<link rel="canonical">` URL, and everything between `<main>` and `</main>`.
Leave the header and footer alone, they're identical on every page.

For a post, copy `blog/what-does-data-science-mean-to-me.html` instead.

**2. Add it to the lists.** In `projects.html` (or `blog.html`), copy the
existing `<li>` and point it at the new file. Newest at the top.

```html
<li>
  <h3><a href="projects/my-new-project.html">Title</a></h3>
  <p class="meta">November 2026 · DTSC 2301</p>
  <p>A sentence on what you asked and what you found.</p>
</li>
```

Then paste the same `<li>` into `index.html` so it shows on the home page.

## What's available inside a write-up

Everything in the `<div class="prose">` is normal HTML. Headings are `<h2>`,
paragraphs are `<p>`. Three extras are styled for you:

```html
<!-- Image with a caption -->
<figure>
  <img src="https://..." alt="What the image shows" loading="lazy">
  <figcaption>Short caption.</figcaption>
</figure>

<!-- Indented note, for disclaimers and limitations -->
<div class="note">
  <p>Text here.</p>
</div>

<!-- Column or variable names, inline -->
<code>overall_rating</code>
```

For a block of code use `<pre><code>...</code></pre>`, and write `&lt;` for `<`
and `&amp;` for `&` inside it.

## Changing the look

The top of `assets/css/style.css`:

```css
--bg:    #fdfcfa;   /* page background   */
--text:  #1c1c1c;   /* body text         */
--muted: #6b6b6b;   /* dates, captions   */
--rule:  #e3e0da;   /* the thin lines    */
--link:  #2f5d50;   /* links             */
```

Fonts are system fonts, so nothing downloads and the page loads instantly. Body
text is your OS sans-serif; write-ups are set in Georgia for reading.

## Previewing locally

```bash
python3 -m http.server 8000
```

Then open <http://localhost:8000>, or just double-click `index.html`.
