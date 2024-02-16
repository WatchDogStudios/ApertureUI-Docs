---
layout: page
title: Element Index
parent: HTML
next: html4_style_sheet
comment: Please run '_tools/generate_elements_and_properties_index.py' whenever elements or their URLs are added or changed.
---

The following is a list of elements supported by HTML:

- [`<rml>`](documents.html#rml)
- [`<head>`](documents.html#head)
- [`<title>`](documents.html#title)
- [`<link>`](documents.html#link)
- [`<style>`](style_sheets.html#style)
- [`<body>`](documents.html#body)
- `<br>`
- [`<handle>`](controls.html#handle)
- [`<img>`](images.html#img)
- [`<form>`](forms.html#form)
- [`<input>`](forms.html#input)
- [`<textarea>`](forms.html#textarea)
- [`<select>`](forms.html#select)
- [`<option>`](forms.html#option)
- [`<label>`](forms.html#label)
- [`<tabset>`](controls.html#tabset)
- [`<tab>`](controls.html#tab)
- [`<panel>`](controls.html#panel)
- [`<progress>`](data_display.html#progress)

See also [element packages]({{"pages/cpp_manual/element_packages.html"|relative_url}}) in the C++ manual for controlling the behavior of several of these elements.

APUI does not provide a default style sheet, thus, tags which only represent a specific style rule in HTML have no special meaning in APUI, such as `<div>`, `<span>` and `<table>`. Users can include the [recommended style sheet](html4_style_sheet.html) to enable common rules for these tags.

The following elements are additionally enabled when including their respective plugins:

- [`<lottie>`](../cpp_manual/lottie.html)
- [`<svg>`](../cpp_manual/svg.html)

---

Deprecated elements:

- [`<datagrid>`](deprecated.html#datagrid)
- [`<col>`](deprecated.html#col)
- [`<dataselect>`](deprecated.html#dataselect)

Users are encouraged to replace these elements with [data bindings](../data_bindings.html) possibly combined with [CSS tables](../CSS/tables.html).
