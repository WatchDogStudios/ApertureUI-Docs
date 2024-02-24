---
layout: page
title: Loading fonts
parent: LuaGuide
next: attaching_to_events
---

The Lua plugin installs a global table `apui`, which provides a way to load supported font files from Lua. The function takes a single string as a parameter, the file name of the font to load.

```python
apui.LoadFontFace('../assets/LatoLatin-Regular.ttf')
apui.LoadFontFace('../assets/LatoLatin-Bold.ttf')
```

See the APUI [Lua API reference](api_reference.html#apui) for other things to do with this global.
