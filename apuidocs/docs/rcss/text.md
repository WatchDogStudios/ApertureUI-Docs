---
layout: page
title: Text
parent: rcss
next: tables
---

### Alignment: the 'text-align' property
{:#text-align}

`text-align`

Value: | left \| right \| center
Initial: | left
Applies to: | block-level elements
Inherited: | yes
Percentages: | N/A

This property affects how inline boxes within a line box are aligned. Values have the following meanings:

`left`
: The row of inline boxes are aligned against the left edge of the line box. 

`right`
: The row of inline boxes are aligned against the right edge of the line box. 

`center`
: The row of inline boxes are aligned in the centre of the line box. 

Note that the 'justify' value is not yet supported in RCSS.

### Decoration

#### Text decoration: the 'text-decoration' property
{:#text-decoration}

`text-decoration`

Value: | none \| underline \| overline \| line-through
Initial: | none
Applies to: | all elements
Inherited: | yes
Percentages: | N/A

Values have the following meaning:

`none`
: Any text generated by this element has no additional decoration. 

`underline`
: Any text generated by this element has an underline, with a thickness and position specified by the font.

`overline`
: Any text generated by this element has an overline, with a thickness and position determined from the font metrics.

`line-through`
: Any text generated by this element has a line-through, with a thickness and position determined from the font metrics.

The colour of any decoration is the same as the font colour.

#### Text shadows: the 'shadow' font effect

Instead of using the CSS-standard `text-shadow` property, text-shadowing is implemented in RmlUi using the more generic [font effect system](font_effects.html). Below is an example of how to specify a shadow for an element of text.

```css
/* Specify a grey text shadow on primary headings. */
h1
{
	font-effect: shadow( 2px 2px grey );
}
```

### White space: the 'white-space' property
{:#white-space}

`white-space`

Value: | normal \| pre \| nowrap \| pre-wrap \| pre-line
Initial: | normal
Applies to: | all elements
Inherited: | yes
Percentages: | N/A

This property defines how whitespace (any spaces, end-lines, carriage-returns and tabs) are processed in sections of text. Values have the following meanings:

`normal`
: Sequences of whitespace are collapsed down to single spaces. Lines are broken as necessary to fit line boxes. Line breaks in the source are ignored. 

`pre`
: Sequences of whitespace are preserved. Lines are only broken where line breaks are present in the source. 

`nowrap`
: Sequences of whitespace are collapsed. Lines are not broken. 

`pre-wrap`
: Sequences of whitespace are not collapsed. Lines are broken to fit line boxes or where line breaks are present in the source. 

`pre-line`
: Sequences of whitespace are collapsed. Lines are broken to fit line boxes or where line breaks are present in the source. 

### Breaking rules for text: the 'word-break' property
{:#word-break}

`word-break`

Value: | normal \| break-all \| break-word
Initial: | normal
Applies to: | all elements
Inherited: | yes
Percentages: | N/A

This property defines how text is broken into new lines where they otherwise would overflow. Values have the following meanings:

`normal`
: Text is only broken at word boundaries (whitespace).

`break-all`
: Word breaks can be inserted at any point to avoid overflow.

`break-word`
: Text is normally broken at word boundaries, but a word break can be inserted anywhere when a single word in the line would otherwise result in overflow.

These properties will only take effect if the `white-space` property allows wrapping.


### Spacing between characters; the 'letter-spacing' property
{:#letter-spacing}

`letter-spacing`

Value: | normal \| \<length\>
Initial: | normal
Applies to: | all elements
Inherited: | yes
Percentages: | N/A

Allows adjustment of the horizontal spacing between text characters.

`normal`
: Use normal letter spacing according to the current font.

`<length>`
: Use *additional* spacing between characters, can be negative to make spacing narrower.


### Text transform: the 'text-transform' property
{:#text-transform}

`text-transform`

Value: | none \| capitalize \| uppercase \| lowercase
Initial: | none
Applies to: | all elements
Inherited: | yes
Percentages: | N/A

Transforms text generated by this element. Values have the following meanings:

`none`
: Has no effect.

`capitalize`
: Any text generated by this element is capitalized.

`uppercase`
: Any text generated by this element is converted to upper case.

`lowercase`
: Any text generated by this element is converted to lower case.