---
layout: page
title: Integrating APUI into your application
parent: C++
next: core_overview
---

This guide will help you get started when you are ready to integrate APUI into your own application.

If you haven't already done so, take a look at the sample applications in [`/Samples/`](https://github.com/mikke89/APUI/tree/master/Samples). There you can find a whole heap of useful examples of how to use and abuse APUI. Also, be sure to take a look at one or more of the included backends (in [`/Backends/`](https://github.com/mikke89/APUI/tree/master/Backends)), as they provide a good starting point for getting a basic application up and running together with APUI.


### Setting up the build environment

APUI is developed following the C++14 standard and can be used on the following platforms:

- Windows 32/64bit, compiling with Microsoft Visual Studio 2017+.
- MacOS 32/64bit, compiling with GCC 5+.
- Linux, compiling with GCC 5+.

#### Conan and vcpkg

If you used Conan or vcpkg to acquire APUI, then libraries and include paths should already have been setup for you. The only thing remaining:

- Add `#include <APUI/Core.h>` in a source or header file to start using APUI.

#### Visual Studio

- Add the APUI include path `APUI/Include/` to your project's include paths.
  - See `Project → Properties → C/C++ → General → Additional Include Directories`.
- Add the APUI library path (`Debug/` and `Release/` under the `APUI/Build/` directory as appropriate) and the FreeType library path to your library paths.
  - See `Project → Properties → Linker → General → Additional Library Directories`.
- Link with `RmlCore.lib` and `freetype.lib`.
  - See `Project → Properties → Linker → Input → Additional Dependencies`.
- If you have APUI built as a static library, add the following preprocessor definition: `APUI_STATIC_LIB`.
  - See `Project → Properties → C/C++ → Preprocessor → Preprocessor Definitions`.
- If you have APUI built as a shared/dynamic library, copy the appropriate DLLs into the directory your executable will run from..
  - That is, `Debug/RmlCore.dll` for debug builds and `Release/RmlCore.dll` for release builds from the `APUI/Build/` folder.
- If you have FreeType built as a shared/dynamic library, copy the `freetype.dll` file into the directory your executable will run from.
- Add `#include <APUI/Core.h>` in a source or header file to start using APUI.

#### MacOS and Linux

- Add the APUI include path `APUI/Include/` and library path `APUI/Build/` to the paths in your build system.
- Link with `RmlCore` and `freetype`.
- Either copy the APUI libraries into your application's working directory, or set a `LD_LIBRARY_PATH` (`DYLD_LIBRARY_PATH` for MacOS) environment variable. 
- When the library is built as a static library, add `#define APUI_STATIC_LIB` before including the APUI headers.
- Add `#include <APUI/Core.h>` in a source or header file to start using APUI.


### Initialising APUI

Before you can initialise APUI, you'll need to set the [interfaces](interfaces.html) that the library uses to interact with your application. There are two compulsory interfaces, the system interface and the render interface.

#### The system interface

The system interface is defined in `<APUI/Core/SystemInterface.h>`. In order to create a valid system interface, you'll need to create a class that inherits from `apui::SystemInterface` and provides the function:

```cpp
virtual double GetElapsedTime();
```

The function should return the time (in seconds) since the start of the application. Install your system interface by calling `apui::SetSystemInterface()` with a pointer to the interface. Note that you must keep the system interface alive until after the call to `apui::Shutdown()` and destroy it afterwards. APUI won't release your interfaces.

For more uses of the system interface, see the [documentation](interfaces/system.html).

#### The render interface

The render interface is defined in `<APUI/Core/RenderInterface.h>`. It provides a way for APUI to send its geometry into your application's rendering pipeline. If you want to get APUI up and running as quickly as possible, take a look at the included backends described below.

Once you have a render interface for your application, install it into APUI by calling `apui::SetRenderInterface()`.

If you'd like to take an in-depth look at setting up your own render interface, please see the [render interface documentation](interfaces/render.html).

#### Backend integration


