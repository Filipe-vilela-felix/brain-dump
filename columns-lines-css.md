# How to Define Columns and Rows in CSS Grid

CSS Grid allows you to organize elements into columns and rows. In this article, we'll explore the basics of defining columns and rows with CSS Grid.

See the initial structure of the HTML and CSS code:

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

Inside the ```div.container``` there are four elements displayed one below the other.

Now, to transform this container into a grid container, we need to add the ```display: grid``` property:

```css
.container {
    margin: 20px;
    display: grid;
}
```
With this, the browser understands that we want to organize the child elements in a grid.

## Defining columns

To define columns in a grid container, we add the ```grid-template-columns``` property.

Each value added to this property, in addition to representing a column, also represents its size. See the example:

```css
.container {
    margin: 20px;
    display: grid;
    grid-template-columns: 200px 150px 20%;
}
```
- The first column is 200px wide.
- The second column is 150px wide.
- The third column takes up 20% of the total width of the container.

By adding only three columns, **Element 4** will automatically go to the bottom row and become part of the first column, since we only added three columns.

Another unit that we can use in CSS Grid is the fraction (```fr```). The element that uses this unit will have the size of the remaining space of the container. See the example:

```css
.container {
    margin: 20px;
    display: grid;
    grid-template-columns: 200px 150px 20% 1fr;
}
```

Now **Element 4** remains on the same line occupying the fourth column.

## Defining lines

The same rules that we used to define the columns, we can use in the ```grid-template-rows``` property to define the rows. See the example:

```css
.container {
    margin: 20px;
    display: grid;
    grid-template-columns: 200px 150px 20% 1fr;
    grid-template-rows: 5rem 2.5rem;
}
```

- The first line is 5rem high.
- The second line is 2.5rem high.

PS: In both ```grid-template-columns``` and ```grid-template-rows``` properties, we can use the same units of measurement (px, rem, %, fr).