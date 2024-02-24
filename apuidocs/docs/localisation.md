---
layout: page
title: Localisation
---

APUI fully supports localisation through the interface described in the following.

### String encoding

APUI assumes all data it is given, whether read in from HTML or provided procedurally, is in UTF-8 encoding. This means if you're using 8-bit ASCII you don't need to change anything, but allows you to specify multi-byte Unicode characters if required.

### Translation

All raw text that APUI reads while parsing HTML (i.e., everything other than XML tags) is sent through the `TranslateString()` function on the [system interface](C++/interfaces/system.html). The function is given the raw string as read, and the application can make any modifications necessary before returning the translated string (and the number of substitutions made) back to APUI.

A pass-through translator would do the following:

```cpp
#include <APUI/Core/SystemInterface.h>

class SampleSystemInterface : public apui::SystemInterface
{
	int TranslateString(apui::String& translated, const apui::String& input) override
	{
		translated = input;
		return 0;
	}
```

#### String tables

The `TranslateString()` method can be used in conjunction with an application's string table to make text substitutions on a document's text. For example, take the pause.rml file in the _Rocket Invaders_ sample:

```html
<html>
	<head>
		<title>Quit?</title>
	</head>
	<body>
		<p>Are you sure you want to end this game?</p>
		<button>Yes</button>
		<button>No!</button>
	</body>
</html>
```

If we were to localise _Rocket Invaders_, we'd want to move all of the English strings out from the HTML and into a string table. The raw text in the HTML would then be replaced with the string table tokens:

```html
<html>
	<head>
		<title>[QUIT_TITLE]</title>
	</head>
	<body>
		<p>[QUIT_CONFIRM]</p>
		<button>[CONFIRM]</button>
		<button>[DENY]</button>
	</body>
</html>
```

Assuming the appliation has a `StringTable` class that has loaded the appropriate string table for the language, our sample translator would then become:

```cpp
	int TranslateString(apui::String& translated, const apui::String& input) override
	{
		// Attempt to find the translation in the string table.
		if (StringTable::GetString(translated, input))
			return 1;

		// No translation; return the raw input string.
		translated = input;
		return 0;
	}
```

Now the strings will be valid for whatever language we specify a string table for. In practice, you might need a more sophisticated translator that could replace multiple tokens within a string.

Note that you can place HTML into the translated string, and it will be parsed appropriately. For example, you could replace a token with an `<img>` tag to render an icon for a controller button.
