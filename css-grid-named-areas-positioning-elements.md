# How to Add Named Template Areas in a CSS Grid

This article aims to show you how we can name template areas in a CSS Grid.

Instead of defining positions using numbers, we can use descriptive names for areas within a grid. This makes the code simpler and allows us to change the layout easily without adjusting each item manually.

It is worth mentioning that this technique is especially useful in more complex layouts, where positioning elements can become confusing without a clear structure.

However, for this article, I will use a simple example to demonstrate how it works.

## Initial Structure of the HTML and CSS

**HTML:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>CSS Grid</title>
    <link rel="stylesheet" href="main.css">
</head>
<body>
    <div class="container">
        <div class="el1">Element 1</div>
        <div class="el2">Element 2</div>
        <div class="el3">Element 3</div>
        <div class="el4">Element 4</div>
    </div>
</body>
</html>
```

**CSS:**

```css
.container {
    margin: 20px;
    display: grid;
    grid-template-columns: 200px 150px 20% 1fr;
    grid-template-rows: 5rem 20rem 3rem;
}

.el1 {
    background: rgba(255, 154, 72, 0.5);
    grid-column: 1 / 5;
}

.el2 {
    background: rgba(255, 0, 0, 0.5);
    grid-column: 2;
}

.el3 {
    background: rgba(200, 243, 9, 0.5);
    grid-column: 3 / 5;
}

.el4 {
    background: rgba(0, 4, 255, 0.5);
    grid-column: 1/5;
    grid-row: 3 / 4;
}
```

In the .container class, we define `display: grid` and use `grid-template-columns` and `grid-template-rows` to create four columns and three rows with different values.    

Each element inside .container has specific grid-column values:

- `.el1` spans the entire first row.
- `.el2` occupies the second column of the second row.
- `.el3` spans from the third to the last column of the second row.
- `.el4` occupies the entire third row.

If you want to understand how we added these properties, check out the article [How to Position Child Elements in a CSS Grid](position-child-grid.md).

## Adding the `grid-template-areas` Property

To assign names to each area of our grid, we need to add the grid-template-areas property to .container. This property defines a visual representation of the grid, where each quoted string represents a row and each name represents a cell.
Example:

```css
grid-template-areas: "header header header header"
                     ". main1 main2 main2"
                     "footer footer footer footer";
```

Each row is enclosed in quotes, and the values inside define the names of the corresponding grid areas. In this case:

- `header` spans the entire first row.
- `.` (dot) represents an empty space in the first column of the second row (dots can be used to indicate unused areas).
- `main1` occupies the second column of the second row.
- `main2` spans the third and fourth columns of the second row.
- `footer` spans the entire third row.

## Adding the Property `grid-area`

To position each element according to the names we assigned in `grid-template-areas`, we need to add the `grid-area` property to each element.

```css
.el1 {
    background: rgba(255, 154, 72, 0.5);
    grid-area: header;
}

.el2 {
    background: rgba(255, 0, 0, 0.5);
    grid-area: main1;
}

.el3 {
    background: rgba(200, 243, 9, 0.5);
    grid-area: main2;
}

.el4 {
    background: rgba(0, 4, 255, 0.5);
    grid-area: footer;
}
```

Now, each element is automatically positioned in the grid according to its assigned area name, making the layout more readable and easier to modify.

# How to Position Grid Elements

The properties `justify-items` and `align-items` allow you to control how elements are positioned horizontally and vertically within their assigned grid areas.

## Understanding `justify-items`

The `justify-items` property controls horizontal alignment within each grid cell. It accepts the following values:

- `start`: Aligns elements to the beginning of the column.
- `center:` Aligns elements in the middle of the column.
- `end:` Aligns elements to the end of the column.

```css
.container {
    margin: 20px;
    display: grid;
    grid-template-columns: 200px 150px 20% 1fr;
    grid-template-rows: 5rem 20rem 3rem;
    grid-template-areas: "header header header header"
                         ". main1 main2 main2"
                         "footer footer footer footer";
    justify-items: center;
}
```
In this example, all elements inside the grid cells will be horizontally centered. And `el3` will be positioned between the third and fourth columns

## Understanding `align-items`

The align-items property controls vertical alignment within each grid cell. It also accepts the same values:

- `start`: Aligns elements to the top of the row.
- `center`: Aligns elements in the middle of the row.
- `end`: Aligns elements to the bottom of the row.

```css
.container {
    margin: 20px;
    display: grid;
    grid-template-columns: 200px 150px 20% 1fr;
    grid-template-rows: 5rem 20rem 3rem;
    grid-template-areas: "header header header header"
                         ". main1 main2 main2"
                         "footer footer footer footer";
    align-items: center;
}
```
In this example, all elements inside the grid cells will be vertically centered.

## Using `justify-items` and `align-items` Together

If you use only justify-items, elements will take up the full height of their grid cell. Similarly, if you use only align-items, elements will take up the full width of their grid cell.

By combining both properties, you can precisely position elements within their grid areas