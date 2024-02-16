---
layout: page
title: Tiled Horizontal decorator
parent: CSS/decorators
grandparent: CSS
next: tiled_vertical
---

The `tiled-horizontal` decorator can render three sprites or images, horizontally across an element. One image is placed on the left edge, another on the right edge, and the last is stretched across the middle.

The decorator renders across the padded area of its element.

```css
decorator: tiled-horizontal( 
	<left-image-src> <left-image-orientation>,  
	<center-image-src> <center-image-orientation>,
	<right-image-src> <right-image-orientation>
);
```

The `<x-orientation>` properties can be omitted, which leaves them at their default values.


### Properties


`*x*-image-src`

Value: | \<string\>
Initial: | *empty*
Percentages: | N/A

This property defines either a [sprite name](../sprite_sheets.html) or a relative path to an image file.

`*x*-image-orientation`

Value: | none \| flip-horizontal \| flip-vertical \| rotate-180
Initial: | none
Percentages: | N/A

Flips or rotates the image.

