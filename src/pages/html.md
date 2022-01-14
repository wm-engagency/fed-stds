---
layout: ../layouts/MainLayout.astro
title: HTML Style Guide
toc:
  - text: Syntax
    link: syntax
  - text: HTML5 doctype
    link: html5-doctype
  - text: Language attribute
    link: language-attribute
  - text: Internet Explorer compatibility mode
    link: ie-compatibility-mode
  - text: Character encoding
    link: character-encoding
  - text: CSS and JavaScript includes
    link: css-javascript-includes
  - text: Practicality over purity
    link: practicality-over-purity
  - text: Attribute order
    link: attribute-order
  - text: Boolean attributes
    link: boolean-attributes
  - text: Reducing markup
    link: reducing-markup
  - text: JavaScript generated markup
    link: javascript-generated-markup
description: |
  These HTML guidelines are adapted from <a href="https://codeguide.co/">CodeGuide</a> which were written by the creator of Twitter's Bootstrap Framework <a href="https://github.com/mdo">@mdo</a>. As stated by @mdo, and on any of these guidelines, "enforce these, on your own, agreed upon guidelines at all times. Small or large, call out what's incorrect."

  And if you would like to suggest any changes to this adapted version of @mdo's guidelines, submit a PR to the repository for these guidelines.
---

## Syntax

* Don't capitalize tags, including the doctype.
* Use soft tabs with two spaces—they're the only way to guarantee code renders the same in any environment.
* Nested elements should be indented once (two spaces).
* Always use double quotes, never single quotes, on attributes.
* Don't include a trailing slash in self-closing elements—the HTML5 spec says they're optional.
* Don’t omit optional closing tags (e.g. `</li>` or `</body>`).


```html
<!doctype html>
<html>
  <head>
    <title>Page title</title>
  </head>
  <body>
    <img src="images/company-logo.png" alt="Company">
    <h1 class="hello-world">Hello, world!</h1>
  </body>
</html>
```

[return to top]()

## HTML5 doctype

Enforce [standards mode](https://developer.mozilla.org/en-US/docs/Web/HTML/Quirks_Mode_and_Standards_Mode) and more consistent rendering in every browser possible with this simple doctype at the beginning of every HTML page.

```html
<!doctype html>
<html>
  <head>
  </head>
</html>
```

[return to top]()

## Language attribute
From the HTML5 spec:

> Authors are encouraged to specify a lang attribute on the root html element, giving the document's language. This aids speech synthesis tools to determine what pronunciations to use, translation tools to determine what rules to use, and so forth.

Read more about the `lang` attribute [in the spec](https://www.w3.org/html/wg/drafts/html/master/semantics.html#the-html-element). Head to Sitepoint for a [list of language codes](https://www.sitepoint.com/iso-2-letter-language-codes/).

```html
<html lang="en">
  <!-- ... -->
</html>
```

[return to top]()

## IE compatibility mode

There's no need to include the Internet Explorer document compatibility `<meta>` tag with IE11. This was used by IE10 and below to declare the highest compatibility mode for the deprecated browser. Microsoft Edge doesn't support document modes.

For more information, [read this awesome Stack Overflow article](https://stackoverflow.com/questions/6771258/what-does-meta-http-equiv-x-ua-compatible-content-ie-edge-do).

```html
<!-- IE10 and below only -->
<meta http-equiv="x-ua-compatible" content="ie=edge">
```

[return to top]()

## Character encoding

Quickly and easily ensure proper rendering of your content by declaring an explicit character encoding. When doing so, you may avoid using character entities in your HTML, provided their encoding matches that of the document (generally UTF-8).

```html
<head>
  <meta charset="utf-8">
</head>
```

[return to top]()

## CSS and JavaScript includes

Per HTML5 spec, typically there is no need to specify a type when including CSS and JavaScript files as text/css and text/javascript are their respective defaults.

### HTML5 spec links

* [Using link](https://www.w3.org/TR/2011/WD-html5-20110525/semantics.html#the-link-element)
* [Using style](https://www.w3.org/TR/2011/WD-html5-20110525/semantics.html#the-style-element)
* [Using script](https://www.w3.org/TR/2011/WD-html5-20110525/scripting-1.html#the-script-element)

```html
<!-- External CSS -->
<link rel="stylesheet" href="code-guide.css">

<!-- In-document CSS -->
<style>
  /* ... */
</style>

<!-- JavaScript -->
<script src="code-guide.js"></script>
```

[return to top]()

## Practicality over purity

Strive to maintain HTML standards and semantics, but not at the expense of practicality. Use the least amount of markup with the fewest intricacies whenever possible.

[return to top]()

## Attribute order

HTML attributes should come in this particular order for easier reading of code.

* `class`
* `id`, `name`
* `data-*`
* `src`, `for`, `type`, `href`, `value`
* `title`, `alt`
* `role`, `aria-*`

Classes make for great reusable components, so they come first. Ids are more specific and should be used sparingly (e.g., for in-page bookmarks), so they come second.

```html
<a class="..." id="..." data-toggle="modal" href="#">
  Example link
</a>

<input class="form-control" type="text">

<img src="..." alt="...">
```

[return to top]()

## Boolean attributes

A boolean attribute is one that needs no declared value. XHTML required you to declare a value, but HTML5 has no such requirement.

For further reading, consult the [WhatWG section on boolean attributes](https://www.whatwg.org/specs/web-apps/current-work/multipage/common-microsyntaxes.html#boolean-attributes):

> The presence of a boolean attribute on an element represents the true value, and the absence of the attribute represents the false value.

If you *must* include the attribute's value, and **you don't need to**, follow this WhatWG guideline:

> If the attribute is present, its value must either be the empty string or [...] the attribute's canonical name, with no leading or trailing whitespace.

**In short, don't add a value.**

```html
<input type="text" disabled>

<input type="checkbox" value="1" checked>

<select>
  <option value="1" selected>1</option>
</select>
```

[return to top]()

## Reducing markup

Whenever possible, avoid superfluous parent elements when writing HTML. Many times this requires iteration and refactoring, but produces less HTML. Take the following example:

```html
<!-- Not so great -->
<span class="avatar">
  <img src="...">
</span>

<!-- Better -->
<img class="avatar" src="...">
```
[return to top]()

## JavaScript generated markup

Writing markup in a JavaScript file makes the content harder to find, harder to edit, and less performant. Avoid it whenever possible.

[return to top]()