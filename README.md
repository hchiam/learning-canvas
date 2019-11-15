# Learning `<canvas>`

Just one of the things I'm learning. <https://github.com/hchiam/learning>

## SVG vs Canvas

<https://www.sitepoint.com/canvas-vs-svg-choosing-the-right-tool-for-the-job/>

**SVG** = visual scalability but more DOM memory.

- good for hi-fi interactive graphics.

**Canvas** = "paint-and-forget" less DOM memory but raster instead of ability to do vector scaling.

- good for painting detailed small pixels, like weather maps.

You can even combine SVG and canvas.

## Tutorial

<https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial>

- `<canvas>` isn't supported on some older browsers.
- `<canvas>` default size is 300 x 150 pixels.
- unlike SVG, `<canvas>` basic building blocks are *only* rectangles and paths.

### Rectangles

```js
var canvas = document.getElementById('tutorial');
var context = canvas.getContext('2d');
context.strokeStyle = 'rgba(...)';
context.fillRect(x, y, w, h);
context.clearRect(x, y, w, h);
context.strokeRect(x, y, w, h);
```

### Paths

```js
var canvas = document.getElementById('tutorial');
var context = canvas.getContext('2d');
context.stroke() // to draw line shape
context.fill(...) // to draw filled shape
context.beginPath(...) // !
context.closePath()
context.moveTo(...)
context.lineTo(...)
context.bezierCurveTo(...)
context.quadraticCurveTo(...)
context.arc(...)
context.arcTo(...)
context.ellipse(...)
context.rect(...)
...
```

and more: <https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D#Paths>

**Note:** `Path2D` object is like a "macro" that "records" paths that you can play back quickly. It is *NOT* currently available in IE.
