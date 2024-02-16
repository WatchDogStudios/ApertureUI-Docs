---
layout: page
title: HTML Images
parent: HTML
next: forms
---

### \<img\>

The `<img>` element is used to include images or [sprites](../CSS/sprite_sheets.html) in the document.

_Attributes_

`src` = uri (CT)
: The source location of an image.

`sprite` = sprite (CS)
: The name of a sprite located in a sprite sheet in the current document. If this attribute is set, the `src` and `rect` attributes will be ignored.

`width` = number (CN)
: The width to force the element to, in pixels. If this is unspecified, it will default to the width of the sprite, rectangle, or image in that order.

`height` = number (CN)
: The height to force the element to, in pixels. If this is unspecified, it will default to the height of the sprite, rectangle, or image in that order.

`rect` = four numbers (CN)
: Crops the image to a sub-rectangle within the image file. Specified as a space-separated list of four (unit-less) values `x y width height`, where pixel units are implied. Will have no effect on sprites.
