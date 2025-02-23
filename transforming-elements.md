# Using Transform in CSS for Element Transformations

One of the methods to manipulate the appearance of elements using CSS is the transform property, which allows modifying the position, size, and rotation of an element. In this article, we will explore the use of rotation with `rotate`, `rotateX`, `rotateY`, `perspective` and `transform-origin`.

## Initial Structure of the HTML and CSS

**HTML:**

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Exemplo de Transformação</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <div class="box">Rotação CSS</div>
    </div>
</body>
</html>
```

**CSS:**

```css
body {
    font-family: Arial, sans-serif;
    background-color: #f0f0f0;
}

.box {
    width: 150px;
    height: 150px;
    background-color: #3498db;
    color: white;
    font-size: 18px;
    font-weight: bold;
    margin: 50px auto;
    text-align: center;
    line-height: 150px;
}
```

I added some properties to the `.box` class to improve visualization. The `.box` is a square centered on the screen, with a blue background and white text.

## Rotation with transform: rotate()

The `rotate()` property in CSS allows rotating an element around its own axis. We can specify the rotation in degrees (`deg`), radians (`rad`), turns (`turn`), among other units.

```css
.box {
    transform: rotate(45deg)
}
```

In this example, we are rotating the element by 45 degrees.

**Rotation Direction:**

- Positive values rotate clockwise.
- Negative values rotate counterclockwise.
- For example, `rotate(30deg)` slightly tilts it clockwise, while `rotate(-30deg)` tilts it in the opposite direction.

## RotateX() e RotateY()

The rotateX() and rotateY() methods allow rotating an element along the X and Y axes, respectively.

### `rotateX()`:

This method rotates the element along the X-axis, creating a tilt effect forward or backward.

```css
.box {
    transform: rotateX(45deg);
}
```

In this example, we are rotating the element 45 degrees along the X-axis.

- Positive values tilt the top of the element backward.
- Negative values move the top forward.
- Example: `rotateX(25deg)` slightly tilts it backward, while `rotateX(-40deg)` tilts it forward.

### `rotateY()`:

This method rotates the element along the Y-axis and, when used alone, only makes the element stretch vertically.

```css
.box {
    transform: rotateY(45deg);
}
```
In this example, we are rotating the element 45 degrees along the Y-axis.

- Positive values move the right side backward and the left side forward.
- Negative values do the opposite.
- Example: `rotateY(20deg)` slightly rotates it to the right, while `rotateY(-35deg)` rotates it to the left.

To create a visible 3D effect at 45 degrees, we need to add the `perspective` property to the parent element, adding depth perception and making the rotation more noticeable.

## Adjusting the Perspective

The `perspective` property defines the depth of the 3D scene. Smaller values make the rotation more apparent, while larger values reduce the depth effect.

```css
.container {
    perspective: 200px;
}
```

## Origin Point with `transform-origin`

The `transform-origin` property defines where the transformation starts. By default, it occurs from the center of the element, but we can change this to any other point, such as a corner or edge. This affects how the element rotates or moves.

```css
.box {
    transform: rotate(45deg);
    transform-origin: top left;
}
```

In this example, the element will rotate from the top-left corner instead of its center.

### `transform-origin` Values

The property accepts values in different formats such as keywords, percentages, and absolute values. Here are some examples:

- **Keywords:** `top left`, `bottom right`, `center`

- **Percentages:** `0% 0%` (top-left corner), `100% 100%` (bottom-right corner)

- **Absolute values**: `10px 20px` (distance close to the top-left corner)

**Comparison of different origins:**

```css
.box1 {
    transform: rotate(30deg);
    transform-origin: center;
}

.box2 {
    transform: rotate(30deg);
    transform-origin: bottom right;
}
```

In the example above, `.box1` rotates from the center, while `.box2` rotates from the bottom-right corner.