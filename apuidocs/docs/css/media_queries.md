---
layout: page
title: Media queries
parent: CSS
next: sprite_sheets
---

The CSS at-rule `@media` can be used to dynamically activate and deactive style rules based on a given set of conditions. The CSS media queries follow the [CSS syntax](https://developer.mozilla.org/en-US/docs/Web/CSS/@media) with some extensions and [limitations](#limitations).

```css
@media (orientation: landscape) and (min-width: 640px)
{
	#menu {
		float: left;
		width: 320px;
	}
}

@media (min-resolution: 2x)
{	
	@spritesheet theme2x
	{
		src: invader2x.tga;
		resolution: 2x;
		
		icon-invader: 179px 152px 102px 78px;
		icon-game:    330px 152px 102px 78px;
		icon-score:   534px 152px 102px 78px;
		icon-help:    728px 152px 102px 78px;
	}
}

@media (theme: blue)
{
	body {
		color: blue;
	}
	#header {
		background-color: #33e;
	}
}
```

### Media features

The following table lists all supported media features.

Name | Range | Value | Description
---- | ----- | ----- | -----------
`width`         | Yes | \<length\>            | Width of context.
`height`        | Yes | \<length\>            | Height of context.
`aspect-ratio`  | Yes | \<ratio\>             | Aspect ratio of context (width / height).
`resolution`    | Yes | \<resolution\>        | The [dp-ratio](syntax.html#dp-unit) of the context. Note that [\<resolution\>](syntax.html#resolution) always takes the `x` unit in CSS.
`orientation`   | No  | landscape \| portrait | Orientation based on the context width and height.
`theme`         | No  | \<string\>            | Custom CSS feature. Can be [activated and deactivated](../cpp_manual/contexts.html#themes) on the context.

Since APUI is designed to be displayed on screens and in a controlled environment, it doesn't make sense to implement all [CSS media features](https://developer.mozilla.org/en-US/docs/Web/CSS/@media#media_features). 

All range media features can be prefixed with `min-` and `max-` to specificy minimum and maximum constraints, respectively. All other constraints are compared for equality.

### Limitations

Currently, CSS has some limitations compared to CSS.

- `@media` rules cannot be nested.
- Conditions cannot be nested within a media query, eg. using parenthesis.
- Only the `and` logical operator is supported.
- Only a single occurrence of a given feature can be specified in a single media query.
    - Except that both `min-` and `max-` of the same range feature can be specified.
- The CSS Level 4 syntax using `<=` operators and similar is not supported.
