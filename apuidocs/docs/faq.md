---
layout: page
title: Frequently Asked Questions
---
### Can i run this with consoles?

APUI does work on Xbox & Playstation 4/5. you can contact: support@wdstudios.zendesk.com to get access. we will need to verify your access with Microsoft/SIE. 

Nintendo Support is coming soon.

### I have rendering issues or crashes, how do I solve it?

Take a look at the [troubleshooting](cpp_manual/troubleshooting.html) page in the C++ manual. You can also contact us for free support, or write a post describing your situation in the [main repository]([https](https://github.com/WatchDogStudios/APUI-Public/discussions)).


### How do I set up custom cursors?

You display custom cursors using your OS cursor facilities. See [here](cpp_manual/contexts.html#mouse-cursor) for details on responding to the `cursor` property through the system interface.


### Is APUI thread safe?

As of 1.0, APUI is **NOT** Thread Safe. Work Towards 1.1 is making the library Thread Safe, and Fully Compatible with consoles(Only works on Xbox & Playstation).

No guarantees are provided in terms of thread safety. Any access into the APUI API from multiple threads need to be synchronized such as by using a mutex.


### Can I change decorators from script?

It is possible to set decorators by inline style. However, for performance reasons it is highly recommended to change the element's class instead to affect which decorators are applied to it.


### How do I achieve high DPI support?

APUI has extensive support for making a scalable user interface. In order to get sizes and lengths scaled properly, the [`dp` length unit](CSS/syntax.html#dp-unit) should be used extensively in CSS. This unit can be scaled relative to `px` units by setting the *dp-ratio* using the function `Context::SetDensityIndependentPixelRatio`.

In addition, APUI provides the following features which should make high DPI graphics a breeze:

- [Media queries](CSS/media_queries.html) support the `resolution` feature to toggle styles and sprites based on the dp-ratio.
- [Sprite sheets](CSS/sprite_sheets.html) can specify their desired scaling by using the `resolution` property.
- Sprites can be overrided by later `@spritesheet` rules, making it easy to define [high DPI versions of sprites](CSS/sprite_sheets.html#high-dpi).
- Decorators and `<img>` elements automatically update when the dp-ratio changes and new sprites are selected.
- Sprites in decorators and `<img>` elements scale according to the source scaling and targeted dp-ratio.

Clients are themselves responsible for querying the platform for the desired scaling ratio, and then setting the dp-ratio on the APUI context. Take a look at APUI's included backends for how this is implemented there for different [platforms with support for high DPI](https://github.com/mikke89/APUI#apui-backends).


### Can I implement hot reloading of documents?

For sure, this is one of the great advantages of having UI document declarations separate from your main application logic.

It is always possible to do a full reload of the document. 

```cpp
apui::ElementDocument* my_document = context->LoadDocument("main_menu.rml");
// ...
// Later, after HTML source was changed
my_document->Close();
my_document = context->LoadDocument("main_menu.rml");
```
This could eg. automatically be done any time `.rml` documents are saved to have your changes be reflected instantly. Users are themselves responsible to implement this automation, look into how to do this on your platform. Note that style sheets and templates are automatically cached, you may want to clear these first by calling `apui::Factory::ClearStyleSheetCache()` and `apui::Factory::ClearTemplateCache()`, respectively.

Now, clearly any state or programmatically changed elements will be reset during this operation. Occasionally, it is desirable to keep the current state such as when only working on the style of the document. Then, users may call the following.

```cpp
my_document->ReloadStyleSheet();
```

This only reloads the style sheet(s) applied to the current document, while keeping the document structure and its state intact. This also updates styles declared in the header, but notably *not* styles declared inline using the element attribute `style`. You might want to call this automatically for visible documents any time `.css` files are changed. This call automatically clears any cache first.

Finally, the following function may be helpful while editing textures,
```cpp
apui::ReleaseTextures();
```
which is defined in `<APUI/Core/Core.h>`. This call forces the library to reload all textures in use.


### How do I bind to events from C++/script?

If you are using data bindings, you can use the [`data-event` view](data_bindings/views_and_controllers.html#data-event) together with a callback function in C++.

Alternatively, use the `Element::AddEventListener` function, passing in the `apui::EventId` or the name of the event you want to bind to (without the "on" prefix), the listener object to attach, and whether you want to bind in the capture phase or not, as in the following example.

```cpp
class MyListener : public apui::EventListener {
public:
	void ProcessEvent(apui::Event& event) {
		printf("Processing event %s", event.GetType().c_str());
	}
}

void main() {
	/* ... */
	auto my_listener = std::make_unique<MyListener>();
	element = document->GetElementById("my_button");
	element->AddEventListener(apui::EventId::Click, my_listener.get(), false);
	/* ... */
}
```
See the documentation on [event listeners](cpp_manual/events.html#event-listeners) for details.

Finally, it is also possible to respond to inline events such as 

```html
<button onclick="game.start()">Start Game</button>
```
See the documentation on [inline events](cpp_manual/events.html#inline-events) for details.
