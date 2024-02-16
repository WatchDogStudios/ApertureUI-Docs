---
layout: page
title: System interface
parent: cpp_manual/interfaces
grandparent: cpp_manual
next: render
---

The system interface is needed for APUI to tell the time, and allows the application to perform common tasks such as logging messages from APUI, translating strings, and setting the mouse cursor. A system interface is necessary, however the only function you need to define is `GetElapsedTime()`.

The system interface is given in `<APUI/Core/SystemInterface.h>`. To develop a custom system interface, create a class derived from `apui::SystemInterface` and provide function definitions for the one pure virtual function and optionally the other virtual functions.

#### Elapsed time (required)

```cpp
// Get the number of seconds elapsed since the start of the application.
virtual double GetElapsedTime() = 0;
```
The `GetElapsedTime()` function should simply return the number of seconds that have elapsed since the start of the application.

#### String translation

```cpp
// Translate the input string into the translated string.
virtual int TranslateString(apui::String& translated, const apui::String& input);
```
`TranslateString()` is called when a text element is constructed from an RML stream. This allows the application to send all text read from file through its string tables. The parameter `input` is the raw text read from the RML, while `translated` should be set to the final text to be given to the text element to render. The total number of changes made to the raw text should be returned. If the number is greater than 0, APUI will recursively call your translate function to process any new text that was added to the stream (watch out for infinite recursion). If your translation function does all the recursion itself, you can safely return 0 on every call.

Note that the translated text can include RML tags and they will be processed as if they were in the original stream; this can be used, for example, to substitute images for certain tokens.

#### Paths

```cpp
// Joins the path of an RML or CSS file with the path of a resource specified within the file.
virtual void JoinPath(String& translated_path, const String& document_path, const String& path);
```
This function can be specialized to modify how paths are joined. This is eg. called from APUI when an CSS file is referenced from an RML file, or when image files are referenced from an CSS file. In most cases the default implementation should be suitable.

#### Logging

```cpp
// Log the specified message.
virtual bool LogMessage(apui::Log::Type type, const apui::String& message);
```
The `LogMessage()` function is called when APUI generates a message. Here, `type` is one of `apui::Log::LT_ERROR` for error messages, `apui::Log::LT_ASSERT` for failed internal assertions (debug library only), `apui::Log::LT_WARNING` for non-fatal warnings, or `apui::Log::LT_INFO` for generic information messages. The `message` parameter is the actual message itself. The function should return true if program execution should continue, or false to generate an interrupt to break execution. This can be useful if you are running inside a debugger to see exactly what an application is doing to trigger a certain message.

#### Mouse cursor

```cpp
// Set the mouse cursor.
virtual void SetMouseCursor(const apui::String& cursor_name);
```
The `SetMouseCursor()` function is called when APUI wants to change the mouse cursor. This behavior is controlled by the [`cursor` property](../../static/css/user_interface.html#cursor), the value of which is directly sent through the interface as the `cursor_name`. The default value for the `cursor` property is an empty string, thus, this can be used to set a default cursor. There are also some [built-in cursor names](../contexts.html#builtin-cursors) that are submitted when the context is in a certain state, such as during autoscrolling.

The user is responsible for setting the system cursor or otherwise rendering the cursor as desired. It is possible to choose for each context whether it should call this function, see [context cursor](../contexts.html#mouse-cursor) for additional details.

#### Clipboard

```cpp
// Set clipboard text.
virtual void SetClipboardText(const String& text);
// Get clipboard text.
virtual void GetClipboardText(String& text);
```
`SetClipboardText()` is called from APUI when it wants to copy the given text to the clipboard. This is typically called when the user presses the copy shortcut keys (Ctrl+C) in a text input field. Likewise, `GetClipboardText()` is called from APUI when it wants to retrieve the text currently stored in the clipboard, typically after the user has pressed the paste key combination (Ctrl+V).

Clients are themselves responsible to interact with the system clipboard if desired, the default library implementation will only copy and paste text internally within the application. All text is considered encoded in UTF-8.


#### Virtual keyboard

```cpp
// Activate keyboard (for touchscreen devices).
virtual void ActivateKeyboard(apui::Vector2f caret_position, float line_height);
// Deactivate keyboard (for touchscreen devices).
virtual void DeactivateKeyboard();
```
These functions are called from APUI when it wants to activate or deactivate a virtual keyboard, such as on phones and tablets. These are typically called when the user focuses on or away from a text input field.

Additionally, `ActivateKeyboard()` is called whenever the caret position of the current text field is changed. The `caret_position` is the absolute position of the carret in window coordinates, while `line_height` is the pixel height of the current line being edited. These arguments can be used to position any input method editor (IME).
