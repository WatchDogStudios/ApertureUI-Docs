---
layout: page
title: HTML Document Structure
parent: HTML
next: style_sheets
---

### \<rml\>

All APUI documents begin with the `<rml>` element. The element should contain two children, `<head>` and `<body>`, as shown in the following basic structure of a document.

```html
<rml>
	<head>
		<title>...</title>
		<link type="text/css" href="style.css"/>
		...
	</head>
	<body>
		...
	</body>
</rml>
```

### \<head\>

The `<head>` element contains information about the current document, such as its title, style and template information is references. No information in the header is rendered.

### \<title\>

The `<title>` element contains the title of the document. This is often used for the specifying the contents of the title bar of a game window.

### \<link\>

The `<link>` element is used to specify additional resources the document requires.

_Attributes_

`type` = cdata (CI)
: Type of link, which should be one of:
* text/css - [APUI Style Sheet Specification](../css.html)
* text/template - [APUI Template](templates.html)
* text/script - APUI script

`href` = cdata (CS)
: Specifies the source URI, relative to the document being parsed.

### \<body\>

The body of a document contains the document's content. All elements within the `<body>` tag is laid out and rendered by APUI based on the active style sheets. 