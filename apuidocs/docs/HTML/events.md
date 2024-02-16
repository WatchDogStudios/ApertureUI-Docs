---
layout: page
title: HTML Events
parent: HTML
next: images
---

The event system is based on the extremely flexible DOM event system. When an event is fired at a target element, it **captures** from the root to the target and then **bubbles** back up to the root. Event listeners can be attached in either capture or bubble phase. Binding done in HTML will always attach to the bubble phase.

Some events do not execute the bubble phase. For additional details, see the [C++ events documentation](../cpp_manual/events.html).

### HTML binding

Event listeners can be bound to an element declared in HTML by specifying an attribute with the name of the event to bind to prefixed with `on`. For example, to bind a listener to the `click` event, you would declare something like the following:

```html
<button onclick="load game">Start Game</button>
```

Note that this is the only time you prefix the event name with `on`; all other times an event is referenced, it is done so simply with its name.

### Events

Below is a list of events and their associated event attributes.

A number of input events send through key modifiers. In this case the following parameters are set to true if the key modifier is active when the action takes place:

* ctrl_key
* shift_key
* meta_key
* alt_key
* caps_lock_key
* num_lock_key
* scroll_lock_key 

#### General Events

`show`
: Sent to a document when it is made visible.

`hide`
: Sent to a document when it is made invisible.

`resize`
: Sent to a document when its context has been resized.

`scroll`
: Sent to an element when it is scrolled.

`focus`
: Sent to an element when it becomes the main focus.
* `focus_visible`: Set to true if focus should be visually indicated.

`blur`
: Sent to an element when it has focus removed.


#### Keyboard Events

`keydown`
: Sent to the focus element when a key is pressed.
* `key_identifier`: A value from the `apui::Input::KeyIdentifier` enumeration (found in `<APUI/Core/Input.h>`).
* Key modifiers. 

`keyup`
: Sent to the focus element when a key is released.
* `key_identifier`: A value from the `apui::Input::KeyIdentifier` enumeration.
* Key modifiers. 

`textinput`
: Sent to the focus element when one or more text characters are entered.
* `text`: An `apui::String` of characters encoded in UTF-8.

#### Mouse Events

All mouse events send through key modifiers.

`click`
: Sent to the element under the mouse cursor when a mouse button is clicked. A click is defined as a button press followed by a button release over the same element.
* `mouse_x`: The mouse x position within the context.
* `mouse_y`: The mouse y position within the context.
* `button`: The mouse button number that was clicked. 

`dblclick`
: Sent to the element under the mouse cursor when a mouse button is double clicked. Note that the `click` event will always be sent before `dblclick`.
* `mouse_x`: The mouse x position within the context.
* `mouse_y`: The mouse y position within the context.
* `button`: The mouse button number that was clicked. 

`mouseover`
: Sent to an element as the mouse cursor moves onto it.
* `mouse_x`: The mouse x position within the context.
* `mouse_y`: The mouse y position within the context. 

`mouseout`
: Sent to an element as the mouse cursor moves off it.
* `mouse_x`: The mouse x position within the context.
* `mouse_y`: The mouse y position within the context. 

`mousemove`
: Sent to the element under the mouse cursor when the mouse is moved.
* `mouse_x`: The mouse x position within the context.
* `mouse_y`: The mouse y position within the context. 

`mouseup`
: Sent to the element under the mouse cursor when a mouse button is released.
* `mouse_x`: The mouse x position within the context.
* `mouse_y`: The mouse y position within the context.
* `button`: The mouse button number that was released. 

`mousedown`
: Sent to the element under the mouse cursor when a mouse button is pressed down.
* `mouse_x`: The mouse x position within the context.
* `mouse_y`: The mouse y position within the context.
* `button`: The mouse button number that was pressed. 

`mousescroll`
: Sent to the focus element when the mouse's scroll wheel is scrolled, or [autoscroll mode](../cpp_manual/contexts.html#autoscroll) is being initiated. The scroll can be cancelled by stopping the event's propagation.
* `mouse_x`: The mouse x position within the context.
* `mouse_y`: The mouse y position within the context.
* `wheel_delta_x`: The distance the wheel has been scrolled horizontally, as a float value with positive values to the right.
* `wheel_delta_y`: The distance the wheel has been scrolled vertically, as a float value with positive values down.
* `autoscroll`: Set to true if autoscroll is being initiated.

#### Dragging Events

All mouse drag events send through key modifiers.

`dragstart`
: Sent to an element when it is first dragged, before the first drag event.
* `mouse_x`: The mouse x position within the context.
* `mouse_y`: The mouse y position within the context.
* `drag_element`: The element that is being dragged. 

`dragend`
: Sent to the dragged element when the mouse button is released.
* `mouse_x`: The mouse x position within the context.
* `mouse_y`: The mouse y position within the context.
* `drag_element`: The element that is being dragged. 

`drag`
: Sent to the dragged element when the mouse is moved.
* `mouse_x`: The mouse x position within the context.
* `mouse_y`: The mouse y position within the context.
* `drag_element`: The element that is being dragged. 

The following events are only sent if the dragged element has a drag property of **drag-drop**. They are sent to elements other than the dragged element, usually as the mouse moves across them.

`dragover`
: Sent during a drag operation to an element when the mouse cursor is moved onto the element (similarly to the mouseover event).
* `mouse_x`: The mouse x position within the context.
* `mouse_y`: The mouse y position within the context.
* `drag_element`: The element that is being dragged. 

`dragout`
: Sent during a drag operation to an element when the mouse cursor is moved off the element (similarly to the mouseout event).
* `mouse_x`: The mouse x position within the context.
* `mouse_y`: The mouse y position within the context.
* `drag_element`: The element that is being dragged. 

`dragmove`
: Sent during a drag operation to the top-most element being hovered over (excluding the dragged element) when the mouse is moved.
* `mouse_x`: The mouse x position within the context.
* `mouse_y`: The mouse y position within the context.
* `drag_element`: The element that is being dragged. 

`dragdrop`
: Sent at the end of a drag operation to the element the cursor is hovering over.
* `mouse_x`: The mouse x position within the context.
* `mouse_y`: The mouse y position within the context.
* `drag_element`: The element that is being dragged. 


#### Animation events

`animationend`
: Sent when an animation has finished executing.
* `property`: The name of the property which has finished animating.

`transitionend`
: Sent when a transition has finished executing.
* `property`: The name of the property which has finished transitioning.

#### Form Events

`submit`
: Sent to the form when it is submitted.
* `parameters`: The event object will have an attribute for each named value in the form. 

#### Form Control Events

`change`
: Sent to a form control when its value is changed.
* `value`: The new value. 

#### Document Events

`load`
: Sent to a document when it is initially loaded. 

`unload`
: Sent to a document when it is unloaded. 

#### Handle Events

`handledrag`
: Sent to the handle when it is moved.
* `handle_x`: Handle x position.
* `handle_y`: Handle y position. 

#### DataGrid Events

`columnadd`
: Sent to the data grid when a column is added.
* `index`: Index of the column that was added. 

`rowupdate`
: Sent to the data grid when any rows in the table are loaded. 

`rowadd`
: Sent to the data grid when rows are added to the table.
* `first_row_added`: Index of the first row added.
* `num_rows_added`: The number of rows added after the first row. 

`rowremove`
: Sent to the data grid when rows are removed from the table.
* `first_row_removed`: Index of the first row removed.
* `num_rows_removed`: The number of rows removed after the first row. 

#### TabSet Events

`tabchange`
: Sent to the tab set when the active tab is changed.
* `tab_index`: The new tab index. 

