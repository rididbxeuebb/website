+++
title = 'Why This Site Stays Small'
date = 2026-03-01T09:00:00Z
description = 'Why a boring stack still beats shipping a framework for every paragraph.'
summary = 'A first post about choosing plain documents, predictable CSS, and less front-end ceremony.'
+++

The web works best when a page behaves like a page. It loads quickly, it reads clearly, and it does not need a bundle graph just to show a headline.

That does not mean going backwards. Modern CSS is good now. Logical properties, better color handling, `:focus-visible`, `light-dark()`, and small view transitions let a site feel polished without pretending every essay is an app.

What I want from a blog is simple:

- readable text
- strong contrast
- sensible spacing
- links that look like links
- markup that still works when JavaScript never arrives

If a static page can do the job, I would rather ship that than introduce React, Next.js, hydration debt, and a week of configuration.

```html
<article>
  <h1>Write the words</h1>
  <p>Then get out of the way.</p>
</article>
```

That is still a good deal.
