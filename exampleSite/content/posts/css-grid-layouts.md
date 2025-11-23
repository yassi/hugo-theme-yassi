+++
title = "Modern Layouts with CSS Grid"
date = 2024-02-20
summary = "Build complex responsive layouts with CSS Grid in minutes"
tags = ["css", "grid", "layout", "design"]
categories = ["Design"]
+++

CSS Grid has transformed how we build layouts. Let's explore its power with practical examples.

## Basic Grid

Create a simple grid:

```css
.container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}
```

## Responsive Grid

Adapt to screen size without media queries:

```css
.container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 20px;
}
```

This creates a grid that automatically adjusts the number of columns based on available space.

## Named Grid Areas

Define layout regions with names:

```css
.container {
  display: grid;
  grid-template-areas:
    "header header header"
    "sidebar content content"
    "footer footer footer";
  gap: 20px;
}

.header { grid-area: header; }
.sidebar { grid-area: sidebar; }
.content { grid-area: content; }
.footer { grid-area: footer; }
```

## Overlapping Elements

Layer elements on the grid:

```css
.container {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
}

.item1 {
  grid-column: 1 / 3;
  grid-row: 1 / 2;
}

.item2 {
  grid-column: 2 / 4;
  grid-row: 1 / 2;
}
```

## Common Patterns

### Holy Grail Layout

```css
body {
  display: grid;
  grid-template-rows: auto 1fr auto;
  min-height: 100vh;
}
```

### Card Grid

```css
.cards {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  gap: 24px;
}
```

### Masonry Layout

```css
.gallery {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  grid-auto-rows: 200px;
  gap: 16px;
}

.gallery img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
```

CSS Grid makes complex layouts simple and maintainable. Experiment with these patterns and create your own!
