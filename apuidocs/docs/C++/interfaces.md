---
layout: page
title: Custom interfaces
parent: C++
next: plugins
---

There are four interfaces that APUI provides to control how it interacts with your application. 

* [System interface](interfaces/system.html)
* [Render interface](interfaces/render.html)
* [File interface](interfaces/file.html)
* [Font engine interface](interfaces/font_engine.html)

Only the system and render interfaces are required to be implemented for all applications. The file interface will use a default implementation using standard library methods unless a custom one is installed first. A default font engine will also be installed, which loads fonts and renders glyphs using the FreeType library, unless the user provides their own.

To install a custom interface, instance your interface and install it with the appropriate `apui::Set*Interface()` before you initialise APUI.

```cpp
auto file_interface = std::make_unique<CustomFileInterface>();
apui::SetFileInterface(file_interface.get());

/* ... */

apui::Initalise();

/* ... */

apui::Shutdown();

file_interface.reset();

```

***Lifetime notice:*** APUI takes non-owning pointers to the interfaces, thus, make sure to keep the interface alive until after the call to `apui::Shutdown()`, and clean it up afterwards.
