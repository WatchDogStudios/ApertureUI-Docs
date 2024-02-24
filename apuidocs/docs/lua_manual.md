---
layout: page
title: Lua Manual
---
:::warning obsolete
Lua is not supported anymore with Aperture UI, as JavaScript/TypeScript is the main scripting language for the Middleware.

Dispite this, The Lua interface to APUI has been designed to resemble Javascript as closely as possible. Due the nature of the language, this is more possible in Lua than C++.

:::

The functionality of APUI is described fully in the [C++ Manual](cpp_manual.html); this manual defines the Lua interface to the aperture ui objects described there. Not all aspects of APUI are accessible from Lua; for example, custom decorators can only be created in C++. However the vast majority is accessible, enabling you to easily and efficiently develop the functionality of your documents.

A good place to get started is the `luainvaders` sample included with the library, which demonstrates many of the functionalities of the Lua plugin.

### Integrating Lua

1. [Getting started](LuaGuide/getting_started.html)
2. [Embedding script](LuaGuide/embedding_script.html)
3. [Loading fonts](LuaGuide/fonts.html)
4. [Attaching to Events](LuaGuide/attaching_to_events.html) 

### Interfaces

1. [Elements](LuaGuide/elements.html)
2. [Documents](LuaGuide/documents.html)
3. [Contexts](LuaGuide/contexts.html)
4. [Events](LuaGuide/events.html)

### Appendix

1. [API reference](LuaGuide/api_reference.html)
