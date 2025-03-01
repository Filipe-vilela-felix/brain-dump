# How to Add Variables on CSS

CSS variables are very useful to organize and make the code easier to change. They help to store values that we can use many times, so we don’t need to repeat the same numbers or colors.

In this article, we will learn how to use CSS variables to make our code better. First, we will see a normal example, and then we will change it to use variables.

## Initial Structure

**HTML**

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Exemplo CSS</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <h1>Bem-vindo ao Meu Site</h1>
    </header>
    <main>
        <button>Saiba Mais</button>
    </main>
</body>
</html>
```

```css
* {
    box-sizing: border-box;
}

body {
    font-family: Arial, sans-serif;
    background-color: #f4f4f4;
    color: #333;
    text-align: center; 
    padding: 20px;
}

button {
    background-color: #007bff;
    color: white;
    padding: 10px 20px;
    border-radius: 5px;
}

button:hover {
    background-color: #0056b3;
}
```

In this code, we created a simple webpage with a title and a centered button.

By using CSS variables, we can store reusable values in our code, making styles easier to maintain and update.

Let's imagine that, instead of the structure shown above, our website contains many repeated colors. If we wanted to change these colors in the future, we would have to modify each value individually. With CSS variables, we can define colors in one place and reuse them throughout the code.

## Defining Variables in CSS

To define CSS variables, we use the :root selector, which represents the highest level of the document. This allows the variables to be used anywhere in the CSS.

**Example**

```css
:root {
    --primary-color: #007bff;
    --secondary-color: #0056b3;
    --text-color: #333;
}

body {
    color: var(--text-color);
}

button {
    background-color: var(--primary-color);
    color: white;
    padding: 10px 20px;
    border-radius: 5px;
}

button:hover {
    background-color: var(--secondary-color, #0056b3);
}
```

As you can see, after defining the variables inside `:root` using a specific syntax, we reference them within each property using the `var()` function.

In this syntax, it is necessary to add the prefix `--`, as in `--primary-color`. This is because the `--` prefix is the way to declare a CSS Custom Property. If we wrote just primary-color, CSS would not recognize it as a valid variable and would ignore the declaration.

We can also add a fallback value in case the variable is not defined, as seen in the `button:hover` style:
```css
button:hover {
    background-color: var(--secondary-color, #0056b3);
}
```
This way, for example, if we want to change the button color, we only need to update the values of `--primary-color` and `--secondary-color`, without modifying each individual element manually.

## CSS Variable Support in Web Browsers

When implementing newer features like **CSS variables**, I recommend checking their compatibility across different browsers. A very useful tool for this is ["Can I Use"](https://caniuse.com/).

According to ["Can I Use"](https://caniuse.com/?search=variables%20css), CSS variables are widely supported in modern browsers, including the latest versions of Chrome, Firefox, and Safari. However, Internet Explorer 11 and earlier versions do not support this functionality.

Therefore, if your project needs to be compatible with older browsers, you should use CSS variables with caution.