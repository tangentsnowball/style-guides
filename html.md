# HTML Style Guide

*A reasonable style guide for modern HTML development.*

## <a name='TOC'>Table of Contents</a>

1. [Whitespace](#whitespace)
1. [Formatting](#formatting)
1. [Attribute Order](#attribute-order)
1. [Naming Conventions](#naming-conventions)
1. [Resources](#resources)
1. [License](#license)

> ### "Arguments over style are pointless. There should be a style guide, and you should follow it."
>*Rebecca Murphey*

## <a name='whitespace'>Whitespace</a>

Use soft tabs set to 2 spaces.

```html
<!-- Bad -->
<ul>
....<li>Apples</li>
</ul>

<!-- Good -->
<ul> {
..<li>Apples</li>
</ul>
```

Place an empty newline at the end of the file.

```html
<!-- Bad -->
<ul>
  <li>Oranges</li>
</ul>
```

```html
<!-- Good -->
<ul>
  <li>Oranges</li>
</ul>

```

**[[⬆]](#TOC)**

## <a name='formatting'>Formatting</a>

The chosen code format encourages the use of existing, common, sensible patterns.

+ Always use lowercase tag and attribute names
+ Write one discrete element per line
+ Use double quotes for attribute values `""` e.g. `<input type="text">`
+ Use valueless boolean attributes e.g. `checked` rather than `checked="checked"`
+ Omit the `type` attributes from `link` stylesheet, `style` and `script` elements
+ Always include closing tags
+ Don't include a trailing slash in self-closing elements

```html
<!-- Bad -->
<article class='tweet'>
  <a href='path/to/profile'><img src='path/to/image.jpg' alt='' /></a><br />
  [tweet text]<br /><button disabled='disabled'>Reply</button>
</article>

<!-- Good -->
<article class="tweet">
  <a href="path/to/profile">
    <img src="path/to/image.jpg" alt="">
  </a>

  <p>[tweet text]</p>

  <button disabled>Reply</button>
</article>
```

**[[⬆]](#TOC)**

## <a name='attribute-order'>Attribute Order</a>

1. `id`
1. `class`
1. `data-*`
1. Everything else

```html
<!-- Bad -->
<button type="button" data-toggle="button" class="btn" id="button">Toggle</button>

<!-- Good -->
<button id="button" class="btn" data-toggle="button" type="button">Toggle</button>
```

**[[⬆]](#TOC)**

## <a name='naming-conventions'>Naming Conventions</a>

Naming is hard, but very important. It's a crucial part of the process of developing a maintainable code base, and ensuring that you have a relatively scalable interface between your HTML and CSS/JS.

+ Use clear, thoughtful and appropriate names for HTML classes. They should be informative both within HTML and CSS files
+ All code should be lowercase: This applies to element names, attributes, attribute values, selectors, properties and property values.
+ Separate words in ID and class names with a hyphen

```html
<!-- Bad -->
<DIV class="cb s_scr"></DIV>

<!-- Good -->
<div class="column-body is-scrollable"></div>
```

For more information on naming conventions please view the [CSS style guide](https://github.com/nathanstaines/style-guides/blob/master/css.md#naming-conventions).

**[[⬆]](#TOC)**

## <a name='resources'>Resources</a>

**The Spec**

+ [HTML: The Living Standard](http://developers.whatwg.org/)

**Books**

+ [HTML5 for Web Designers](http://www.abookapart.com/products/html5-for-web-designers)

**Blogs**

+ [HTML5 Doctor](http://html5doctor.com/)
+ [MDN HTML](https://developer.mozilla.org/en/docs/HTML)

**Other Styleguides**

+ [GitHub HTML Style Guide](https://github.com/styleguide/html)
+ [Google HTML/CSS Style Guide](http://google-styleguide.googlecode.com/svn/trunk/htmlcssguide.xml)

**[[⬆]](#TOC)**

## <a name='license'>License</a>

(The MIT License)

Copyright (c) 2012 Nathan Staines

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
'Software'), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

**[[⬆]](#TOC)**
