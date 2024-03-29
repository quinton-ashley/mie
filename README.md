# mie : mini editor

mie is great for embedding p5.js sketches on your own website.

Demo: https://p5play.org/learn/sprite.html

## Usage

Load the Ace editor and mie in your HTML:

```html
<script src="https://cdn.jsdelivr.net/npm/ace-builds@1.18.0/src-min-noconflict/ace.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/ace-builds@1.18.0/src-min-noconflict/ext-language_tools.js"></script>

<script src="https://quinton-ashley.github.io/mie/mie.js"></script>
```

Or use [mie](https://www.npmjs.com/package/@qashto/mie) via npm:

```bash
npm i @qashto/mie
```

Add p5.js scripts to your page and they will be embedded in an editor with an instanced preview of the sketch auto-playing by default.

```html
<script type="mie/p5" name="Sketch">
	function setup() {
		createCanvas(100, 100);
	}
	function draw() {
		background('blue');
	}
</script>
```

## Options

You can add properties to the script tag to adjust the mie player to your liking. Here's an example that limits the height of the editor to 10 lines.

```html
<script type="mie/p5" name="Sketch" lines="10">
```

Other property options include:  
`horiz`/`vert` - horizontal or vertical layout (vert is the default)
`lines="#"` - sets the height of the editor to the specified number of lines  
`base-#` - specifies the sketch as a base sketch  
`base="#"` - will load the code in its editor into the draw function of the specified base sketch  
`editor-btn` - add the show/hide editor button  
`hide-editor` - hides the editor, just shows the preview
`hide` - hides the whole mini player, useful for invisible base sketches

## Advanced Usage

If you don't want all the sketches on a page to be automatically loaded when the mie.js script executes you can disable auto-loading. Simply run this before the mie.js script executes:

```js
window.mie = {
	autoLoad: false
};
```

Then load mie after the ace editor has loaded:

```js
mie.load();
```

Then you can load only the mie scripts contained inside an specific HTML element by using the `mie.loadMinis` function. This is good if you have multiple pages of content in one HTML file and you want to load the sketches on each page separately.

```js
mie.loadMinis(elem);
```

You can also define the `mie.ready` function, which is run when mie is ready to load sketches.
