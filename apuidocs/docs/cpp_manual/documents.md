---
layout: page
title: Documents
parent: cpp_manual
next: contexts
---

Documents are container [elements](elements.html). They are designed to represent a single `window' within your application's interface. Documents are elements themselves, and the elements they contain directly are parented to them.

### Identification

Documents have a title, defined in RML by contents of the `<title>` tag within the document header. By default the title does not do anything, but can be used to populate the contents of a title bar (as in the _Rocket Invaders from Mars_ demo). The function `GetTitle()` will return the document's title, `SetTitle()` will set it.

```cpp
// Sets the document's title.
// @param[in] title The new title of the document.
void SetTitle(apui::String& title);

// Returns the title of this document.
// @return The document's title.
const apui::String& GetTitle() const;
```

If a document was loaded from an RML file, the function `GetSourceURL()` will return the path of the source RML.

```cpp
// Returns the source address of this document.
// @return The source of this document, usually a file name.
const apui::String& GetSourceURL() const;
```

### Documents and contexts

Every document is part of a single context. The documents within a context are layered similarly to windows on a desktop. Document layering can be controlled through user input (ie, when a document is clicked on, by default it is raised to the top), programatically or through the `z-index` property.

The function `GetContext()` will return the document's context.

```cpp
// Returns the document's context.
// @return The context this document exists within.
apui::Context* GetContext();
```

#### Layering

The `z-index` property of a document controls the rendering order similarly to elements. A document with a higher `z-index` will always be rendered on top of a document with a lower `z-index`. Documents start with a default `z-index` of `0`.

The functions `PullToFront()` and `PushToBack()` will move the document to the front and back of the document stack among documents with a similar `z-index`. For example, calling `PullToFront()` on a document with a `z-index` of `1` will force all documents with a `z-index` lower than `1`, and all other documents with a `z-index` of `1`, to be rendered before it. However, documents with a higher `z-index` will still be rendered after it.

```cpp
// Brings the document to the front of the document stack.
void PullToFront();

// Sends the document to the back of the document stack.
void PushToBack();
```

Pulling and pushing documents only affects the document stack at the moment it is called. If further documents are loaded, or other documents are pushed and pulled, the document stack will change.

#### Layering and the mouse

By default, if the primary mouse button is pressed while hovering over a document, that document will be brought to the front of the document stack (similarly to a `PullToFront()` call). If a document has any `z-index` value other than the default of `auto`, this behaviour will not occur.

### Visibility

When a document is loaded into a context, it begins hidden (it has a `visibility` value of `hidden`). To show a document, use the `Show()` function:

```cpp
// Show the document.
// @param[in] modal_flag Flags controlling the modal state of the document, see the 'ModalFlag' description for details.
// @param[in] focus_flag Flags controlling the focus, see the 'FocusFlag' description for details.
void Show(ModalFlag modal_flag = ModalFlag::None, FocusFlag focus_flag = FocusFlag::Auto);
```
By default, the `Show()` function will make the document visible and switch keyboard focus to the document and if possible the first control element with an `autofocus` attribute set. The focus behavior as well as the modal state can be controlled with two separate flags. The flags are specified as follows:
```cpp
/**
	 ModalFlag used for controlling the modal state of the document.
		None:  Remove modal state.
		Modal: Set modal state, other documents cannot receive focus.
		Keep:  Modal state unchanged.

	FocusFlag used for displaying the document.
		None:     No focus.
		Document: Focus the document.
		Keep:     Focus the element in the document which last had focus.
		Auto:     Focus the first tab element with the 'autofocus' attribute or else the document.
*/
enum class ModalFlag { None, Modal, Keep };
enum class FocusFlag { None, Document, Keep, Auto };
```

To hide a document, call `Hide()`.

```cpp
// Hide the document.
void Hide();
```

### Manually updating the document

The document is [always updated](contexts.html#update-and-rendering) during the call to `Context::Update()`. However, sometimes it may in addition be necessary to update the document manually so that elements can be queried for their layed out size or position, in particular after elements have been modified or added to the document.

```cpp
// Updates the document, including its layout. Users must call this manually before requesting information such as 
// size or position of an element if any element in the document was recently changed, unless Context::Update has
// already been called after the change. This has a perfomance penalty, only call when necessary.
void ElementDocument::UpdateDocument();
```

See more on the [validity of retrieved element values](elements.html#validity-of-retrieved-values).

### Closing

Calling `Close()` on a document will remove the document from its context and destroy it and all of its elements.

```cpp
// Close the document.
void Close();
```

Documents aren't actually destroyed until the next call to `Context::Update()` or `apui::Shutdown()`, so event listeners attached to the document or any of its children must be kept alive until then.

### Creating new elements

Similarly to HTML documents, APUI documents are capable of creating new elements and text nodes. You can use the `CreateElement()` function to create a new element of a certain type:

```cpp
// Creates the named element.
// @param[in] name The tag name of the element.
apui::ElementPtr CreateElement(const apui::String& name);
```

The name parameter is the desired tag name of the new element. Note that as you cannot specify an independent instancer name or RML attributes to pass to the instancer, this method is not as flexible as creating an element through the factory, but is useful for easily creating simple elements.

Call `CreateTextNode()` to create a new text element with a given text string:

```cpp
// Create a text element with the given text content.
// @param[in] text The text content of the text element.
apui::ElementPtr CreateTextNode(const apui::String& text);
```

The text parameter will be interpreted as a UTF-8 encoded string. The element returned will be derived from `apui::ElementText`.

Note that neither of these functions actually attaches the new element to the document in any way. See the description of [elements](elements.html#using-a-document) for details on how to do this.

### Custom documents

All documents are instanced like normal elements from the 'body' tag. The process for creating a custom document type is identical to that for [creating a custom element](custom_elements.html), except you should derive from `apui::ElementDocument` instead of `apui::Element`, and only register the element instancer against the `<body>` tag.

If you register an instancer for the `<body>` tag that returns an element not derived from `apui::ElementDocument`, documents will fail to load.

There is one virtual function that is particular to `apui::ElementDocument`:

```cpp
// Load a script into the document.
// @param[in] stream Stream of code to process.
// @param[in] source_name Name of the the script the source comes from, useful for debug information.
virtual void LoadScript(apui::Stream* stream, const apui::String& source_name);
```

`LoadScript()` is generally only used to integrate a scripting language into APUI. It is called on a document for every `<script>` tag with the script content. The default implementation does nothing; custom documents can do whatever they need to here to load, compile and bind the scripts for their elements. 