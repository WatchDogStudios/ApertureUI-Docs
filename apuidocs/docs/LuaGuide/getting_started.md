---
layout: page
title: Getting started
parent: LuaGuide
next: embedding_script
---

The Lua plugin for APUI can be used in an application that extends or embeds Lua. Your application will still need to initialize the APUI core library and provide the necessary System and Render interfaces, see the [C++ manual](../cpp_manual.html) for details on how to initialize APUI.

For a full list of types and methods please see the APUI Lua [API Reference](api_reference.html).

### Requirements

- [Lua 5.1+](https://www.lua.org/)

Tested with Lua 5.3 which is the recommended version, but we aim for compatibility with Lua version 5.1 and newer, including support for LuaJIT. There is also an unofficial Lua plugin [RmlSolLua](https://github.com/LoneBoco/RmlSolLua) based on sol3 with Lua 5.1 compatibility.

### Lua plugin integration

Perform the following steps to integrate the Lua plugin with APUI.

1. Download and build the Lua 5.x library, or install it with your package manager.

2. Build APUI with the Lua plugin enabled. See [Building with CMake](../cpp_manual/building_with_cmake.html) in the C++ manual for details.
    - Enable the option `BUILD_LUA_BINDINGS` during the CMake configuration.
	- You may also need to guide CMake to find the Lua libraries by providing `LUA_DIR` set to the Lua directory.
	- We encourage you to also enable the samples, `BUILD_SAMPLES` options, and try to build the `luainvaders` sample application to test that everything is working.

3. Within your application, setup and initialize APUI as you normally would, see [integrating APUI](../cpp_manual/integrating.html) in the C++ manual.

4. Link with the `RmlLua` library just as you would link to `RmlCore`.

5. Include the Lua plugin headers in your C++ source files: `#include <APUI/Lua.h>`.

6. Finally, initialize the Lua library with the single call to `apui::Lua::Initialise();`.
    - This call should happen just after the call to `apui::Initialise();`.
	- It is also possible to provide your own lua state by calling `apui::Lua::Initialise(lua_State* L);`.

Once you are done integrating the Lua plugin, you can start [embedding Lua scripts](embedding_script.html) inside your HTML documents.
