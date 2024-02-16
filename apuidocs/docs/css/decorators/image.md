---
layout: page
title: Image decorator
parent: CSS/decorators
grandparent: CSS
next: tiled_horizontal
---

The `image` decorator can render a single sprite or image.

```css
decorator: image( <image-src> <image-orientation> <image-fit> <image-align-x> <image-align-y> );
```
Values must be specified in the given order, any unspecified properties will be left at their default values. See the 'demo' sample for usage examples.

The decorator renders across the padded area of its element.

### Properties

`image-src`

Value: | \<string\>
Initial: | *empty*
Percentages: | N/A

This property defines either a [sprite name](../sprite_sheets.html) or a relative path to an image file.

`image-orientation`

Value: | none \| flip-horizontal \| flip-vertical \| rotate-180
Initial: | none
Percentages: | N/A

Flips or rotates the image.

`image-fit`

Value: | fill \| contain \| cover \| scale-none \| scale-down \| repeat \| repeat-x \| repeat-y
Initial: | fill
Percentages: | N/A

`fill`
: The image is stretched to boundaries.

`contain`
: The image is stretched to boundaries, keeping aspect ratio fixed, 'letter-boxed'.

`cover`
: The image is stretched to cover the boundaries, keeping aspect ratio fixed.

`scale-none`
: The image is never scaled.

`scale-down`
: The image acts like 'scale-none' if smaller than boundaries, or like 'contain' otherwise.

`repeat`
: The image is tiled, repeating both horizontally and vertically. It does not work on sprite images.

`repeat-x`
: The image is horizontally tiled along the X-axis. It does not work on sprite images.

`repeat-y`
: The image is vertically tiled along the Y-axis. It does not work on sprite images.


`image-align-x`

Value: | left \| center \| right \| \<length-percentage\>
Initial: | center
Percentages: | relative to the element's padding width

Horizontally align or offset the image.

`image-align-y`

Value: | top \| center \| bottom \| \<length-percentage\>
Initial: | center
Percentages: | relative to the element's padding height

Vertically align or offset the image.
