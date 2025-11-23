+++
title = "Web Accessibility Essentials"
date = 2024-03-10
summary = "Make your websites usable for everyone with these accessibility fundamentals"
tags = ["accessibility", "a11y", "inclusive-design"]
categories = ["Design"]
+++

Accessibility isn't optional—it's essential. Here's how to make your websites usable for everyone.

## Semantic HTML

Use the right elements:

```html
<!-- Good -->
<nav>
  <ul>
    <li><a href="/">Home</a></li>
  </ul>
</nav>

<main>
  <article>
    <h1>Article Title</h1>
    <p>Content...</p>
  </article>
</main>

<!-- Bad -->
<div class="nav">
  <div><a href="/">Home</a></div>
</div>
```

## ARIA Labels

Enhance accessibility with ARIA:

```html
<!-- Button with no visible text -->
<button aria-label="Close dialog">×</button>

<!-- Navigation landmark -->
<nav aria-label="Main navigation">...</nav>

<!-- Loading state -->
<div aria-live="polite" aria-busy="true">
  Loading...
</div>
```

## Keyboard Navigation

Ensure keyboard accessibility:

- All interactive elements must be keyboard accessible
- Logical tab order
- Visible focus indicators
- Skip links for main content

```css
/* Visible focus indicator */
:focus {
  outline: 2px solid blue;
  outline-offset: 2px;
}

/* Never remove outline without replacement */
:focus {
  outline: none; /* Only if providing alternative */
  box-shadow: 0 0 0 3px rgba(66, 153, 225, 0.5);
}
```

## Color Contrast

Ensure sufficient contrast:

- Normal text: 4.5:1 minimum
- Large text: 3:1 minimum
- UI components: 3:1 minimum

```css
/* Good contrast */
.text {
  color: #333;
  background: #fff;
}

/* Check with tools like:
   - WebAIM Contrast Checker
   - Chrome DevTools
   - Lighthouse */
```

## Images

Always provide alt text:

```html
<!-- Informative image -->
<img src="graph.png" alt="Sales increased 50% in Q4">

<!-- Decorative image -->
<img src="decoration.png" alt="">

<!-- Complex image -->
<img src="chart.png" 
     alt="Bar chart showing sales data"
     aria-describedby="chart-description">
<div id="chart-description">
  Detailed description of the chart data...
</div>
```

## Forms

Make forms accessible:

```html
<form>
  <label for="email">Email address</label>
  <input 
    type="email" 
    id="email" 
    name="email"
    required
    aria-describedby="email-error">
  <span id="email-error" role="alert">
    Please enter a valid email
  </span>
</form>
```

## Testing

Test with:

- Screen readers (NVDA, JAWS, VoiceOver)
- Keyboard only navigation
- Browser zoom (200%)
- Color contrast tools
- Automated tools (axe, Lighthouse)

## Common Mistakes

1. Missing alt text
2. Poor color contrast
3. No keyboard access
4. Unclear form labels
5. Missing ARIA labels
6. Removed focus indicators
7. Automatic media playback
8. Time limits without controls

Accessibility benefits everyone. Start with these basics and make the web more inclusive.
