---
layout: page
title: Contexts
parent: cpp_manual
next: events
---

APUI contexts are independent collections of documents. All documents exist within a single context. Contexts are rendered, updated and given input independently of each other at the application's discretion.

### Uses of multiple contexts

Most games will feature a single context for the main interface. Multiple contexts could be used however for a number of different reasons.

#### Multiple desktops

A second or subsequent context could be used to store alternative 'desktops' that the user could switch to, in a similar fashion to many Linux desktops. This could be very useful for interface-heavy games where the user may have several windows open at once, more than could fit easily onto one screen.

#### In-world interfaces

Computer terminals or consoles in a 3D game world could themselves be APUI contexts. As they wouldn't necessarily be viewed parallel to the screen, mouse input would need to be projected onto the surface. When the context was rendered, it would need to be transformed correctly to fit onto the surface or rendered onto a texture.

### Creating a context

To create a new context, use the `apui::CreateContext()` function.

```cpp
// Creates a new element context.
// @param[in] name The new name of the context. This must be unique.
// @param[in] dimensions The initial dimensions of the new context.
// @return The new context, or nullptr if the context could not be created.
apui::Context* CreateContext(const apui::String& name,
                                     const apui::Vector2i& dimensions);
```

The context needs a unique string name and initial dimensions. The dimensions are used to generate relative lengths (for example, if a document has a percentage dimension), and sets the extents for the mouse cursor within the context.

To fetch a previously-constructed context, use the `GetContext()` function.

```cpp
// Fetches a previously constructed context by name.
// @param[in] name The name of the desired context.
// @return The desired context, or nullptr if no context exists with the given name.
apui::Context* GetContext(const apui::String& name);
```

### Releasing a context

A context can be manually removed by calling the following function.

```cpp
// Removes and destroys a context.
// @param[in] name The name of the context to remove.
// @return True if name is a valid context, false otherwise.
bool RemoveContext(const apui::String& name);
```
All remaining contexts are destroyed during the call to `apui::Shutdown()`.

### Update and rendering

If a context is active, it should have `Update()` called on it after the frame's input events have been sent to it.

```cpp
// Updates all elements in the context's documents.
bool Update();
```

