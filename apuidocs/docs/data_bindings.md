---
layout: page
title: Data Binding
---







APUI features a model-view-controller (MVC) approach through data bindings. This is a powerful approach for responding to changes in the data, or in reverse, updating data based on user actions.

In the approach taken in APUI, the MVC terms have the following meaning.

- `Model`  The data model is the interface between the user data through data variables, and the views and controllers assigned to the model.
- `View`  Data views are used to present a data variable in the document by different means.
- `Controller` Data controllers typically respond to user input by setting a new value to a data variable.

Views are automatically updated whenever a variable becomes dirty. This ensures that the document displayed to the user is always synchronized with the application data. Using the MVC appoach, there is no need to handle individual elements, or manually modify the HTML.

See the following detailed sections:

- [Examples](Data Bindings/examples.md)
- [Data variables and expressions](Data Bindings/expressions.md)
- [Data model](Data Bindings/model.md)
- [Data views and controllers](Data Bindings/views_and_controllers.md)

---

![Schematic of the control flow in APUI's model-view-controller.](Data Bindings/model-view-controller.svg)

---

##### Limitations

- You should not affect the document structure within a data model. This includes manually adding or removing elements. E.g. removing an element inside a `data-for` view is undefined behavior and may lead to a crash.
- Currently, only top-level data variables can have a dirty state. That means data addresses can not be used to dirty just an Array index or Struct member. However, sub-values that have not been changed will be ignored inside the relevant views.
- Adding `data-` attributes after the element has been attached to the document has no effect.
- Registering `const` objects or member functions, or members inherited from a parent class, is not supported.
- Types may need to be re-registered if binding variables in different dynamic libraries.

##### Element compatibility

- Putting the `data-model` attribute on the `<body>` tag may cause issues when combined with templates.
- Some special elements internally change the structure of the document. For such elements, data bindings may not work as intended. This includes in particular the `<tabset>`, `<panel>` and `<tab>` elements, notably when combined with the `data-for` view.
- The `<select>` element may not always properly reflect changes in the underlying `selected` or `value` attributes of its `<option>`s, or the content of the options. For dynamically changing the selected option, use the `data-value` view on the `<select>` element. Note that, initially populating the options using `data-for` should now work.

##### Authoring notes

- Element attributes starting with `data-` are reserved for data bindings in APUI.
- All use of `{{` and `}}` inside HTML documents are reserved for data bindings.

