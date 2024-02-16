---
layout: page
title: HTML Controls
parent: html
next: data_display
---

### \<handle\>

The `<handle>` element can be used to move or change the size of elements.

_Attributes_

`move_target` = idref (CI)
: If specified, the handle will move the element specified by the ID when dragged. Can be `#document` to reference the current document, or `#parent` to reference the parent element.

`size_target` = idref (CI)
: If specified, the handle will size the element specified by the ID when dragged. Can be `#document` to reference the current document, or `#parent` to reference the parent element.

During drag operations, the handle element will size the target element by adjusting its `width` and `height` properties, while it will move the target by adjusting its `top` and `left` properties.

```html
<div id="bucket">Bucket</div>
<handle move_target="bucket">Drag to move the bucket.</handle>
```

```html
<handle move_target="#document">
	<div id="title">My document</div>
</handle>
```

```html
<div class="help_box">
	<handle size_target="#parent"/>
</div>
```


### \<tabset\>

A `<tabset>` element contains `<tab>` elements and `<panel>` elements.

See also the [tab set documentation]({{"pages/cpp_manual/element_packages/tab_set.html"|relative_url}}) in the C++ manual.

#### \<tab\>

Each `<tab>` element acts as a button, that when clicked will hide the currently visible panel and show its corresponding panel.

#### \<panel\>

A `<panel>` element is the body of the tabset. The visibility of the panel is controlled by the tab elements in the parent tabset.
