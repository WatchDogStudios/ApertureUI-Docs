---
layout: page
title: Elements
parent: HTML
next: documents
---

APUI has no prior understanding of XML elements other than the built-in [element types](element_index.html).

When parsing a tag APUI will look up custom elements associated with the tag name and fall back to a generic element. Very few custom elements are required as most of the power in APUI comes from styling elements with [CSS](../css.html) to produce the desired layout.

The user is encouraged to follow standard HTML guidelines where possible to improve readability across the community. For more information on setting up APUI to emulate HTML4 see [Appendix: HTML4 Style Sheet](html4_style_sheet.html).

### Global Attributes

Elements have a base set of attributes that are common to all types, which are:

`id` = id (CS)
: The unique identifier for the element in this document.

`class` = cdata (CI)
: Assigns a class name or set of class names to an element. Any number of elements may be assigned the same class name or names. Multiple class names must be separated by white space characters. See [CSS](../css.html).

`style` = cdata (CS)
: Specifies inline style information for the element. See [CSS](../css.html).

`lang` = language-code (CI)
: Specifies the language of the element's text. Value is passed to the font engine to assist with text shaping. Inherited by child elements.

`dir` = ltr | rtl | auto (CS)
: Specifies the flow direction of the element's text. Value is passed to the font engine to assist with text shaping. Inherited by child elements. Unlike HTML, this attribute is case-sensitive and does not affect document layout.

`on*` events = cdata (CS)
: Event bindings. See [Events](events.html).

`data-*` data bindings = cdata (CS)
: Denotes views and controllers for [data bindings](../data_bindings.html).
