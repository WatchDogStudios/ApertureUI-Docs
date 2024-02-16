---
layout: page
title: Blur Effect
parent: css/font_effects
grandparent: css
---

The blur font effect renders a Gaussian blurred copy of the text.

![Blur sample](blur.png)

Note that, the blur effect will not replace the original text. To only show the blurred version of the text, set the `color` property of the original text to `transparent`.

The effect is declared as:

```css
font-effect: blur( <width> <color> );
```

Its properties are specified by the following.

`width`

Value: | \<length\>
Initial: | 1px
Percentages: | N/A

Determines the radius of the blur effect.

`color`

Value: | \<color\>
Initial: | white
Percentages: | N/A

The color is applied multiplicatively over the entire effect.



```css
/* Renders a blurred version of the text, hides the original text. */
h1
{
	color: transparent;
	font-effect: blur(3px #ed5);
}
```
