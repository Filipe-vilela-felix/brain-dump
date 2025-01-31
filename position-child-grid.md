# How to Position Child Elements in a CSS Grid

This article aims to show you how to position child elements inside a grid container.

If you want to learn how to organize elements into columns and rows using CSS Grid, check out the file...

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
    grid-template-rows: 5rem 2.5rem;
}

.el1 {
    background: rgba(255, 154, 72, 0.5);
}

.el2 {
    background: rgba(255, 0, 0, 0.5);
}

.el3 {
    background: rgba(0, 128, 0, 0.5);
}

.el4 {
    background: rgba(0, 4, 255, 0.5);
}
```

Inside the ```div.container``` on our html, displayed one below the other. And inside the ```.container``` on our css we have the ```display: grid``` property with ```grid-template-columns``` and ```grid-template-rows``` adding four columns and two rows with diferent values.

Now that our parent container is a grid, we can change the position of our child elements.

## Understanding Grid Cell Positioning

Before modifying the positioning, you need to understand that when we add the grid property, each cell in the grid has its own "location."

For example, in our case, since we created four columns and two rows, we have eight cells in total. So far, Element 3 is located in column 3, row 1, and ends at column 4, row 1.

_PS: To better visualize the grid, I recommend using the "Layout" tab in the Developer Tools of your browser. There, you can see the numbers of each row and column. If you use Firefox, you can also enable an overlay grid for better visualization._

## Changing the Position Using Columns

Now, let's change an element's position using the ```grid-column-start``` and ```grid-column-end``` properties. See the example:

```css
.el1 {
    background: rgba(255, 154, 72, 0.5);
    grid-column-start: 1;
    grid-column-end: 5;
}
```

By adding these values, Element 1 starts at column 1 and extends to column 5.

Since Element 1 originally belonged to the first row, it now occupies all the columns in that row. As a result, the other elements are pushed down to the second row.

## Changing the Position Using Rows

Now, let's change an element's position using the ```grid-row-start``` and ```grid-row-end```. See the example:

```css
.el1 {
    background: rgba(255, 154, 72, 0.5);
    grid-column-start: 1;
    grid-column-end: 5;
    grid-row-start: 1;
    grid-row-end: 3
}
```

By adding these values, Element 1 starts at row 1 and extends to row 3, filling the entire grid vertically.

**Note:** Since we have two rows, we need to understand that:

1. The **first row** is at the top.

2. The **second row** is in the middle.

3. The **third row** is the of the grid.

That’s why I added "3" to grid-row-end.

Since Element 1 now occupies the entire grid, an extra row is automatically created below it to accommodate the remaining elements.

## Using Column & Row Shorthands

Instead of writing separate properties, we can use shorthand notation. See the example:

```css
.el1 {
    background: rgba(255, 154, 72, 0.5);
    /* grid-column-start: 1;
    grid-column-end: 5; */
    grid-column: 1 / 5;
    /* grid-row-start: 1;
    grid-row-end: 3 */
    grid-row: 1 / 3;
}
```

Instead of specifying `grid-column-start` and `grid-column-end` separately, we simply use `grid-column: 1 / 5;`. The same applies to `grid-row`.

The **first value** represents the **start**, and the **second value** represents the **end**. Both values are separated by a forward slash (/).