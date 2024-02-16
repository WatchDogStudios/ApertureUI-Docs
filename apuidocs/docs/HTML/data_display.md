---
layout: page
title: HTML Data Display Elements
parent: HTML
next: element_index
---

See also [data bindings](../data_bindings.html) for dynamically displaying and updating data from the client application.

### \<progress\>

The `<progress>` element can display progress bars and gauges. For a detailed description and styling information see the [progress element]({{"pages/cpp_manual/element_packages/progress_bar.html"|relative_url}}) in the C++ Manual.

_Attributes_

`value` = number (CN)
: A number between `0` and `max`, representing the fraction of the progress element that is filled and where `max` means completely filled.

`max` = number (CN)
: A positive number representing the maximum value, defaults to `1`.

`direction` = cdata (CI)
: The direction the progress bar expands with increasing values. Must be one of:
* `top`
* `right` (default)
* `bottom`
* `left`
* `clockwise`
* `counter-clockwise`

`start-edge` = cdata (CI)
: Only applies to `clockwise` or `counter-clockwise` directions. Defines which edge the
circle should start expanding from. Must be one of:
* `top` (default)
* `right`
* `bottom`
* `left`
