---
layout: page
title: Lua API Reference
parent: LuaGuide
---

Most of the Lua types, properties, and functions listed in this reference correspond directly to their C++ API equivalent, users are encouraged to take a look at the [C++ Manual](../cpp_manual.html) for more detailed descriptions.

All instantiable classes define a `new()` function which returns an object of that particular class. With the exception of this `new()` function, all members listed will be member functions.

#### Main Types
- [Context](#Context)
- [Document](#Document)
- [Element](#Element)
- [Event](#Event)
- [apui](#apui)

#### Utility

- [Colourb](#Colourb)
- [Colourf](#Colourf)
- [DataFormatter](#DataFormatter)
- [DataSource](#DataSource)
- [ElementInstancer](#ElementInstancer)
- [ElementPtr](#ElementPtr)
- [GlobalLuaFunctions](#GlobalLuaFunctions)
- [Log](#Log)
- [Vector2f](#Vector2f)
- [Vector2i](#Vector2i)

#### Special Elements

- [ElementDataGrid](#ElementDataGrid)
- [ElementDataGridRow](#ElementDataGridRow)
- [ElementForm](#ElementForm)
- [ElementFormControl](#ElementFormControl)
- [ElementFormControlDataSelect](#ElementFormControlDataSelect)
- [ElementFormControlInput](#ElementFormControlInput)
- [ElementFormControlSelect](#ElementFormControlSelect)
- [ElementFormControlTextArea](#ElementFormControlTextArea)
- [ElementTabSet](#ElementTabSet)
- [ElementText](#ElementText)

#### Enumerations

- [DocumentFocus](#DocumentFocus)
- [DocumentModal](#DocumentModal)

#### Proxy
- [ContextDocumentsProxy](#ContextDocumentsProxy)
- [ElementAttributesProxy](#ElementAttributesProxy)
- [ElementChildNodesProxy](#ElementChildNodesProxy)
- [ElementStyleProxy](#ElementStyleProxy)
- [EventParametersProxy](#EventParametersProxy)
- [APUIContextsProxy](#APUIContextsProxy)
- [SelectOptionsProxy](#SelectOptionsProxy)


---

### <a href='#Colourb' name='Colourb'>Colourb</a>

Inherits: `nil`

Constructs a colour with four channels, each from 0 to 255.

#### Properties

| Name | Type |
| ------------ | ---- |
| [alpha](#Colourb-alpha) | `integer` |
| [blue](#Colourb-blue) | `integer` |
| [green](#Colourb-green) | `integer` |
| [red](#Colourb-red) | `integer` |
| [rgba](#Colourb-rgba) | `integer, integer, integer, integer` |


#### Functions

| Name | Return Type |
| ------------ | ---- |
| [new](#Colourb-new)(`integer` red, `integer` green, `integer` blue, `integer` alpha) | `Colourb` |


#### Metafunctions

| Metafunctions |
| ------------- |
| __add |
| __eq |
| __mul |


#### Property Descriptions

<a href='#Colourb-alpha' name='Colourb-alpha'>alpha</a>  :: `integer`
: Alpha channel

<a href='#Colourb-blue' name='Colourb-blue'>blue</a>  :: `integer`
: Blue channel

<a href='#Colourb-green' name='Colourb-green'>green</a>  :: `integer`
: Green channel

<a href='#Colourb-red' name='Colourb-red'>red</a>  :: `integer`
: Red channel

<a href='#Colourb-rgba' name='Colourb-rgba'>rgba</a>  :: `integer`, `integer`, `integer`, `integer`


#### Function Descriptions

<a href='#Colourb-new' name='Colourb-new'>new</a>(`integer` red, `integer` green, `integer` blue, `integer` alpha)  &rarr; `Colourb`
: Construct a new `Colourb` object

---

### <a href='#Colourf' name='Colourf'>Colourf</a>

Inherits: `nil`

Constructs a colour with four floating point channels.

#### Properties

| Name | Type |
| ------------ | ---- |
| [alpha](#Colourf-alpha) | `number` |
| [blue](#Colourf-blue) | `number` |
| [green](#Colourf-green) | `number` |
| [red](#Colourf-red) | `number` |
| [rgba](#Colourf-rgba) | `number, number, number, number` |


#### Functions

| Name | Return Type |
| ------------ | ---- |
| [new](#Colourf-new)(`number` red, `number` green, `number` blue, `number` alpha) | `Colourf` |


#### Metafunctions

| Metafunctions |
| ------------- |
| __eq |


#### Property Descriptions

<a href='#Colourf-alpha' name='Colourf-alpha'>alpha</a>  :: `number`
: Alpha channel

<a href='#Colourf-blue' name='Colourf-blue'>blue</a>  :: `number`
: Blue channel

<a href='#Colourf-green' name='Colourf-green'>green</a>  :: `number`
: Green channel

<a href='#Colourf-red' name='Colourf-red'>red</a>  :: `number`
: Red channel

<a href='#Colourf-rgba' name='Colourf-rgba'>rgba</a>  :: `number`, `number`, `number`, `number`


#### Function Descriptions

<a href='#Colourf-new' name='Colourf-new'>new</a>(`number` red, `number` green, `number` blue, `number` alpha)  &rarr; `Colourf`
: Construct a new `Colourf` object.

---

### <a href='#Context' name='Context'>Context</a>

Inherits: `nil`

The Context class has no constructor; it must be instantiated through the CreateContext() function. It has the following functions and properties:

#### Properties

| Name | Type |
| ------------ | ---- |
| [dimensions](#Context-dimensions) | `Vector2i` |
| [documents](#Context-documents) | `ContextDocumentsProxy` |
| [dp_ratio](#Context-dp_ratio) | `number` |
| [focus_element](#Context-focus_element) | `Element` |
| [hover_element](#Context-hover_element) | `Element` |
| [name](#Context-name) | `string` |
| [root_element](#Context-root_element) | `Element` |


#### Functions

| Name | Return Type |
| ------------ | ---- |
| [AddEventListener](#Context-AddEventListener)(`string` event, `function, string` script, `Element` element_context, `boolean` in_capture_phase) | `nil` |
| [CreateDocument](#Context-CreateDocument)(`string` tag) | `Document`<br></br> |
| [IsMouseInteracting](#Context-IsMouseInteracting)() | `boolean`<br></br> |
| [LoadDocument](#Context-LoadDocument)(`string` document_path) | `Document`<br></br> |
| [ProcessKeyDown](#Context-ProcessKeyDown)(`integer` key_identifier, `integer` key_modifier_state) | `boolean` <br></br> |
| [ProcessKeyUp](#Context-ProcessKeyUp)(`integer` key_identifier, `integer` key_modifier_state) | `boolean` <br></br> |
| [ProcessMouseButtonDown](#Context-ProcessMouseButtonDown)( `integer` button_index, `integer` key_modifier_state) | `boolean` <br></br> |
| [ProcessMouseButtonUp](#Context-ProcessMouseButtonUp)( `integer` button_index, `integer` key_modifier_state) | `boolean` <br></br> |
| [ProcessMouseLeave](#Context-ProcessMouseLeave)() | `boolean`<br></br> |
| [ProcessMouseWheel](#Context-ProcessMouseWheel)(`number` delta, `integer` key_modifier_state) | `boolean` <br></br> |
| [ProcessTextInput](#Context-ProcessTextInput)(`string` `integer`  input) | `boolean` <br></br> |
| [Render](#Context-Render)() | `boolean`<br></br> |
| [UnloadAllDocuments](#Context-UnloadAllDocuments)() | `nil` |
| [UnloadDocument](#Context-UnloadDocument)(`Document` document) | `nil` |
| [Update](#Context-Update)() | `boolean`<br></br> |


#### Property Descriptions

<a href='#Context-dimensions' name='Context-dimensions'>dimensions</a>  :: `Vector2i`
: The dimensions of the context, as a Vector2i type.

<a href='#Context-documents' name='Context-documents'>documents</a>  :: `ContextDocumentsProxy`
: Returns an array of the documents within the context. This can be looked up as an array or a dictionary. Read-only.

<a href='#Context-dp_ratio' name='Context-dp_ratio'>dp_ratio</a>  :: `number`
: The density independent pixel ratio of the context. This value determines ratio between 'dp' and 'px' units.

<a href='#Context-focus_element' name='Context-focus_element'>focus_element</a>  :: `Element`
: Returns the leaf of the context's focus tree. Read-only.

<a href='#Context-hover_element' name='Context-hover_element'>hover_element</a>  :: `Element`
: Returns the element under the context's cursor. Read-only.

<a href='#Context-name' name='Context-name'>name</a>  :: `string`
: The name of the context, specified at construction. Read-only.

<a href='#Context-root_element' name='Context-root_element'>root_element</a>  :: `Element`
: Returns the context's root element. Read-only.



#### Function Descriptions

<a href='#Context-AddEventListener' name='Context-AddEventListener'>AddEventListener</a>(`string` event, `function, string` script, `Element` element_context, `boolean` in_capture_phase)  &rarr; `nil`
: Adds the inline Lua script or a Lua function, `script`, as an event listener to the context. `element_context` is an optional `Element`; if it is not `nil`, then the script will be executed as if it was bound to that element.

<a href='#Context-CreateDocument' name='Context-CreateDocument'>CreateDocument</a>(`string` tag)  &rarr; `Document`
: Creates a new document with the tag name of `tag`.

<a href='#Context-IsMouseInteracting' name='Context-IsMouseInteracting'>IsMouseInteracting</a>() &rarr; `boolean`
: Returns a hint on whether the mouse is currently interacting with any elements in this context.

<a href='#Context-LoadDocument' name='Context-LoadDocument'>LoadDocument</a>(`string` document_path)  &rarr; `Document`
: Attempts to load a document from the HTML file found at `document_path`. If successful, the document will be returned with a reference count of one.

<a href='#Context-ProcessKeyDown' name='Context-ProcessKeyDown'>ProcessKeyDown</a>(`integer` key_identifier, `integer` key_modifier_state) &rarr; `boolean`
: Sends a key down event into this context. `key_identifier` is the key pressed and the `key_modifier_state` is the state of key modifiers at the moment of the event. Returns true if the event was consumed, otherwise false.

<a href='#Context-ProcessKeyUp' name='Context-ProcessKeyUp'>ProcessKeyUp</a>(`integer` key_identifier, `integer` key_modifier_state) &rarr; `boolean`
: Sends a key release event into this context. `key_identifier` is the key released and the `key_modifier_state` is the state of key modifiers at the moment of the event. Returns true if the event was consumed, otherwise false.

<a href='#Context-ProcessMouseButtonDown' name='Context-ProcessMouseButtonDown'>ProcessMouseButtonDown</a>(`integer` button_index, `integer` key_modifier_state) &rarr; `boolean`
: Sends a mouse-button down event into this context. `button_index` is the the index of the button that was pressed (0 for the left button, 1 for right, and any others from 2 onwards), and the `key_modifier_state` is the state of key modifiers at the moment of the event. Returns true if the mouse is not interacting with any elements in the context, otherwise false.

<a href='#Context-ProcessMouseButtonUp' name='Context-ProcessMouseButtonUp'>ProcessMouseButtonUp</a>(`integer` button_index, `integer` key_modifier_state) &rarr; `boolean`
: Sends a mouse-button up event into this context. `button_index` is the the index of the button that was released (0 for the left button, 1 for right, and any others from 2 onwards), and the `key_modifier_state` is the state of key modifiers at the moment of the event. Returns true if the mouse is not interacting with any elements in the context, otherwise false.

<a href='#Context-ProcessMouseLeave' name='Context-ProcessMouseLeave'>ProcessMouseLeave</a>()  &rarr; `boolean`
: Tells the context that the mouse has left the window. Returns true if the mouse is not interacting with any elements in the context, otherwise false.

<a href='#Context-ProcessMouseWheel' name='Context-ProcessMouseWheel'>ProcessMouseWheel</a>(`number` delta, `integer` key_modifier_state) &rarr; `boolean`
: Sends a mouse-wheel movement event into this context. `wheel_delta` is the mouse-wheel movement this frame, and the `key_modifier_state` is the state of key modifiers at the moment of the event. Returns true if the event was not consumed (ie, was prevented from propagating by an element), false if it was.

<a href='#Context-ProcessTextInput' name='Context-ProcessTextInput'>ProcessTextInput</a>(`string` `integer`  input) &rarr; `boolean`
: Sends a text input event into the context. If the `input` type is `integer`, sends a single key event, if the `input` is `string`, sends this string as a text input event. Return true if the event was not consumed (ie, was prevented from propagating by an element), false if it was.

<a href='#Context-Render' name='Context-Render'>Render</a>()  &rarr; `boolean`
: Renders the context.

<a href='#Context-UnloadAllDocuments' name='Context-UnloadAllDocuments'>UnloadAllDocuments</a>()  &rarr; `nil`
: Closes all documents currently loaded with the context.

<a href='#Context-UnloadDocument' name='Context-UnloadDocument'>UnloadDocument</a>(`Document` document)  &rarr; `nil`
: Unloads a specific document within the context.

<a href='#Context-Update' name='Context-Update'>Update</a>()  &rarr; `boolean`
: Updates the context.



---

### <a href='#ContextDocumentsProxy' name='ContextDocumentsProxy'>ContextDocumentsProxy</a>

Inherits: `nil`

Table of documents with the ability to be iterated over or indexed by an integer or a string.

#### Metafunctions

| Metafunctions |
| ------------- |
| __index |
| __pairs |


---

### <a href='#DataFormatter' name='DataFormatter'>DataFormatter</a>

Inherits: `nil`

Lua data formatting helper.

#### Properties

| Name | Type |
| ------------ | ---- |
| [FormatData](#DataFormatter-FormatData) | `function` |

#### Functions

| Name | Return Type |
| ------------ | ---- |
| [new](#DataFormatter-new)(`nil, function` format_data) | `DataFormatter` |

#### Property Descriptions

<a href='#DataFormatter-FormatData' name='DataFormatter-FormatData'>FormatData</a>  :: `function`
: Formatting function which returns a `string`

#### Function Descriptions

<a href='#DataFormatter-new' name='DataFormatter-new'>new</a>(`nil, function` format_data)  &rarr; `DataFormatter`
: Construct a new `DataFormatter` object. Optional `format_data` argument which is a function which returns a `string`.

---

### <a href='#DataSource' name='DataSource'>DataSource</a>

Inherits: `nil`

Abstract DataSource Interface.

#### Functions

| Name | Return Type |
| ------------ | ---- |
| [new](#DataSource-new)(`string` name) | `DataSource`<br></br> |
| [GetNumRows](#DataSource-GetNumRows)(`DataSource` table_name) | `integer`<br></br> |
| [GetRow](#DataSource-GetRow)(`DataSource` table_name, `lua_type` index) | `string`<br></br> |
| [NotifyRowAdd](#DataSource-NotifyRowAdd)(`string` table_name, `integer` first_row_added, `integer` num_rows_added) | `nil` |
| [NotifyRowChange](#DataSource-NotifyRowChange)(`string` table_name, `nil, integer` first_row_changed, `nil, integer` num_rows_changed) | `nil` |
| [NotifyRowRemove](#DataSource-NotifyRowRemove)(`string` table_name, `integer` first_row_removed, `integer` num_rows_removed) | `nil` |


#### Function Descriptions

<a href='#DataSource-new' name='DataSource-new'>new</a>(`string` name)  &rarr; `DataSource`
: Construct a new `DataSource` object.

<a href='#DataSource-GetNumRows' name='DataSource-GetNumRows'>GetNumRows</a>(`DataSource` table_name)  &rarr; `integer`
: Return the number of rows in the given table

<a href='#DataSource-GetRow' name='DataSource-GetRow'>GetRow</a>(`DataSource` table_name, `lua_type` index)  &rarr; `string`
: Return a list of the column values in string form

<a href='#DataSource-NotifyRowAdd' name='DataSource-NotifyRowAdd'>NotifyRowAdd</a>(`string` table_name, `integer` first_row_added, `integer` num_rows_added)  &rarr; `nil`
: Notify listeners that rows have been added to the data source.

<a href='#DataSource-NotifyRowChange' name='DataSource-NotifyRowChange'>NotifyRowChange</a>(`string` table_name, `nil, integer` first_row_changed, `nil, integer` num_rows_changed)  &rarr; `nil`
: Notify listeners that all rows on the data source have changed. Optional arguments `first_row_changed` for specifying the first row number which changed and `num_rows_changed` for specifying how many rows changed after the first row.

<a href='#DataSource-NotifyRowRemove' name='DataSource-NotifyRowRemove'>NotifyRowRemove</a>(`string` table_name, `integer` first_row_removed, `integer` num_rows_removed)  &rarr; `nil`
: Notify listeners that rows have been removed from the data source.

---

### <a href='#DocumentFocus' name='DocumentFocus'>DocumentFocus</a>

Inherits: `nil`

Enum type used as an argument to various functions requiring focus options.

#### Properties

| Name | Type |
| ------------ | ---- |
| [None](#DocumentFocus-None) | `integer` |
| [Document](#DocumentFocus-Document) | `integer` |
| [Keep](#DocumentFocus-Keep) | `integer` |
| [Auto](#DocumentFocus-Auto) | `integer` |

#### Property Descriptions

<a href='#DocumentFocus-None' name='DocumentFocus-None'>None</a>  :: `integer`
: No focus.

<a href='#DocumentFocus-Document' name='DocumentFocus-Document'>Document</a>  :: `integer`
: Document focus.

<a href='#DocumentFocus-Keep' name='DocumentFocus-Keep'>Keep</a>  :: `integer`
: Keep focus.

<a href='#DocumentFocus-Auto' name='DocumentFocus-Auto'>Auto</a>  :: `integer`
: Auto focus.

---

### <a href='#DocumentModal' name='DocumentModal'>DocumentModal</a>

Inherits: `nil`

Enum type used as an argument to various functions requiring modal options.

#### Properties

| Name | Type |
| ------------ | ---- |
| [None](#DocumentModal-None) | `integer` |
| [Modal](#DocumentModal-Modal) | `integer` |
| [Keep](#DocumentModal-Keep) | `integer` |

#### Property Descriptions

<a href='#DocumentModal-None' name='DocumentModal-None'>None</a>  :: `integer`
: No modal.

<a href='#DocumentModal-Modal' name='DocumentModal-Modal'>Modal</a>  :: `integer`
: Modal.

<a href='#DocumentModal-Keep' name='DocumentModal-Keep'>Keep</a>  :: `integer`
: Keep modal.

---

### <a href='#Document' name='Document'>Document</a>

Inherits: `Element`

Document derives from Element. Document has no constructor; it must be instantiated through a Context object instead, either by loading an external HTML file or creating an empty document. It has the following functions and properties:

#### Properties

| Name | Type |
| ------------ | ---- |
| [context](#Document-context) | `Context` |
| [title](#Document-title) | `string` |


#### Functions

| Name | Return Type |
| ------------ | ---- |
| [Close](#Document-Close)() | `nil` |
| [CreateElement](#Document-CreateElement)(`string` tag_name) | `ElementPtr`<br></br> |
| [CreateTextNode](#Document-CreateTextNode)(`string` text) | `ElementPtr`<br></br> |
| [Hide](#Document-Hide)() | `nil` |
| [PullToFront](#Document-PullToFront)() | `nil` |
| [PushToBack](#Document-PushToBack)() | `nil` |
| [Show](#Document-Show)(`nil, DocumentModal` modal, `nil, DocumentFocus` focus) | `nil` |


#### Property Descriptions

<a href='#Document-context' name='Document-context'>context</a>  :: `Context`
: The context the document belongs to. Read-only.

<a href='#Document-title' name='Document-title'>title</a>  :: `string`
: The title of the document, as initially set by the \<title\> tag in the document's header.



#### Function Descriptions

<a href='#Document-Close' name='Document-Close'>Close</a>()  &rarr; `nil`
: Hides and closes the document, destroying its contents.

<a href='#Document-CreateElement' name='Document-CreateElement'>CreateElement</a>(`string` tag_name)  &rarr; `ElementPtr`
: Instances an element with a tag of tag_name.

<a href='#Document-CreateTextNode' name='Document-CreateTextNode'>CreateTextNode</a>(`string` text)  &rarr; `ElementPtr`
: Instances a text element containing the string text.

<a href='#Document-Hide' name='Document-Hide'>Hide</a>()  &rarr; `nil`
: Hides the document.

<a href='#Document-PullToFront' name='Document-PullToFront'>PullToFront</a>()  &rarr; `nil`
: Pulls the document in front of other documents within its context with a similar z-index.

<a href='#Document-PushToBack' name='Document-PushToBack'>PushToBack</a>()  &rarr; `nil`
: Pushes the document behind other documents within its context with a similar z-index.

<a href='#Document-Show' name='Document-Show'>Show</a>(`nil, DocumentModal` modal, `nil, DocumentFocus` focus)  &rarr; `nil`
: Shows the document. Optional enum arguments to specify modal and focus mode. Defaults to `DocumentModal.None` and `DocumentFocus.Auto`.



---

### <a href='#Element' name='Element'>Element</a>

Inherits: `nil`

The Element class has no constructor; it must be instantiated through a [Document](#document) object instead. It has the following functions and properties:

#### Properties

| Name | Type |
| ------------ | ---- |
| [attributes](#Element-attributes) | `ElementAttributesProxy` |
| [child_nodes](#Element-child_nodes) | `ElementChildNodesProxy` |
| [class_name](#Element-class_name) | `string` |
| [client_height](#Element-client_height) | `number` |
| [client_left](#Element-client_left) | `number` |
| [client_top](#Element-client_top) | `number` |
| [client_width](#Element-client_width) | `number` |
| [first_child](#Element-first_child) | `nil, Element` |
| [id](#Element-id) | `string` |
| [inner_rml](#Element-inner_rml) | `string` |
| [last_child](#Element-last_child) | `nil, Element` |
| [next_sibling](#Element-next_sibling) | `nil, Element` |
| [offset_height](#Element-offset_height) | `number` |
| [offset_left](#Element-offset_left) | `number` |
| [offset_parent](#Element-offset_parent) | `Element` |
| [offset_top](#Element-offset_top) | `number` |
| [offset_width](#Element-offset_width) | `number` |
| [owner_document](#Element-owner_document) | `Document` |
| [parent_node](#Element-parent_node) | `nil, Element` |
| [previous_sibling](#Element-previous_sibling) | `nil, Element` |
| [scroll_height](#Element-scroll_height) | `number` |
| [scroll_left](#Element-scroll_left) | `number` |
| [scroll_top](#Element-scroll_top) | `number` |
| [scroll_width](#Element-scroll_width) | `number` |
| [style](#Element-style) | `ElementStyleProxy` |
| [tag_name](#Element-tag_name) | `string` |


#### Functions

| Name | Return Type |
| ------------ | ---- |
| [AddEventListener](#Element-AddEventListener)(`string` event, `function, string` listener, `boolean` in_capture_phase) | `nil` |
| [AppendChild](#Element-AppendChild)(`ElementPtr` element) | `nil, Element` |
| [Blur](#Element-Blur)() | `nil` |
| [Click](#Element-Click)() | `nil` |
| [DispatchEvent](#Element-DispatchEvent)(`string` event, `table` parameters) | `nil`<br></br> |
| [new](#Element-new)(`string` tag) | `Element` |
| [Focus](#Element-Focus)() | `nil` |
| [GetAttribute](#Element-GetAttribute)(`string` name) | `Variant`<br></br> |
| [GetElementById](#Element-GetElementById)(`string` id) | `Element`<br></br> |
| [GetElementsByTagName](#Element-GetElementsByTagName)(`string` tag_name) | `table`<br></br> |
| [HasAttribute](#Element-HasAttribute)(`string` name) | `boolean`<br></br> |
| [HasChildNodes](#Element-HasChildNodes)() | `boolean`<br></br> |
| [InsertBefore](#Element-InsertBefore)(`ElementPtr` element, `Element` adjacent_element) | `nil, Element` |
| [IsClassSet](#Element-IsClassSet)(`string` name) | `boolean`<br></br> |
| [QuerySelector](#Element-QuerySelector)(`string` selectors) | `Element`<br></br> |
| [QuerySelectorAll](#Element-QuerySelectorAll)(`string` selectors) | `table`<br></br> |
| [Matches](#Element-Matches)(`string` selectors) | `boolean`<br></br> |
| [RemoveAttribute](#Element-RemoveAttribute)(`string` name) | `nil` |
| [RemoveChild](#Element-RemoveChild)(`Element` element) | `boolean`<br></br> |
| [ReplaceChild](#Element-ReplaceChild)(`ElementPtr` inserted_element, `Element` replaced_element) | `boolean`<br></br> |
| [ScrollIntoView](#Element-ScrollIntoView)(`boolean` align_with_top) | `nil` |
| [SetAttribute](#Element-SetAttribute)(`string` name, `string` value) | `nil` |
| [SetClass](#Element-SetClass)(`string` name, `boolean` value) | `nil` |


#### Property Descriptions

<a href='#Element-attributes' name='Element-attributes'>attributes</a>  :: `ElementAttributesProxy`
: The array of attributes on the element. Each element has the read-only properties name and value. Read-only.

<a href='#Element-child_nodes' name='Element-child_nodes'>child_nodes</a>  :: `ElementChildNodesProxy`
: The array of child nodes on the element. Read-only.

<a href='#Element-class_name' name='Element-class_name'>class_name</a>  :: `string`
: The space-separated list of classes on the element.

<a href='#Element-client_height' name='Element-client_height'>client_height</a>  :: `number`
: The height of the element's client area. Read-only.

<a href='#Element-client_left' name='Element-client_left'>client_left</a>  :: `number`
: The distance between the left border edge and the left client edge of the element. Read-only.

<a href='#Element-client_top' name='Element-client_top'>client_top</a>  :: `number`
: The distance between the top border edge and the top client edge of the element. Read-only.

<a href='#Element-client_width' name='Element-client_width'>client_width</a>  :: `number`
: The width of the element's client area. Read-only.

<a href='#Element-first_child' name='Element-first_child'>first_child</a>  :: `nil`, `Element`
: The first child of the element, or `nil` if the client has no children. Read-only.

<a href='#Element-id' name='Element-id'>id</a>  :: `string`
: The ID of the element, or the empty string if the element has no ID.

<a href='#Element-inner_rml' name='Element-inner_rml'>inner_rml</a>  :: `string`
: The element's HTML content.

<a href='#Element-last_child' name='Element-last_child'>last_child</a>  :: `nil`, `Element`
: The last child of the element, or `nil` if the client has no children. Read-only.

<a href='#Element-next_sibling' name='Element-next_sibling'>next_sibling</a>  :: `nil`, `Element`
: The element's next sibling, or `nil` if it is the last sibling. Read-only.

<a href='#Element-offset_height' name='Element-offset_height'>offset_height</a>  :: `number`
: The height of the element, excluding margins. Read-only.

<a href='#Element-offset_left' name='Element-offset_left'>offset_left</a>  :: `number`
: The distance between the element's offset parent's left border edge and this element's left border edge. Read-only.

<a href='#Element-offset_parent' name='Element-offset_parent'>offset_parent</a>  :: `Element`
: The element's offset parent. Read only.

<a href='#Element-offset_top' name='Element-offset_top'>offset_top</a>  :: `number`
: The distance between the element's offset parent's top border edge and this element's top border edge. Read-only.

<a href='#Element-offset_width' name='Element-offset_width'>offset_width</a>  :: `number`
: The width of the element, excluding margins. Read-only.

<a href='#Element-owner_document' name='Element-owner_document'>owner_document</a>  :: `Document`
: The document this element is part of. Read-only.

<a href='#Element-parent_node' name='Element-parent_node'>parent_node</a>  :: `nil`, `Element`
: The element this element is directly parented to. Read-only.

<a href='#Element-previous_sibling' name='Element-previous_sibling'>previous_sibling</a>  :: `nil`, `Element`
: The element's previous sibling, or None if it is the first sibling. Read-only.

<a href='#Element-scroll_height' name='Element-scroll_height'>scroll_height</a>  :: `number`
: The height of this element's content. This will be at least as high as the client height. Read-only.

<a href='#Element-scroll_left' name='Element-scroll_left'>scroll_left</a>  :: `number`
: The offset between the left edge of this element's client area and the left edge of the content area.

<a href='#Element-scroll_top' name='Element-scroll_top'>scroll_top</a>  :: `number`
: The offset between the top edge of this element's client area and the top edge of the content area.

<a href='#Element-scroll_width' name='Element-scroll_width'>scroll_width</a>  :: `number`
: The width of this element's content. This will be at least as wide as the client width. Read-only.

<a href='#Element-style' name='Element-style'>style</a>  :: `ElementStyleProxy`
: An object used to access this element's style information. Individual CSS properties can be accessed by using the name of the property as a Lua property on the object itself (ie, element.style.width = "40px").

<a href='#Element-tag_name' name='Element-tag_name'>tag_name</a>  :: `string`
: The tag name used to instance this element. Read-only.



#### Function Descriptions

<a href='#Element-AddEventListener' name='Element-AddEventListener'>AddEventListener</a>(`string` event, `function, string` listener, `boolean` in_capture_phase)  &rarr; `nil`
: NOTE: Events added from Lua cannot be removed.

<a href='#Element-AppendChild' name='Element-AppendChild'>AppendChild</a>(`ElementPtr` element)  &rarr; `nil, Element`
: Appends element as a child to this element.

<a href='#Element-Blur' name='Element-Blur'>Blur</a>()  &rarr; `nil`
: Removes input focus from this element.

<a href='#Element-Click' name='Element-Click'>Click</a>()  &rarr; `nil`
: Fakes a click on this element.

<a href='#Element-DispatchEvent' name='Element-DispatchEvent'>DispatchEvent</a>(`string` event, `table` parameters)  &rarr; `nil`
: Dispatches an event to this element. The event is a string value of the event type, *without* the 'on' prefix. Parameters to the event are given in the dictionary parameters; the dictionary must only contain string keys, and numeric, string or boolean values.

<a href='#Element-new' name='Element-new'>new</a>(`string` tag)  &rarr; `Element`
: Construct new `Element` object.

<a href='#Element-Focus' name='Element-Focus'>Focus</a>()  &rarr; `nil`
: Gives input focus to this element.

<a href='#Element-GetAttribute' name='Element-GetAttribute'>GetAttribute</a>(`string` name)  &rarr; `Variant`
: Returns the value of the attribute named name. If no such attribute exists, the empty string will be returned.

<a href='#Element-GetElementById' name='Element-GetElementById'>GetElementById</a>(`string` id)  &rarr; `Element`
: Returns the descendant element with an id of id.

<a href='#Element-GetElementsByTagName' name='Element-GetElementsByTagName'>GetElementsByTagName</a>(`string` tag_name)  &rarr; `table`
: Returns a list of all descendant elements with the tag of `tag_name`. Returned table is indexable with integers.

<a href='#Element-HasAttribute' name='Element-HasAttribute'>HasAttribute</a>(`string` name)  &rarr; `boolean`
: Returns true if the element has a value for the attribute named name, false if not.

<a href='#Element-HasChildNodes' name='Element-HasChildNodes'>HasChildNodes</a>()  &rarr; `boolean`
: Returns true if the element has at least one child node, false if not.

<a href='#Element-InsertBefore' name='Element-InsertBefore'>InsertBefore</a>(`ElementPtr` element, `Element` adjacent_element)  &rarr; `nil, Element`
: Inserts the element element as a child of this element, directly before adjacent_element in the list of children.

<a href='#Element-IsClassSet' name='Element-IsClassSet'>IsClassSet</a>(`string` name)  &rarr; `boolean`
: Returns true if the class name is set on the element, false if not.

<a href='#Element-QuerySelector' name='Element-QuerySelector'>QuerySelector</a>(`string` selectors)  &rarr; `Element`
: Returns the first descendant element matching the provided CSS selector(s).

<a href='#Element-QuerySelectorAll' name='Element-QuerySelectorAll'>QuerySelectorAll</a>(`string` selectors)  &rarr; `table`
: Returns a set of all descendant elements matching the provided CSS selector(s). Returned table is indexable with integers.

<a href='#Element-Matches' name='Element-Matches'>Matches</a>(`string` selectors)  &rarr; `boolean`
: Returns true if the element matches the provided CSS selector(s), false if not.

<a href='#Element-RemoveAttribute' name='Element-RemoveAttribute'>RemoveAttribute</a>(`string` name)  &rarr; `nil`
: Removes the attribute named name from the element.

<a href='#Element-RemoveChild' name='Element-RemoveChild'>RemoveChild</a>(`Element` element)  &rarr; `boolean`
: Removes the child element element from this element.

<a href='#Element-ReplaceChild' name='Element-ReplaceChild'>ReplaceChild</a>(`ElementPtr` inserted_element, `Element` replaced_element)  &rarr; `boolean`
: Replaces the child element replaced_element with `inserted_element` in this element's list of children. If replaced_element is not a child of this element, `inserted_element` will be appended onto the list instead.

<a href='#Element-ScrollIntoView' name='Element-ScrollIntoView'>ScrollIntoView</a>(`boolean` align_with_top)  &rarr; `nil`
: Scrolls this element into view if its ancestors have hidden overflow. If `align_with_top` is true, the element's top edge will be aligned with the top (or as close as possible to the top) of its ancestors' viewing windows. If false, its bottom edge will be aligned to the bottom.

<a href='#Element-SetAttribute' name='Element-SetAttribute'>SetAttribute</a>(`string` name, `string` value)  &rarr; `nil`
: Sets the value of the attribute named name to value.

<a href='#Element-SetClass' name='Element-SetClass'>SetClass</a>(`string` name, `boolean` value)  &rarr; `nil`
: Sets (if value is true) or clears (if value is false) the class name on the element.



---

### <a href='#ElementAttributesProxy' name='ElementAttributesProxy'>ElementAttributesProxy</a>

Inherits: `nil`



#### Metafunctions

| Metafunctions |
| ------------- |
| __index |
| __pairs |


---

### <a href='#ElementChildNodesProxy' name='ElementChildNodesProxy'>ElementChildNodesProxy</a>

Inherits: `nil`



#### Metafunctions

| Metafunctions |
| ------------- |
| __index |
| __pairs |
| __len   |


---

### <a href='#ElementDataGrid' name='ElementDataGrid'>ElementDataGrid</a>

Inherits: `Element`

ElementDataGrid derives from Element. The data grid has the following functions and properties:

#### Properties

| Name | Type |
| ------------ | ---- |
| [rows](#ElementDataGrid-rows) | `table` |


#### Functions

| Name | Return Type |
| ------------ | ---- |
| [AddColumn](#ElementDataGrid-AddColumn)(`string` fields, `string` formatter, `number` initial_width, `string` header_rml) | `nil` |
| [SetDataSource](#ElementDataGrid-SetDataSource)(`string` data_source_name) | `nil` |


#### Property Descriptions

<a href='#ElementDataGrid-rows' name='ElementDataGrid-rows'>rows</a>  :: `table`
: Returns an array containing all the rows in the data grid.



#### Function Descriptions

<a href='#ElementDataGrid-AddColumn' name='ElementDataGrid-AddColumn'>AddColumn</a>(`string` fields, `string` formatter, `number` initial_width, `string` header_rml)  &rarr; `nil`
: Adds a new column to the data grid. The column will read the columns fields (in CSV format) from the grid's data source, processing it through the data formatter named formatter. `header_rml` specifies the HTML content of the column's header.

<a href='#ElementDataGrid-SetDataSource' name='ElementDataGrid-SetDataSource'>SetDataSource</a>(`string` data_source_name)  &rarr; `nil`
: Sets the name and table of the new data source to be used by the data grid.



---

### <a href='#ElementDataGridRow' name='ElementDataGridRow'>ElementDataGridRow</a>

Inherits: `Element`

ElementDataGridRow derives from Element. The data grid row has the following properties:

#### Properties

| Name | Type |
| ------------ | ---- |
| [parent_grid](#ElementDataGridRow-parent_grid) | `ElementDataGrid` |
| [parent_relative_index](#ElementDataGridRow-parent_relative_index) | `integer` |
| [parent_row](#ElementDataGridRow-parent_row) | `ElementDataGridRow` |
| [row_expanded](#ElementDataGridRow-row_expanded) | `boolean` |
| [table_relative_index](#ElementDataGridRow-table_relative_index) | `integer` |


#### Property Descriptions

<a href='#ElementDataGridRow-parent_grid' name='ElementDataGridRow-parent_grid'>parent_grid</a>  :: `ElementDataGrid`
: The data grid that this row belongs to.

<a href='#ElementDataGridRow-parent_relative_index' name='ElementDataGridRow-parent_relative_index'>parent_relative_index</a>  :: `integer`
: The index of the row, relative to its parent row. So if you are the third row in your parent, then it will be 3.

<a href='#ElementDataGridRow-parent_row' name='ElementDataGridRow-parent_row'>parent_row</a>  :: `ElementDataGridRow`
: The parent row of this row. None if it at the top level.

<a href='#ElementDataGridRow-row_expanded' name='ElementDataGridRow-row_expanded'>row_expanded</a>  :: `boolean`
: The expanded state of the row, either true or false.

<a href='#ElementDataGridRow-table_relative_index' name='ElementDataGridRow-table_relative_index'>table_relative_index</a>  :: `integer`
: The index of the row, relative to the data grid it is in. This takes into account all previous rows and their children.



---

### <a href='#ElementForm' name='ElementForm'>ElementForm</a>

Inherits: `Element`

ElementForm derives from Element. The form element has the following function:

#### Functions

| Name | Return Type |
| ------------ | ---- |
| [Submit](#ElementForm-Submit)(`nil, string` name, `nil, string` submit_value) | `nil` |


#### Function Descriptions

<a href='#ElementForm-Submit' name='ElementForm-Submit'>Submit</a>(`nil, string` name, `nil, string` submit_value)  &rarr; `nil`
: Submits the form with name of `name` and a submit value of `submit_value`. `name` and `value` are optional and are empty by default.



---

### <a href='#ElementFormControl' name='ElementFormControl'>ElementFormControl</a>

Inherits: `Element`



#### Properties

| Name | Type |
| ------------ | ---- |
| [disabled](#ElementFormControl-disabled) | `boolean` |
| [name](#ElementFormControl-name) | `string` |
| [value](#ElementFormControl-value) | `string` |


#### Property Descriptions

<a href='#ElementFormControl-disabled' name='ElementFormControl-disabled'>disabled</a>  :: `boolean`


<a href='#ElementFormControl-name' name='ElementFormControl-name'>name</a>  :: `string`


<a href='#ElementFormControl-value' name='ElementFormControl-value'>value</a>  :: `string`


---

### <a href='#ElementFormControlDataSelect' name='ElementFormControlDataSelect'>ElementFormControlDataSelect</a>

Inherits: `ElementFormControlSelect`

ElementFormControlDataSelect derives from ElementFormControlSelect. It has the following additional function:

#### Functions

| Name | Return Type |
| ------------ | ---- |
| [SetDataSource](#ElementFormControlDataSelect-SetDataSource)(`string` data_source_name) | `nil` |


#### Function Descriptions

<a href='#ElementFormControlDataSelect-SetDataSource' name='ElementFormControlDataSelect-SetDataSource'>SetDataSource</a>(`string` data_source_name)  &rarr; `nil`
: Sets the name and table of the new data source to be used by the select box.



---

### <a href='#ElementFormControlInput' name='ElementFormControlInput'>ElementFormControlInput</a>

Inherits: `ElementFormControl`

ElementFormControlInput derives from IElementFormControl. The control has the following properties, only appropriate on the relevant types:

#### Properties

| Name | Type |
| ------------ | ---- |
| [checked](#ElementFormControlInput-checked) | `boolean` |
| [max](#ElementFormControlInput-max) | `integer` |
| [maxlength](#ElementFormControlInput-maxlength) | `integer` |
| [min](#ElementFormControlInput-min) | `integer` |
| [size](#ElementFormControlInput-size) | `integer` |
| [step](#ElementFormControlInput-step) | `integer` |


#### Functions

| Name | Return Type |
| ------------ | ---- |
| [GetSelection](#ElementFormControlInput-GetSelection)() | `integer, integer, string` |
| [Select](#ElementFormControlInput-Select)() | `nil` |
| [SetSelection](#ElementFormControlInput-SetSelection)(`integer` selection_start, `integer` selection_end) | `nil` |


#### Property Descriptions

<a href='#ElementFormControlInput-checked' name='ElementFormControlInput-checked'>checked</a>  :: `boolean`
: Relevant for radio and checkbox types. The checked status of the input.

<a href='#ElementFormControlInput-max' name='ElementFormControlInput-max'>max</a>  :: `integer`
: Relevant for range types. The value of the control on the bottom / right of the slider.

<a href='#ElementFormControlInput-maxlength' name='ElementFormControlInput-maxlength'>maxlength</a>  :: `integer`


<a href='#ElementFormControlInput-min' name='ElementFormControlInput-min'>min</a>  :: `integer`
: Relevant for range types. The value of the control on the top / left of the slider.

<a href='#ElementFormControlInput-size' name='ElementFormControlInput-size'>size</a>  :: `integer`
: Relevant for text types. The approximate number of characters the text field shows horizontally at once.

<a href='#ElementFormControlInput-step' name='ElementFormControlInput-step'>step</a>  :: `integer`
: Relevant for range types. The step the control's value changes in.


#### Function Descriptions

<a href='#ElementFormControlInput-GetSelection' name='ElementFormControlInput-GetSelection'>GetSelection</a>()  &rarr; `integer, integer, string`
: Retrieves the selection range and text. If no text is selected, both offsets are equal to 1.

<a href='#ElementFormControlInput-Select' name='ElementFormControlInput-Select'>Select</a>()  &rarr; `nil`
: Selects all text.

<a href='#ElementFormControlInput-SetSelection' name='ElementFormControlInput-SetSelection'>SetSelection</a>(`integer` selection_start, `integer` selection_end)  &rarr; `nil`
: Selects the text in the given character range.


---

### <a href='#ElementFormControlSelect' name='ElementFormControlSelect'>ElementFormControlSelect</a>

Inherits: `ElementFormControl`

ElementFormControlSelect derives from IElementFormControl. The control has the following functions and properties:

#### Properties

| Name | Type |
| ------------ | ---- |
| [options](#ElementFormControlSelect-options) | `SelectOptionsProxy` |
| [selection](#ElementFormControlSelect-selection) | `integer` |


#### Functions

| Name | Return Type |
| ------------ | ---- |
| [Add](#ElementFormControlSelect-Add)(`string` rml, `string` value, `nil, integer` before) | `integer`<br></br> |
| [Remove](#ElementFormControlSelect-Remove)(`integer` index) | `nil` |
| [RemoveAll](#ElementFormControlSelect-RemoveAll)() | `nil` |


#### Property Descriptions

<a href='#ElementFormControlSelect-options' name='ElementFormControlSelect-options'>options</a>  :: `SelectOptionsProxy`
: The array of options available in the select box. Each entry in the array has the property value, the string value of the option, and element, the root of the element hierarchy that represents the option in the list.

<a href='#ElementFormControlSelect-selection' name='ElementFormControlSelect-selection'>selection</a>  :: `integer`
: The index of the currently selected option.



#### Function Descriptions

<a href='#ElementFormControlSelect-Add' name='ElementFormControlSelect-Add'>Add</a>(`string` rml, `string` value, `nil, integer` before)  &rarr; `integer`
: Adds a new option to the select box. The new option has the string value of value and is represented by the elements created by the HTML string rml. The new option will be inserted by the index specified by before; if this is out of bounds (the default), then the new option will be appended onto the list. The index of the new option will be returned.

<a href='#ElementFormControlSelect-Remove' name='ElementFormControlSelect-Remove'>Remove</a>(`integer` index)  &rarr; `nil`
: Removes an existing option from the selection box.

<a href='#ElementFormControlSelect-RemoveAll' name='ElementFormControlSelect-RemoveAll'>RemoveAll</a>()  &rarr; `nil`


---

### <a href='#ElementFormControlTextArea' name='ElementFormControlTextArea'>ElementFormControlTextArea</a>

Inherits: `ElementFormControl`

ElementFormControlTextArea derives from IElementFormControl. The control has the following properties:

#### Properties

| Name | Type |
| ------------ | ---- |
| [cols](#ElementFormControlTextArea-cols) | `integer` |
| [maxlength](#ElementFormControlTextArea-maxlength) | `integer` |
| [rows](#ElementFormControlTextArea-rows) | `integer` |
| [wordwrap](#ElementFormControlTextArea-wordwrap) | `boolean` |


#### Functions

| Name | Return Type |
| ------------ | ---- |
| [GetSelection](#ElementFormControlTextArea-GetSelection)() | `integer, integer, string` |
| [Select](#ElementFormControlTextArea-Select)() | `nil` |
| [SetSelection](#ElementFormControlTextArea-SetSelection)(`integer` selection_start, `integer` selection_end) | `nil` |


#### Property Descriptions

<a href='#ElementFormControlTextArea-cols' name='ElementFormControlTextArea-cols'>cols</a>  :: `integer`
: The approximate number of characters the text area shows horizontally at once.

<a href='#ElementFormControlTextArea-maxlength' name='ElementFormControlTextArea-maxlength'>maxlength</a>  :: `integer`


<a href='#ElementFormControlTextArea-rows' name='ElementFormControlTextArea-rows'>rows</a>  :: `integer`
: The number of lines the text area shows at once.

<a href='#ElementFormControlTextArea-wordwrap' name='ElementFormControlTextArea-wordwrap'>wordwrap</a>  :: `boolean`


#### Function Descriptions

<a href='#ElementFormControlTextArea-GetSelection' name='ElementFormControlTextArea-GetSelection'>GetSelection</a>()  &rarr; `integer, integer, string`
: Retrieves the selection range and text. If no text is selected, both offsets are equal to 1.

<a href='#ElementFormControlTextArea-Select' name='ElementFormControlTextArea-Select'>Select</a>()  &rarr; `nil`
: Selects all text.

<a href='#ElementFormControlTextArea-SetSelection' name='ElementFormControlTextArea-SetSelection'>SetSelection</a>(`integer` selection_start, `integer` selection_end)  &rarr; `nil`
: Selects the text in the given character range.


---

### <a href='#ElementInstancer' name='ElementInstancer'>ElementInstancer</a>

Inherits: `nil`



#### Functions

| Name | Return Type |
| ------------ | ---- |
| [new](#ElementInstancer-new)() | `ElementInstancer` |
| [InstanceElement](#ElementInstancer-InstanceElement)(`ElementInstancer` ) | `value`<br></br> |


#### Function Descriptions

<a href='#ElementInstancer-new' name='ElementInstancer-new'>new</a>()  &rarr; `ElementInstancer`


<a href='#ElementInstancer-InstanceElement' name='ElementInstancer-InstanceElement'>InstanceElement</a>(`ElementInstancer` )  &rarr; `value`


---

### <a href='#ElementPtr' name='ElementPtr'>ElementPtr</a>

Inherits: `nil`

Represents an owned element. This type is mainly used to modify the DOM tree by passing the object into other elements. For example [Element.AppendChild()](#Element-AppendChild).

A current limitation in the Lua plugin is that `Element` member properties and functions cannot be used directly on this type.


---

### <a href='#ElementStyleProxy' name='ElementStyleProxy'>ElementStyleProxy</a>

Inherits: `nil`



#### Metafunctions

| Metafunctions |
| ------------- |
| __index |
| __newindex |
| __pairs |


---

### <a href='#ElementTabSet' name='ElementTabSet'>ElementTabSet</a>

Inherits: `Element`

ElementTabSet derives from Element. The control has the following functions and properties:

#### Properties

| Name | Type |
| ------------ | ---- |
| [active_tab](#ElementTabSet-active_tab) | `integer` |
| [num_tabs](#ElementTabSet-num_tabs) | `integer` |


#### Functions

| Name | Return Type |
| ------------ | ---- |
| [SetPanel](#ElementTabSet-SetPanel)(`integer` index, `string` rml) | `nil` |
| [SetTab](#ElementTabSet-SetTab)(`integer` index, `string` rml) | `nil` |


#### Property Descriptions

<a href='#ElementTabSet-active_tab' name='ElementTabSet-active_tab'>active_tab</a>  :: `integer`
: Index of the active panel.

<a href='#ElementTabSet-num_tabs' name='ElementTabSet-num_tabs'>num_tabs</a>  :: `integer`
: The number of tabs in the tab set. Read-only.



#### Function Descriptions

<a href='#ElementTabSet-SetPanel' name='ElementTabSet-SetPanel'>SetPanel</a>(`integer` index, `string` rml)  &rarr; `nil`
: Sets the contents of a panel to the HTML content rml. If index is out-of-bounds, a new panel will be added at the end.

<a href='#ElementTabSet-SetTab' name='ElementTabSet-SetTab'>SetTab</a>(`integer` index, `string` rml)  &rarr; `nil`
: Sets the contents of a tab to the HTML content rml. If index is out-of-bounds, a new tab will be added at the end.



---

### <a href='#ElementText' name='ElementText'>ElementText</a>

Inherits: `Element`



#### Properties

| Name | Type |
| ------------ | ---- |
| [text](#ElementText-text) | `string` |


#### Property Descriptions

<a href='#ElementText-text' name='ElementText-text'>text</a>  :: `string`


---

### <a href='#Event' name='Event'>Event</a>

Inherits: `nil`

The Event class has no constructor; it is generated internally. It has the following functions and properties:

#### Properties

| Name | Type |
| ------------ | ---- |
| [current_element](#Event-current_element) | `Element` |
| [parameters](#Event-parameters) | `EventParametersProxy` |
| [target_element](#Event-target_element) | `Element` |
| [type](#Event-type) | `string` |


#### Functions

| Name | Return Type |
| ------------ | ---- |
| [StopPropagation](#Event-StopPropagation)() | `nil` |
| [StopImmediatePropagation](#Event-StopImmediatePropagation)() | `nil` |


#### Property Descriptions

<a href='#Event-current_element' name='Event-current_element'>current_element</a>  :: `Element`
: The element the event has propagated to. Read-only.

<a href='#Event-parameters' name='Event-parameters'>parameters</a>  :: `EventParametersProxy`
: A dictionary like object containing all the parameters in the event.

<a href='#Event-target_element' name='Event-target_element'>target_element</a>  :: `Element`
: The element the event was originally targeted at. Read-only.

<a href='#Event-type' name='Event-type'>type</a>  :: `string`
: The string name of the event. Read-only.



#### Function Descriptions

<a href='#Event-StopPropagation' name='Event-StopPropagation'>StopPropagation</a>()  &rarr; `nil`
: Stops the propagation of the event through the event cycle, if allowed.

<a href='#Event-StopImmediatePropagation' name='Event-StopImmediatePropagation'>StopImmediatePropagation</a>()  &rarr; `nil`
: Stops the propagation of the event through the event cycle, including to any other listeners on the current element.



---

### <a href='#EventParametersProxy' name='EventParametersProxy'>EventParametersProxy</a>

Inherits: `nil`



#### Metafunctions

| Metafunctions |
| ------------- |
| __index |
| __pairs |


---

### <a href='#GlobalLuaFunctions' name='GlobalLuaFunctions'>GlobalLuaFunctions</a>

Inherits: `nil`

#### Functions

| Name | Return Type |
| ------------ | ---- |
| [print](#GlobalLuaFunctions-print)(`...` output) | `nil` |

#### Function Descriptions

<a href='#GlobalLuaFunctions-print' name='GlobalLuaFunctions-print'>print</a>(`...` output)  &rarr; `nil`
: Overrides the Lua print method and redirects it to the APUI logging system, which can eg. be accessed through the APUI debugger.

---

### <a href='#Log' name='Log'>Log</a>

Inherits: `nil`

Log messages through APUI.

#### Properties

| Name | Type |
| ------------ | ---- |
| [logtype](#Log-logtype) | `table` |

#### Functions

| Name | Return Type |
| ------------ | ---- |
| [Message](#Log-Message)(`Log.logtype` type, `string` str) | `nil` |


#### Property Descriptions

<a href='#Log-logtype' name='Log-logtype'>logtype</a>  :: `table`
: Enum table for specifying the type of log.

* `Log.logtype.always`
* `Log.logtype.error`
* `Log.logtype.warning`
* `Log.logtype.info`
* `Log.logtype.debug`

#### Function Descriptions

<a href='#Log-Message' name='Log-Message'>Message</a>(`Log.logtype` type, `string` str)  &rarr; `nil`
: Log a message with a type.

---

### <a href='#apui' name='apui'>apui</a>

Inherits: `nil`

`apui` exposes some general APUI functionality globally in Lua. Access with the global table `apui`.

#### Properties

| Name | Type |
| ------------ | ---- |
| [contexts](#LuaAPUI-contexts) | `APUIContextsProxy` |
| [key_identifier](#LuaAPUI-key_identifier) | `table` |
| [key_modifier](#LuaAPUI-key_modifier) | `table` |


#### Functions

| Name | Return Type |
| ------------ | ---- |
| [CreateContext](#LuaAPUI-CreateContext)(`string` name, `Vector2i` dimensions) | `nil`<br></br>`Context`<br></br> |
| [LoadFontFace](#LuaAPUI-LoadFontFace)(`string` path) | `boolean`<br></br> |
| [RegisterTag](#LuaAPUI-RegisterTag)(`string` tag) | `nil` |


#### Property Descriptions

<a href='#LuaAPUI-contexts' name='LuaAPUI-contexts'>contexts</a>  :: `APUIContextsProxy`
: Table of active contexts indexable with integers and context name strings.

<a href='#LuaAPUI-key_identifier' name='LuaAPUI-key_identifier'>key_identifier</a>  :: `table`
: Enum containing all input key identifiers.

<a href='#LuaAPUI-key_modifier' name='LuaAPUI-key_modifier'>key_modifier</a>  :: `table`
: Enum containing all input key modifiers.

#### Function Descriptions

<a href='#LuaAPUI-CreateContext' name='LuaAPUI-CreateContext'>CreateContext</a>(`string` name, `Vector2i` dimensions)  &rarr; `Context`, `Context`
: Create APUI context with specified `dimensions`.

<a href='#LuaAPUI-LoadFontFace' name='LuaAPUI-LoadFontFace'>LoadFontFace</a>(`string` path)  &rarr; `boolean`
: Load font face at `path`

<a href='#LuaAPUI-RegisterTag' name='LuaAPUI-RegisterTag'>RegisterTag</a>(`string` tag)  &rarr; `nil`
: Register tag to element instancer.

---

### <a href='#APUIContextsProxy' name='APUIContextsProxy'>APUIContextsProxy</a>

Inherits: `nil`



#### Metafunctions

| Metafunctions |
| ------------- |
| __index |
| __pairs |


---

### <a href='#SelectOptionsProxy' name='SelectOptionsProxy'>SelectOptionsProxy</a>

Inherits: `nil`



#### Metafunctions

| Metafunctions |
| ------------- |
| __index |
| __pairs |


---

### <a href='#Vector2f' name='Vector2f'>Vector2f</a>

Inherits: `nil`

Constructs a two-dimensional floating-point vector.

#### Properties

| Name | Type |
| ------------ | ---- |
| [magnitude](#Vector2f-magnitude) | `number` |
| [x](#Vector2f-x) | `number` |
| [y](#Vector2f-y) | `number` |


#### Functions

| Name | Return Type |
| ------------ | ---- |
| [DotProduct](#Vector2f-DotProduct)(`Vector2f` other) | `number`<br></br> |
| [Normalise](#Vector2f-Normalise)() | `Vector2f`<br></br> |
| [Rotate](#Vector2f-Rotate)(`number` angle) | `Vector2f`<br></br> |
| [new](#Vector2f-new)(`number` x, `number` y) | `Vector2f` |


#### Metafunctions

| Metafunctions |
| ------------- |
| __add |
| __div |
| __eq |
| __mul |
| __sub |


#### Property Descriptions

<a href='#Vector2f-magnitude' name='Vector2f-magnitude'>magnitude</a>  :: `number`


<a href='#Vector2f-x' name='Vector2f-x'>x</a>  :: `number`


<a href='#Vector2f-y' name='Vector2f-y'>y</a>  :: `number`


#### Function Descriptions

<a href='#Vector2f-DotProduct' name='Vector2f-DotProduct'>DotProduct</a>(`Vector2f` other)  &rarr; `number`


<a href='#Vector2f-Normalise' name='Vector2f-Normalise'>Normalise</a>()  &rarr; `Vector2f`


<a href='#Vector2f-Rotate' name='Vector2f-Rotate'>Rotate</a>(`number` angle)  &rarr; `Vector2f`


<a href='#Vector2f-new' name='Vector2f-new'>new</a>(`number` x, `number` y)  &rarr; `Vector2f`


---

### <a href='#Vector2i' name='Vector2i'>Vector2i</a>

Inherits: `nil`

Constructs a two-dimensional integral vector.

#### Properties

| Name | Type |
| ------------ | ---- |
| [magnitude](#Vector2i-magnitude) | `number` |
| [x](#Vector2i-x) | `integer` |
| [y](#Vector2i-y) | `integer` |


#### Functions

| Name | Return Type |
| ------------ | ---- |
| [new](#Vector2i-new)(`integer` x, `integer` y) | `Vector2i` |


#### Metafunctions

| Metafunctions |
| ------------- |
| __add |
| __div |
| __eq |
| __mul |
| __sub |


#### Property Descriptions

<a href='#Vector2i-magnitude' name='Vector2i-magnitude'>magnitude</a>  :: `number`


<a href='#Vector2i-x' name='Vector2i-x'>x</a>  :: `integer`


<a href='#Vector2i-y' name='Vector2i-y'>y</a>  :: `integer`


#### Function Descriptions

<a href='#Vector2i-new' name='Vector2i-new'>new</a>(`integer` x, `integer` y)  &rarr; `Vector2i`


---
