# Learning `<canvas>`

Just one of the things I'm learning. <https://github.com/hchiam/learning>

## SVG vs Canvas

<https://www.sitepoint.com/canvas-vs-svg-choosing-the-right-tool-for-the-job/>

**SVG** = visual scalability but more DOM memory.

- good for hi-fi interactive graphics.

**Canvas** = "paint-and-forget" less DOM memory but raster instead of ability to do vector scaling.

- good for painting detailed small pixels, like weather maps.

You can even combine SVG and canvas.

## Canvas vs WebGL

[WebGL](https://github.com/hchiam/learning-webgl) uses `<canvas>`. WebGL tutorial: <https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API/Tutorial>

## Tutorial

<https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial>

- `<canvas>` isn't supported on some older browsers (i.e. IE8 or earlier).
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

**Note:** `Path2D` object is like a "macro" that "records" paths that you can play back quickly. It is *NOT* currently available in IE.

### Transformations

- save & restore state: `context.save()` and `context.restore()`
- translate: `context.translate(x, y)`
- rotate: `context.rotate(angleInRadians)`
- scale: `context.scale(x, y)`
- matrix transform: `context.transform(a, b, c, d, e, f)` for matrix `[[a, c, e], [b, d, f], [0, 0, 1]]` and `context.resetTransform()`:
  - `a` = horizontal scaling
  - `b` = horizontal skewing
  - `c` = vertical skewing
  - `d` = vertical scaling
  - `e` = horizontal moving
  - `f` = vertical moving
  - `context.setTransform(a, b, c, d, e, f)` undoes the previous transform and sets a new one (instead of transforming an already-transformed version)

### Clipping paths

Everything after it will only show up inside the clipping path.

### Animation

<https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial/Basic_animations>

1. **clear** canvas `context.clearRect(x, y, w, h);`
2. (**save state** of canvas (if you want to reuse it each frame) [`context.save();`](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/save))
3. **draw**
4. (**restore state** of canvas (before the next frame, if you already want to save state) [`context.restore();`](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/restore))

<https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial/Advanced_animations>

### Pixel manipulation

<https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial/Pixel_manipulation_with_canvas>

Examples:

- Colour picker
- Colour filter
- Zooming and anti-aliasing
- Saving images

### Hit regions ***(currently experimental)***

<https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial/Hit_regions_and_accessibility>

### Perf tips

<https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial/Optimizing_canvas>
