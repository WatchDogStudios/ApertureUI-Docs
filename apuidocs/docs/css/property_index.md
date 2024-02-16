---
layout: page
title: Property index
parent: CSS
comment: Please run '_tools/generate_elements_and_properties_index.py' whenever properties or their URLs are added or changed.
---

The following table lists all properties recognised by CSS. The **Notes** column details important changes from the CSS specification.

Name | Values | Initial value | Applies to | Inherited | Percentages | Notes
---- | ------ | ------------- | ---------- | ---------- | ----------- | -----
[`align-content`][align-content] |flex-start \| flex-end \| center \| space-between \| space-around \| space-evenly \| stretch | stretch | multi-line flex containers | no | | 
[`align-items`][align-items] | flex-start \| flex-end \| center \| baseline \| space-around \| stretch | stretch | flex containers | no | | 
[`align-self`][align-self] | auto \| flex-start \| flex-end \| center \| baseline \| space-around \| stretch | auto | flex containers | no | | 
[`animation`][animation] | See [animations](animations_transitions_transforms.html#animation) | none | all | no | | 
[`background`][background] | `background-color` | | | | | Excludes images, use decorators instead.
[`background-color`][background-color] | \<colour\> | transparent | all | no | | 
[`border`][border] | `border-width` `border-color` | | | | | Excludes border style.
[`border-color`][border-color] | `border-top-color` `border-right-color` `border-bottom-color` `border-left-color` | | | | | 
[`border-top`][border] [`border-right`][border] [`border-bottom`][border] [`border-left`][border] | `border-<edge>-width` `border-<edge>-color` | | | | | Excludes border style.
[`border-top-color`][border-color] [`border-right-color`][border-color] [`border-bottom-color`][border-color] [`border-left-color`][border-color] | \<color\> | black | all | no | | 
[`border-top-width`][border-width] [`border-right-width`][border-width] [`border-bottom-width`][border-width] [`border-left-width`][border-width] | \<length\> \| \<percentage\> | 0px | all | no | width of containing block | 
[`border-width`][border-width] | `border-top-width` `border-right-width` `border-bottom-width` `border-left-width` | | all | | | 
[`border-top-left-radius`][border-radius] [`border-top-right-radius`][border-radius] [`border-bottom-right-radius`][border-radius] [`border-bottom-left-radius`][border-radius] | \<length\> | 0px | all | no | | Percentages and two-axis radii not supported. |
[`border-radius`][border-radius] | `border-top-left-radius` `border-top-right-radius` `border-bottom-right-radius` `border-bottom-left-radius` | | all | | | 
[`bottom`][top_right_bottom_left] | auto \| \<length\> \| \<percentage\> | auto | positioned elements | no | height of containing block | 
[`box-sizing`][box-sizing] | content-box \| border-box | content-box | block and replaced inline elements | no | | 
[`caret-color`][caret-color] | auto \| \<colour\> | auto | all elements | yes | | 
[`clear`][clear] | left \| right \| both \| none | none | block-level elements | no | | 
[`clip`][clip] | auto \| none \| always \| \<number\> | auto | all | no | | Controls interaction with ancestor element's clipping regions.
[`color`][color] | \<colour\> | black | all | yes | | 
[`column-gap`][gap] | \<length\> \| \<percentage\> | 0px | table elements | no | initial width of table | 
[`cursor`][cursor] | \<string\> | _empty_ | all | yes | | \<string\> refers an application specific cursor name.
[`decorator`][decorator] | none \| \<name\> \| \<type\>( \<properties\> ) | none | all | no | | See [decorators](decorators.html) for details.
[`display`][display] | inline \| block \| inline-block \| flow-root \| flex \| inline-flex \| table \| inline-table \| table-row-group \| table-row \| table-column-group \| table-column \| table-cell \| none | inline | all | no | | 
[`drag`][drag] | none \| drag \| drag-drop \| block \| clone | none | all | no | | Introduced for CSS. Controls generation of drag messages.
[`fill-image`][fill-image] | \<string\> | _empty_ | [progress](pages/cpp_manual/element_packages/progress_bar.html) element | no | | \<string\> refers to a sprite name or an image url.
[`flex`][flex] | auto \| none \| \<flex-grow\> \<flex-shrink\>? \<flex-basis\>? \| \<flex-basis\> | 0 1 auto | flex items | no | | 
[`flex-basis`][flex-basis] | \<length\> \| \<percentage\> \| auto | auto | flex items | no | | 
[`flex-direction`][flex-direction] | row \| row-reverse \| column \| column-reverse | row | flex containers | no | | 
[`flex-flow`][flex-flow] |  \<flex-direction\> \<flex-wrap\> | | | | | 
[`flex-grow`][flex-grow] | \<number\> | 0 | flex items | no | | 
[`flex-shrink`][flex-shrink] | \<number\> | 1 | flex items | no | | 
[`flex-wrap`][flex-wrap] | nowrap \| wrap \| wrap-reverse | nowrap | flex containers | no | | 
[`float`][float] | left \| right \| none | none | all | no | | 
[`focus`][focus] | none \| auto | auto | all | yes | | Introduced for CSS.
[`font`][font] | `font-style` `font-weight` `font-size` `font-family` | | | | | 
[`font-effect`][font-effect] | none \| \<type\>( \<properties\> ) | none | all | yes | | See [font effects](font_effects.html) for details.
[`font-family`][font-family] | \<string\> | | all | yes | | Only single family supported.
[`font-size`][font-size] | \<length\> \| \<percentage\> | 12px | all | yes | size of parent font | 
[`font-style`][font-style] | normal \| italic | normal | all | yes | | 'oblique' not supported.
[`font-weight`][font-weight] | normal \| bold \| \<number \[1,1000\]\> | normal | all | yes | | Relative weights not supported.
[`gap`][gap] | `row-gap` `column-gap` | | table elements | | | Replaces the CSS `border-spacing` property.
[`height`][height] | \<length\> \| \<percentage\> \| auto | auto | block and replaced inline elements | no | height of containing block | 
[`image-color`][image-color] | \<color\> | white | \<img\> elements and decorators | no | | Introduced for CSS.
[`justify-content`][justify-content] | flex-start \| flex-end \| center \| space-between \| space-around \| space-evenly | flex-start | flex containers | no | | 
[`left`][top_right_bottom_left] | auto \| \<length\> \| \<percentage\> | auto | positioned elements | no | width of containing block | 
[`letter-spacing`][letter-spacing] | normal \| \<length\> | normal | all elements | yes | | 
[`line-height`][line-height] | \<number\> \| \<length\> \| \<percentage\> | 1.2 | all | yes | font size | 'normal' not supported.
[`margin`][margin] | `margin-top` `margin-right` `margin-bottom` `margin-left` | | | | | 
[`margin-top`][margin] [`margin-right`][margin] [`margin-bottom`][margin] [`margin-left`][margin] | \<length\> \| \<percentage\> \| auto | 0px | all | no | width of containing block | 
[`max-height`][max-height] | \<length\> \| \<percentage\> \| none | none | block and replaced inline elements | no | height of containing block | 
[`min-height`][min-height] | \<length\> \| \<percentage\> | 0px | block and replaced inline elements | no | height of containing block | 
[`max-width`][max-width] | \<length\> \| \<percentage\> \| none | none | block and replaced inline elements | no | width of containing block | 
[`min-width`][min-width] | \<length\> \| \<percentage\> | 0px | block and replaced inline elements | no | width of containing block | 
[`nav`][nav] | none \| auto \| horizontal \| vertical | none | tabbable elements | no | | Shorthand for navigation properties.
[`nav-up`][nav] [`nav-right`][nav] [`nav-down`][nav] [`nav-left`][nav] | none \| auto \| \<id\> | none | tabbable elements | no | | Controls spatial navigation.
[`opacity`][opacity] | \<number\> | 1 | all | yes | | 
[`overflow`][overflow] | `overflow-x` `overflow-y` | | | | | 
[`overflow-x`][overflow] | visible \| hidden \| scroll \| auto | visible | block elements | no | | Content clipped if either axis is not 'visible'.
[`overflow-y`][overflow] | visible \| hidden \| scroll \| auto | visible | block elements | no | | Content clipped if either axis is not 'visible'.
[`overscroll-behavior`][overscroll-behavior] | auto \| contain | auto | scroll containers | no | | 
[`padding`][padding] | `padding-top` `padding-right` `padding-bottom` `padding-left` | | | | | 
[`padding-top`][padding] [`padding-right`][padding] [`padding-bottom`][padding] [`padding-left`][padding] | \<length\> \| \<percentage\> | 0px | all | no | width of containing block | 
[`perspective`][perspective] | none \| \<length ≥ 0px\> | none | all | no | |
[`perspective-origin`][perspective-origin] | \<perspective-origin-x\> \|\| \<perspective-origin-y\> | 50% 50% | all | no | |
[`pointer-events`][pointer-events] | auto \| none | auto | all | yes | | 
[`position`][position] | static \| relative \| absolute \| fixed | static | all | no | | 'fixed' is positioned like 'absolute' but ignores scrolling.
[`right`][top_right_bottom_left] | auto \| \<length\> \| \<percentage\> | auto | positioned elements | no | width of containing block | 
[`row-gap`][gap] | \<length\> \| \<percentage\> | 0px | table elements | no | initial height of table | 
[`scrollbar-margin`][scrollbar-margin] | \<length\> | 0px | scrollbar-horizontal and scrollbar-vertical elements | no | | Introduced for CSS. Specifies a bottom / right margin (depending on orientation) that will collapse with the scrollbar on the complementary axis.
[`tab-index`][tab-index] | none \| auto | none | all | no | | Introduced for CSS. Controls order of focus switching when the tab key is pressed.
[`text-align`][text-align] | left \| right \| center | left | block-level elements | yes | | 'justify' not supported.
[`text-decoration`][text-decoration] | none \| underline \| overline \| line-through | none | all | yes | | 
[`text-transform`][text-transform] | none \| capitalize \| uppercase \| lowercase | none | all | yes | | 
[`top`][top_right_bottom_left] | auto \| \<length\> \| \<percentage\> | auto | positioned elements | no | height of containing block | 
[`transition`][transition] | See [transitions](animations_transitions_transforms.html#transition) | none | all | no | | 
[`transform`][transform] | none \| \<transform-function\>+ | none | all | no | | 
[`transform-origin`][transform-origin] | \[\<transform-origin-x\> \|\| \<transform-origin-y\>\] \<transform-origin-z\>? | 50% 50% 0px | all | no | | 
[`vertical-align`][vertical-align] | baseline \| sub \| super \| text-top \| text-bottom \| middle \| top \| center \| bottom \| \<percentage\> \| \<length\> | baseline | inline-level elements | no | line-height | 
[`visibility`][visibility] | visible \| hidden | visible | all | no | | 
[`white-space`][white-space] | normal \| pre \| nowrap \| pre-wrap \| pre-line | normal | all elements | yes | | 
[`word-break`][word-break] | normal \| break-all \| break-word | normal | all elements | yes | | 
[`width`][width] | \<length\> \| \<percentage\> \| auto | auto | block and replaced inline elements | no | width of containing block | 
[`z-index`][z-index] | \<number\> \| auto | auto | all | no | | Applies to all elements. For documents, 'auto' allows pulling to front, otherwise remains at top or bottom. 


[align-content]: flexboxes.html#align-content
[align-items]: flexboxes.html#align-items
[align-self]: flexboxes.html#align-self
[animation]: animations_transitions_transforms.html#animation
[background-color]: colours_backgrounds.html#background-color
[background]: colours_backgrounds.html#background-color
[border]: box_model.html#border
[border-color]: box_model.html#border-color
[border-radius]: colours_backgrounds.html#border-radius
[border-width]: box_model.html#border-width
[box-sizing]: user_interface.html#box-sizing
[caret-color]: user_interface.html#caret-color
[clear]: visual_formatting_model.html#clear
[clip]: visual_effects.html#clip
[color]: colours_backgrounds.html#color
[cursor]: user_interface.html#cursor
[decorator]: decorators.html#decorator
[display]: visual_formatting_model.html#display
[drag]: user_interface.html#drag
[fill-image]: {{"pages/cpp_manual/element_packages/progress_bar.html#fill-image"|relative_url}}
[flex]: flexboxes.html#flex
[flex-basis]: flexboxes.html#flex-basis
[flex-direction]: flexboxes.html#flex-direction
[flex-flow]: flexboxes.html#flex-flow
[flex-grow]: flexboxes.html#flex-grow
[flex-shrink]: flexboxes.html#flex-shrink
[flex-wrap]: flexboxes.html#flex-wrap
[float]: visual_formatting_model.html#float
[focus]: user_interface.html#focus
[font]: fonts.html#font
[font-effect]: font_effects.html#font-effect
[font-family]: fonts.html#font-family
[font-size]: fonts.html#font-size
[font-style]: fonts.html#font-style
[font-weight]: fonts.html#font-weight
[gap]: tables.html#gap
[height]: visual_formatting_model_details.html#height
[image-color]: colours_backgrounds.html#image-color
[justify-content]: flexboxes.html#justify-content
[letter-spacing]: text.html#letter-spacing
[line-height]: visual_formatting_model_details.html#line-height
[margin]: box_model.html#margin
[max-height]: visual_formatting_model_details.html#max-height
[max-width]: visual_formatting_model_details.html#max-width
[min-height]: visual_formatting_model_details.html#min-height
[min-width]: visual_formatting_model_details.html#min-width
[nav]: user_interface.html#nav
[opacity]: colours_backgrounds.html#opacity
[overflow]: visual_effects.html#overflow
[overscroll-behavior]: user_interface.html#overscroll-behavior
[padding]: box_model.html#padding
[perspective]: animations_transitions_transforms.html#perspective
[perspective-origin]: animations_transitions_transforms.html#perspective-origin
[pointer-events]: user_interface.html#pointer-events
[position]: visual_formatting_model.html#position
[scrollbar-margin]: ../style_guide.html#scrollbar-margin
[tab-index]: user_interface.html#tab-index
[text-align]: text.html#text-align
[text-decoration]: text.html#text-decoration
[text-transform]: text.html#text-transform
[top_right_bottom_left]: visual_formatting_model.html#top_right_bottom_left
[transition]: animations_transitions_transforms.html#transition
[transform]: animations_transitions_transforms.html#transform
[transform-origin]: animations_transitions_transforms.html#transform-origin
[vertical-align]: tables.html#vertical-align
[vertical-align]: visual_formatting_model_details.html#vertical-align
[visibility]: visual_effects.html#visibility
[white-space]: text.html#white-space
[width]: visual_formatting_model_details.html#width
[word-break]: text.html#word-break
[z-index]: visual_formatting_model.html#z-index
