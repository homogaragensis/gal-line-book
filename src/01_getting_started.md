# Getting Started

Surely, a good software engineering professor would say that you should start developing a system by analyzing it.

The detail that is often omitted is that, in order to analyze a system, you need to understand the problem it solves. For this reason, I believe the development process should begin by immediately exploring the development environment and starting to stimulate your vision and imagination, trying to obtain a minimalist approximation of your idea.

Let's start by creating a folder on our computer. In my case, I'll call it `gal-line`.

Inside it, I'll create the usual three files:
- `index.html`
- `assets/style.css`
- `src/main.js`

I've decided to structure the folders this way simply out of habit; we won't focus on that.

Ready? Let's start programming!

## The Page Skeleton

In the `index.html` file, we insert the usual boilerplate:
```html
<!doctype html>
<html>
  <head>
  </head>
  <body>
  </body>
</html>
```

in the `<head>` section, we add the title:
```html
<title>gal-line</title>
```

we add the character set and viewport responsiveness tags:
```html
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
```

and we link the stylesheet:
```html
<link rel="stylesheet" href="assets/style.css">
```

at this point, we create the skeleton of our page and insert the following inside the `<body>` section:
```html
<main class="container">
  <section id="game" class="game-area">
    <canvas id="rendercanvas"></canvas>
  </section>
</main>
```

the `<main>` element identifies the main container, while the section with the `game` id contains the main canvas on which we will draw our entire game.

## The page looks

Now let's attach the `style.css` file. in this file, we will define the appearance of the UI elements of our game, as well as how the various elements behave when the browser is resized.

Let's start by declaring a variable that will represent 
the size of the white border around the canvas.
```css
:root {
  --game-margin: 24px;
}
```
then we specify that no element has either margin or 
padding and that they position their children completely inside (ignoring margin).
We also want the document to fill the entire screen.
```css
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

html,
body {
  width: 100%;
  min-height: 100%;
}
```
we set the font:
```css
body {
  font-family: sans-serif;
}
```
and we define the properties for the `container` class, which will be a 1x1 grid that completely fills the screen.
```css
.container {
  display: grid;
  width: 100%;
  min-height: 100vh;
  padding: var(--game-margin);
  place-items: center;
}
```
inside it, there is the section with the `game-area` class.

This class is designed to allow the canvas to fill it while making the section take the desired shape. In particular, we want it to be as large as possible while maintaining the aspect ratio chosen for the canvas.

Since we would like to be able to define the canvas rendering dimensions from JavaScript (that is, the same dimensions specified by the `width` and `height` attributes on the canvas element in HTML),

## Configuring the Canvas

To configure the canvas display size and internal size, we need to link a JavaScript script. To do so, we add
```html
<script type="module" src="src/main.js"></script>
```
to the bottom of our `<body>` block. This allows us to load `main.js` as a module, enabling the browser to automatically load the necessary files without having to add a large number of `<script>` tags.

Inside the Javscript module we insert an  IIFE, which will be run at page load.
```js
(() => {})();
```
Inside its scope we retrieve the canvas from the DOM and set its internal resolution:
```js
(() => {
    const canvas = document.getElementById("renderCanvas");
    canvas.width = 1230;
    canvas.height = 680;
})();
```
Now we need to add the `--viewport-aspect` variable to 
our css and we set it to be the aspect ratio
of our chosen resolution:

```js
...

document.documentElement.style.setProperty(
"--viewport-aspect", canvas.width / canvas.height
);
```

And in the css, we add the variable with a dummy value in the `:root` selector:
```css
:root {
    --game-margin: 24px;
    --viewport-aspect: 1; /* Set by main.js */
}
```
And finally compute the display size:
```css
.game-area {
  position: relative;
  /* Scale the game to fit the available viewport while
   * preserving the aspect ratio defined by the js. */
  width: min(100%, calc((100vh - 2 * var(--game-margin)) * var(--viewport-aspect)));
  aspect-ratio: var(--viewport-aspect);
}

#renderCanvas {
  display: block;
  width: 100%;
  height: 100%;
}
```
> Notice how we have also set the canvas to fill its parent!

We now have our canvas, and to end this section with a 
visible result other than a white page, you can retrieve
a 2D rendering context as follows:
```js
const ctx = canvas.getContext('2d');
```
And then use it to draw a black rectangle covering the whole canvas:
```js
ctx.fillStyle = "#000000";
ctx.fillRect(0, 0, canvas.width, canvas.height);
```

If you have done everything correctly you should see:
![Black rectangle](./images/image01.png)
Cool huh?? 
Well, probably not so much, but i promise that this is pretty much all the boilerplate needed to develop our game!