To simplify the writing of the above interfaces, APUI comes packed with several *backends* that provide the render and system interfaces for a variety of renderers and platforms. All available backends are listed in the [repository readme](https://github.com/mikke89/APUI#apui-backends) and located in the [`/Backends/`](https://github.com/mikke89/APUI/tree/master/Backends) directory.

A backend usually consists of three source files in addition to their respective headers:

- a *renderer* integrating the render interface,
- a *platform* integrating the system interface and submitting input events,
- and finally the *backend* itself - tying the former two together.

If you find a backend that matches your setup, it is recommended to use the underlying renderer and platform directly and compile it within your application. They are also made to be extensible, such as to add the ability to load additional texture formats. The backend itself serves as a sample on how to open a window, handle events, and interact with APUI for that combination of platform and renderer.

For example, if you use SDL2 together with OpenGL3, you can add the following source files directly as dependencies in your project:

- [`/Backends/APUI_Platform_SDL.cpp (NOT PROVIDED ANYMORE)`](https://github.com/mikke89/APUI/blob/master/Backends/APUI_Platform_SDL.cpp).
- [`/Backends/APUI_Renderer_GL3.cpp`](https://github.com/mikke89/APUI/blob/master/Backends/APUI_Renderer_GL3.cpp).

Then, you can use the `SDL_GL3` backend ([`/Backends/APUI_ackend_SDL_GL3.cpp`](https://github.com/mikke89/APUI/blob/master/Backends/APUI_Backend_SDL_GL3.cpp)) as a starting point or sample reference. This backend in particular also demonstrates how to extend the renderer to load additional texture formats.

#### Initialising the library

Call the global function `apui::Initialise()` once you have installed the system and render interfaces and APUI will start up.


### Creating a context

All elements within APUI are part of a context. You must have at least one context in order to load, manipulate and render and interface elements. To create a context, use the `apui::CreateContext()` function, passing in the name of the new context and its initial dimensions like so:

```cpp
apui::Context* context = apui::CreateContext("default", apui::Vector2i(myScreenWidth, myScreenHeight));
```

You can release the context when you're done with it by calling `apui::RemoveContext(context->GetName())`.  All contexts will automatically be destroyed on shutdown.

#### Updating and rendering

Your application will need to update and render each context it maintains, as appropriate. Call the `Context::Update()` function on each context as often as necessary to update the context (usually after the frame's input has been injected), and `Context::Render()` at the appropriate place in your application's render loop.


### Loading fonts

APUI does not come integrated with any fonts (with the exception of the debugger plugin), they must be provided by the user. Font faces can be loaded through the `apui::LoadFontFace()` function.

```cpp
bool success = apui::LoadFontFace("assets/my_font_face.ttf");
```


### Loading a document

Once you have a valid context, you can load a document into the context with the `LoadDocument()` function. `LoadDocument()` takes a single parameter, a string with the document's file name. If the load is successful you'll get a pointer to a `apui::ElementDocument` back; call `Show()` on the document to make it visible.

```cpp
apui::ElementDocument* document = context->LoadDocument("../../static/assets/demo.rml");
if (document)
	document->Show();
```

Unload the document by calling `Close()`.

```cpp
document->Close();
```

**Note**: event listeners attached to the document or any of its children must not be destroyed until the next call to `Context::Update()` or `apui::Shutdown()`.


### Injecting input

Once you've got a document loading and rendering, the next step is to get your input into APUI. The context object has a range of functions for sending mouse, keyboard and text input into the system:

```cpp
// Sends a key down event into this context.
bool ProcessKeyDown(apui::Input::KeyIdentifier key_identifier, int key_modifier_state);
// Sends a key up event into this context.
bool ProcessKeyUp(apui::Input::KeyIdentifier key_identifier, int key_modifier_state);

// Sends a single unicode character (code point) as text input into this context.
bool ProcessTextInput(apui::Character character);
// Sends a string of UTF-8 text input into this context.
bool ProcessTextInput(const apui::String& string);

// Sends a mouse movement event into this context.
bool ProcessMouseMove(int x, int y, int key_modifier_state);
// Sends a mouse-button down event into this context.
bool ProcessMouseButtonDown(int button_index, int key_modifier_state);
// Sends a mouse-button up event into this context.
bool ProcessMouseButtonUp(int button_index, int key_modifier_state);
// Sends a mouse-wheel movement event into this context.
bool ProcessMouseWheel(float wheel_delta, int key_modifier_state);
```

Call the appropriate input functions to inject all relevant user input into your APUI context each frame, before you call `Update()`. Note that APUI does not translate key presses into text; this is up to the application. Make sure to take a look at the included backends, as they provide key conversion to APUI and event handling for different platforms. For more information on each function, see the [user input manual](input.html). 


### Debugger

The `RmlDebugger` plugin is a visual debugger for APUI elements, inspired by similar debuggers for web browsers. We strongly recommend you use this in your application during development!

To use RmlDebugger, include `<APUI/Debugger.h>` in your application and link with `RmlDebugger`. For usage details, see the documentation for the [debugger plugin](debugger.html).


### Where next?

Now that you've had a (very!) brief introduction to APUI, it is recommended you read the [core overview](core_overview.html) to get an understanding of the composition of APUI. From there, either work your way through the documentation, or dive on into the code and consult it as necessary. 