The context update ensures that properties and computed values of all elements located in the context are updated, and layouting is performed on all documents that need it. Elements may not always report their correct size or position until the context is updated, as described on the [elements page](elements.html#validity-of-retrieved-values).

To render a context, call `Render()` on it. Easy!

```cpp
// Renders all visible elements in the context's documents.
bool Render();
```

See the [main loop documentation](main_loop.html) for how these calls fits into an application's main loop. See also [on-demand rendering](#on-demand-rendering) below, for utilities allowing the application to delay update and rendering, in case there is a desire to reduce resource consumption when idle.

### Loading and creating documents

Documents are loaded through contexts. To load a document from an RML file into a context, call the `LoadDocument()` function on the appropriate context.

```cpp
// Load a document into the context.
// @param[in] document_path The path to the document to load.
// @return The loaded document, or nullptr if no document was loaded.
ElementDocument* LoadDocument(const apui::String& document_path);
```

The `document_path` parameter will be given to APUI's [file interface](interfaces/file.html) to be open and read. If the document is loaded successfully, it will be added to the context and returned. Call `Show()` on the document to make it visible.

You can also load documents directly from a memory stream, this can be useful if you want to receive documents over the network or similar.

```cpp
/// Load a document into the context.
/// @param[in] document_rml The string containing the document RML.
/// @param[in] source_url Optional string used to set the document's source URL, or naming the document for log messages.
/// @return The loaded document, or nullptr if no document was loaded.
ElementDocument* LoadDocumentFromMemory(const String& document_rml, const String& source_url = "[document from memory]");
```

To create a new, empty document you can populate dynamically, use the `CreateDocument()` function.

```cpp
/// Creates a new, empty document and places it into this context.
/// @param[in] instancer_name The name of the instancer used to create the document.
/// @return The new document, or nullptr if no document could be created.
ElementDocument* CreateDocument(const String& instancer_name = "body");
```

The context will attempt to instance an element using the instancer specified by the caller, 'body' by default. If an `apui::ElementDocument` is instanced, it will be added to the context and returned.

### Scrolling

The context can initiate scrolling in multiple ways:

- `ProcessMouseWheel()` may initiate a scroll action on the hover element's closest scrollable ancestor.
- `ProcessMouseButtonDown()` can activate [autoscroll mode](#autoscroll) when the middle mouse button is submitted.
- Further, an element's scrollbar can be dragged, or its scroll position programmatically set.

See the [input documentation](input.html#mouse-buttons) for more details on these functions. In some situations, a scroll action initiates [smooth scrolling](#smooth-scrolling). An element's closest scrollable ancestor is decided by scroll chaining, which can be controlled using the [`overflow-behavior` property](../css/user_interface.html#overscroll-behavior).

#### Autoscroll mode


Autoscroll mode is activated by pressing or holding the middle mouse button. This scrolls the document with a controllable velocity based on the mouse cursor's distance from its initial activation position.

#### Smooth scrolling


Smooth scrolling makes a given scroll action animate smoothly towards its destination. Smooth scrolling can be activated in several situations:

- During a call to `Context::ProcessMouseWheel()`.
- When clicking a scrollbar's arrow keys or track.
- When calling any of the `Element::Scroll...()` methods using `ScrollBehavior::Smooth` or `ScrollBehavior::Auto`.

The default smooth scroll behavior can be configured on the context, and is enabled by default. This affects all scroll actions with auto scroll behavior, including mouse wheel and scrollbar interaction.

```cpp
/// Sets the default scroll behavior, such as for mouse wheel processing and scrollbar interaction.
/// @param[in] scroll_behavior The default smooth scroll behavior, set to instant to disable smooth scrolling.
/// @param[in] speed_factor A factor for adjusting the final smooth scrolling speed, must be strictly positive, defaults to 1.0.
void SetDefaultScrollBehavior(ScrollBehavior scroll_behavior, float speed_factor);
```
By default, smooth scrolling is enabled. It can be disabled by setting the `scroll_behavior` to `ScrollBehavior::Instant`. The speed of the smooth scroll can also be adjusted using the `speed_factor` parameter.


### Mouse cursor

Each context can propagate the mouse cursor name to the user through the [system interface](interfaces/system.html). The cursor name is set on an element through the  [`cursor` property](../css/user_interface.html#cursor). When the cursor name changes, the new name is sent though the interface. The client can then change the displayed cursor using the cursor facilities on their platform.

The submitted cursor name is chosen in the following order.

1. If the context is in autoscroll mode, submit one of the built-in cursor names listed below.
2. Otherwise, if an element is being dragged, the cursor is taken from that element's `cursor` property.
3. Otherwise, if an element is being hovered, the cursor is taken from that element's `cursor` property.
4. Otherwise, an empty string is submitted.

#### Built-in cursor names


The following built-in cursor names are submitted to the system interface under specific conditions.

|        Cursor name        | Description   |
|---------------------------|---------------|
| `apui-scroll-idle`       | Autoscroll mode active, but scrolling is idle.                 |
| `apui-scroll-up`         | Autoscroll mode active, scrolling in the given direction.      |
| `apui-scroll-down`       | "                                                              |
| `apui-scroll-left`       | "                                                              |
| `apui-scroll-right`      | "                                                              |
| `apui-scroll-up-left`    | "                                                              |
| `apui-scroll-up-right`   | "                                                              |
| `apui-scroll-down-left`  | "                                                              |
| `apui-scroll-down-right` | "                                                              |


#### Multiple contexts

In the case of multiple contexts, it might be convenient for only a single context to handle the mouse cursor. The following function can be used to control this behavior:
```cpp
/// Enable or disable handling of the mouse cursor from this context.
/// When enabled, changes to the cursor name is transmitted through the system interface.
/// @param[in] show True to enable mouse cursor handling, false to disable.
void EnableMouseCursor(bool enable);
```
By default it is enabled.

### Media themes


Media themes can be used to activate or deactivate parts of a style sheet in combination with [media queries](../css/media_queries.html), using the `theme` media feature.

```cpp
/// Activate or deactivate a media theme. Themes can be used in CSS media queries.
/// @param theme_name[in] The name of the theme to (de)activate.
/// @param activate True to activate the given theme, false to deactivate.
void ActivateTheme(const String& theme_name, bool activate);
/// Check if a given media theme has been activated.
/// @param theme_name The name of the theme.
/// @return True if the theme is activated.
bool IsThemeActive(const String& theme_name) const;
```

### Events

Event listeners can be attached to a context (rather than an element) to receive events sent to all elements within that context. As with elements, call `AddEventListener()` to attach a listener and `RemoveEventListener()` to detach.

```cpp
// Adds an event listener to the context's root element.
// @param[in] event The name of the event to attach to.
// @param[in] listener Listener object to be attached.
// @param[in] in_capture_phase True if the listener is to be attached to the capture phase, false for the bubble phase.
void AddEventListener(const apui::String& event,
                      apui::EventListener* listener,
                      bool in_capture_phase = false);

// Removes an event listener from the context's root element.
// @param[in] event The name of the event to detach from.
// @param[in] listener Listener object to be detached.
// @param[in] in_capture_phase True to detach from the capture phase, false from the bubble phase.
void RemoveEventListener(const apui::String& event,
                         apui::EventListener* listener,
                         bool in_capture_phase = false);
```

Note as for all raw pointers, they are non-owning. Thus, it is the user's responsibility to keep the event listener alive until it is removed, and then to clean it up.

### Input

See the section on [input](input.html) for detail on sending user input from your application into APUI contexts.

### On-demand rendering (power saving mode)


In the graphics world we can roughly divide applications into two groups. 

1. Applications that aim to pump out as many frames as possible, as fast as possible, such as games.
2. Other applications that only redraw their window when their contents change, to reduce CPU usage and power consumption.

APUI provides utilities to handle either of these cases, to suit the target application's requirements. Users of APUI control their own update loop, thus, doing it the first way is as simple as running the context update and rendering in a loop, without delay. On the other hand, the second approach requires some support from the library side, because the application needs to know e.g. when animations are happening or when a text cursor should blink.

#### Loop update triggers

During on-demand rendering, the application needs to update the user interface in the following situations:

1. When time-dependent, library-internal changes affect the rendered output.
2. When platform events are received.
3. When the application wants to make their own changes to the document.

This feature is intended to assist in the first case. The second case depends on the user's platform, and is outside the responsibility of the library itself, but there are many examples in the [included backends](https://github.com/mikke89/APUI/tree/master/Backends). The last case is fully up to the user, it is their own responsibility to know when they need to make their own changes to the interface, and to decide how to proceed.

#### Update delay utilities

Opting in to on-demand rendering requires explicit support by the code that drives the update loop. The feature consists of two functions which can be used to manipulate a time value.

```cpp
// Updates the time until Update should get called again.
// @param[in] delay Maximum time until next update
void RequestNextUpdate(double delay);
```

This function is used by APUI and custom elements to set the delay until the user interface should be rendered again, unless platform events are received in-between. This is not a direct setter, it takes the minimum value of the already stored and the passed-in value.

The rendering loop can then use the following function to retrieve the value in the range zero to infinity.

```cpp
// Get the max delay until update and render should get called again
// @return Time until next update is expected.
double GetNextUpdateDelay() const;
```

A returned value of zero means the rendering loop should not block for events, that is, render the next frame as soon as possible. This happens for example if an animation is playing. A non-zero, finite value means a delay in seconds until the update and render loop should be invoked again. Infinity means there is no reason to redraw the content at all unless a platform event is received. This is the usual case if there are no custom elements or running animations. 

You can see this in action by tweaking the `power_save` flag passed to `Backend::Process()` function in the [provided samples](https://github.com/mikke89/APUI/blob/master/Samples/basic/loaddocument/src/main.cpp). This is implemented in most of the [included backends](https://github.com/mikke89/APUI/tree/master/Backends), take a look at the `APUI_Backend_….cpp` files to see how this functionality is integrated there.

### Custom contexts

Contexts are created, like elements and decorators, through instancers. You can override the default context instancer if you want to create custom contexts. Generally, this is only required for adding support for scripting languages.

#### Creating a custom context

A custom context is a class derived from `apui::Context`. There are no virtual methods on `apui::Context`, so it cannot be specialised.

#### Creating a custom context instancer

A custom context instancer needs to be registered with the APUI factory in order to override the default instancer. A custom context instancer needs to be derived from `apui::ContextInstancer`, and implement the required virtual methods:

```cpp
// Instances a context.
// @param[in] name Name of this context.
// @return The instanced context.
virtual apui::ContextPtr InstanceContext(const apui::String& name) = 0;

// Releases a context previously created by this context.
// @param[in] context The context to release.
virtual void ReleaseContext(apui::Context* context) = 0;

// Releases this context instancer
virtual void Release() = 0;
```

`InstanceContext()` will be called whenever a new context is requested. It takes a single parameter, name, the name of the new context. If a context can be created, it should be initialised and returned wrapped in a `ContextPtr` which is a unique pointer with a custom deleter. Otherwise, return nullptr.

`ReleaseContext()` will be called whenever a context is released. The context instancer should destroy the context and free and resources allocated for it.

`Release()` will be called when APUI is shut down. The instancer should delete itself if it was dynamically allocated.

#### Registering an instancer

To register a custom instancer with APUI, call `RegisterContextInstancer()` on the APUI factory after APUI has been initialised.

```cpp
// The custom_instancer must be kept alive until after the call to apui::Shutdown()
auto custom_instancer = std::make_unique<CustomContextInstancer>();
apui::Factory::RegisterContextInstancer(custom_instancer.get());
```

Like for other instancers, it is the user's responsibility to manage the lifetime of the instancer. Thus, it must be kept alive until after the call to `apui::Shutdown()`, and then cleaned up by the user.

#### Enumerating Contexts

All active contexts can be enumerated via the `apui::GetNumContexts()` and `apui::GetContext(int index)` function calls. 