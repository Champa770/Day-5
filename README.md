# Day-5
Semantic HTML5 &amp; Accessibility Basics
inline, block, div, inspect

---

**What "semantic" means**
A semantic tag describes *what its content is*, not just how it looks. `<div>` tells you nothing about the content inside it — it's a generic box. `<header>`, `<nav>`, `<article>` etc. tell you exactly what role that section plays on the page.

```html
<!-- non-semantic -->
<div class="header">...</div>

<!-- semantic -->
<header>...</header>
```

Both can look identical after styling — the difference is meaning, not appearance.

**Why it matters**

- Screen readers use semantic tags to help visually impaired users navigate ("jump to navigation", "jump to main content")
- Search engines use them to understand page structure (helps SEO)
- Other developers reading your code instantly understand the layout without guessing

**Core semantic layout tags**

```html
<header>Site logo, title, nav</header>
<nav>Navigation links</nav>
<main>The primary content of the page</main>
<section>A thematic grouping of content</section>
<article>Self-contained content — a blog post, news story</article>
<aside>Side content — related links, ads, sidebars</aside>
<footer>Copyright, contact info, footer links</footer>
```

**Typical page skeleton using semantic tags**

```html
<body>
  <header>
    <h1>My Website</h1>
    <nav>
      <ul>
        <li><a href="#">Home</a></li>
        <li><a href="#">About</a></li>
      </ul>
    </nav>
  </header>

  <main>
    <article>
      <h2>Blog Post Title</h2>
      <p>Content...</p>
    </article>

    <aside>
      <p>Related links</p>
    </aside>
  </main>

  <footer>
    <p>&copy; 2026 My Website</p>
  </footer>
</body>
```

**`<section>` vs `<article>` vs `<div>`**

- `<article>` — makes sense on its own, even if pulled out and placed elsewhere (a blog post, a product card)
- `<section>` — a thematic chunk of a page, usually has its own heading, doesn't necessarily stand alone
- `<div>` — no meaning at all, purely a styling/structure hook when nothing semantic fits

**Accessibility basics (a11y)**

*Alt text on images* — already covered, but this is the #1 accessibility rule:

```html
<img src="chart.png" alt="Bar chart showing sales growth from Jan to June">
```

*Labels on form inputs* — already covered too, same reasoning.

`*aria-label*` — gives an accessible name to something that has no visible text, like an icon button:

```html
<button aria-label="Close menu">✕</button>
```

*Using headings in order* — don't skip levels just for font size (`<h1>` → `<h3>` skipping `<h2>`). Screen reader users navigate by heading structure, and skipping breaks that mental map.

*Buttons vs links — use the right one*

```html
<a href="page.html">Go to page</a>   <!-- navigates somewhere -->
<button onclick="doSomething()">Submit</button>  <!-- triggers an action -->
```

Don't use a `<div>` or `<span>` styled to look like a button — it won't be keyboard-accessible or announced correctly by screen readers.

*Color contrast* — briefly mention: text needs enough contrast against its background to be readable (this becomes more relevant once we hit CSS, just plant the awareness now).

*Keyboard navigation* — a sighted-but-motor-impaired or keyboard-only user should be able to `Tab` through interactive elements (links, buttons, inputs) in a logical order. Native semantic elements get this for free; custom `<div>`-as-button does not.

**Common mistakes**

- Using `<div>` for everything even when a semantic tag fits perfectly
- Multiple `<h1>`s on one page, or skipping heading levels
- Icon-only buttons with no `aria-label`, so screen readers announce nothing useful
- Using `<section>` when there's no real thematic grouping — just use `<div>` in that case

**Small practice task**
Rebuild yesterday's registration form page (or any earlier practice page) using proper semantic structure:

- Wrap it in `<main>`
- Add a `<header>` with a `<nav>`
- Add a `<footer>`
- Add `aria-label` to any icon-only button
- Check the heading order makes sense
