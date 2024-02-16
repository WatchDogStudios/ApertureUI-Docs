---
layout: page
title: Text Elements
parent: C++
next: custom_elements
---

APUI uses text elements, `apui::ElementText` derived from `apui::Element`, to store and render loose text. Text elements are generated automatically for text in HTML documents, and can be created dynamically by using the '#text' element instancer through the APUI factory, or through the `CreateTextNode()` function on a document.

### Text encoding

The string type used throughout APUI `apui::String` is an alias for `std::string`. This is always assumed to be encoded in UTF-8. This allows storing any Unicode character efficiently, and is compatible with the standard ASCII characters. There are some helper functions for iterating over UTF-8 encoded strings in `APUI/Core/StringUtilities.h`.

### HTML characters

APUI text nodes support a subset of the full HTML-encoding for special characters to allow XML characters to be present in loose text. The characters supported are:

* The less-than symbol,
* The greater-than symbol
* The ampersand symbol
* A non-breaking space. 

You should use these symbols instead of their literal equivalents when putting them into HTML. For example, the following HTML fragment will most likely generate a parse error:

```html
<p>You shouldn't use < or > characters in loose text.</p>
```

The following fragment puts the characters in correctly:

```html
<p>You shouldn't use &lt; or &gt; characters in loose text.</p>
```

### Setting an element's text

The `SetText()` function on a `apui::ElementText` will change the text on the text element to a new string.

```cpp
// Sets the raw string this text element contains.
// @param[in] text The new string to set on this element.
void SetText(const apui::String& text);
```

Note that this sets the raw text on the element; the actual rendered text may differ due to whitespace processing.

### Retrieving an element's text

The `GetText()` function will return the element's raw text.

```cpp
// Returns the raw string this text element contains.
// @return This element's raw text.
const apui::String& GetText() const;
```

### String generation

Text elements are capable of generating formatted sub-sections of their content. This is generally only required by custom elements placing text internally; see the section on hidden elements for more information.
