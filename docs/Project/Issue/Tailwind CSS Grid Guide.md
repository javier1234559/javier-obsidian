---
Created: 19:14 13-09-2024
tags:
  - issue
---
TLDR
1. Grid Template Columns:
    - `grid-cols-{n}`: Define n equal-width columns
    - `grid-cols-[...]`: Custom column sizes
2. Grid Column Span:
    - `col-span-{n}`: Span n columns
    - `col-start-{n}`: Start at column n
    - `col-end-{n}`: End at column n
3. Grid Template Rows:
    - `grid-rows-{n}`: Define n equal-height rows
    - `grid-rows-[...]`: Custom row sizes
4. Grid Row Span:
    - `row-span-{n}`: Span n rows
    - `row-start-{n}`: Start at row n
    - `row-end-{n}`: End at row n
5. Grid Flow:
    - `grid-flow-row`: Arrange items by row
    - `grid-flow-col`: Arrange items by column
    - `grid-flow-dense`: Fill in holes earlier in the grid
6. Grid Auto Flow:
    - `auto-cols-auto`: Auto-sized columns
    - `auto-cols-min`: Minimum content-sized columns
    - `auto-cols-max`: Maximum content-sized columns
    - `auto-cols-fr`: Equally-sized columns
    - (Similar classes exist for rows: `auto-rows-...`)
7. Gap:
    - `gap-{size}`: Set gap between rows and columns
    - `gap-x-{size}`: Set gap between columns
    - `gap-y-{size}`: Set gap between rows
8. Justify Content:
    - `justify-{alignment}`: Align grid content along the inline (row) axis
9. Justify Items:
    - `justify-items-{alignment}`: Align grid items along the inline (row) axis
10. Align Content:
    - `content-{alignment}`: Align grid content along the block (column) axis
11. Align Items:
    - `items-{alignment}`: Align grid items along the block (column) axis
12. Place Content:
    - `place-content-{alignment}`: Shorthand for align-content and justify-content
13. Place Items:
    - `place-items-{alignment}`: Shorthand for align-items and justify-items

# Tailwind CSS Grid Guide

## 1. Creating a Grid Container

To create a grid container, use the `grid` class:

```html
<div class="grid">
  <!-- Grid items go here -->
</div>
```

## 2. Defining Grid Columns

Use `grid-cols-{n}` to define the number of columns:

```html
<div class="grid grid-cols-3">
  <!-- Creates a grid with 3 equal-width columns -->
</div>
```

For custom column sizes, use `grid-cols-[...]`:

```html
<div class="grid grid-cols-[200px_1fr_2fr]">
  <!-- Creates a grid with columns of 200px, 1fr, and 2fr -->
</div>
```

## 3. Defining Grid Rows

Use `grid-rows-{n}` to define the number of rows:

```html
<div class="grid grid-rows-3">
  <!-- Creates a grid with 3 equal-height rows -->
</div>
```

For custom row sizes:

```html
<div class="grid grid-rows-[100px_auto_200px]">
  <!-- Creates a grid with rows of 100px, auto, and 200px -->
</div>
```

## 4. Grid Item Placement

### Column Span

Use `col-span-{n}` to make an item span multiple columns:

```html
<div class="grid grid-cols-3">
  <div class="col-span-2">Spans 2 columns</div>
  <div>Normal column</div>
</div>
```

### Row Span

Use `row-span-{n}` to make an item span multiple rows:

```html
<div class="grid grid-rows-3">
  <div class="row-span-2">Spans 2 rows</div>
  <div>Normal row</div>
</div>
```

## 5. Grid Gap

Set gap between grid items:

```html
<div class="grid grid-cols-3 gap-4">
  <!-- Creates a grid with 3 columns and 1rem (16px) gap -->
</div>
```

For different column and row gaps:

```html
<div class="grid grid-cols-3 gap-x-4 gap-y-8">
  <!-- 1rem (16px) horizontal gap, 2rem (32px) vertical gap -->
</div>
```

## 6. Responsive Grids

Tailwind's responsive prefixes work with grid classes:

```html
<div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3">
  <!-- 1 column on small screens, 2 on medium, 3 on large -->
</div>
```

## 7. Grid Flow

Control how auto-placed items flow:

```html
<div class="grid grid-flow-row"> <!-- Default: items flow row by row -->
<div class="grid grid-flow-col"> <!-- Items flow column by column -->
<div class="grid grid-flow-dense"> <!-- Attempts to fill in holes in the grid -->
```

## 8. Alignment

### Align Grid Content

```html
<div class="grid grid-cols-3 content-center h-screen">
  <!-- Centers grid content vertically in a full-height container -->
</div>
```

### Align Grid Items

```html
<div class="grid grid-cols-3 items-center h-screen">
  <!-- Centers grid items vertically -->
</div>
```

### Justify Grid Content

```html
<div class="grid grid-cols-3 justify-items-center">
  <!-- Centers grid items horizontally -->
</div>
```

## 9. Auto Columns/Rows

For implicit grid tracks:

```html
<div class="grid grid-cols-3 auto-cols-max">
  <!-- Any implicitly created columns will be sized to their maximum content -->
</div>
```

This guide covers the basics of using CSS Grid with Tailwind CSS. Remember to consult the Tailwind CSS documentation for more detailed information and advanced usage.