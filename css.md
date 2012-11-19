# CSS Style Guide

*A reasonable style guide for modern CSS development.*

## <a name='TOC'>Table of Contents</a>

1. [Whitespace](#whitespace)
1. [Formatting](#formatting)
1. [Declaration Order](#declaration-order)
1. [Naming Conventions](#naming-conventions)
1. [Comments](#comments)
1. [Resources](#resources)
1. [License](#license)

> ### "Part of being a good steward to a successful project is realising that writing code for yourself is a Bad Idea™. If thousands of people are using your code, then write your code for maximum clarity, not your personal preference of how to get clever within the spec."
>*Idan Gazit*

## <a name='whitespace'>Whitespace</a>

Use soft tabs set to 2 spaces.

```css
/* Bad */
.selector {
∙∙∙∙display: block;
}

/* Good */
.selector {
∙∙display: block;
}
```

Place 1 space before the leading brace and place 1 space after the colon of a declaration.

```css
/* Bad */
.selector{
  float:left;
}

/* Good */
.selector {
  float: left;
}
```

Place an empty newline at the end of the file.

```css
/* Bad */
.selector {
  clear: both;
}
```

```css
/* Good */
.selector {
  clear: both;
}

```

**[[⬆]](#TOC)**

## <a name='formatting'>Formatting</a>

The chosen code format ensures that code is: easy to read; easy to clearly comment; minimises the chance of accidentally introducing errors; and results in useful diffs and blames.

+ Use 1 selector per line in multi-selector rulesets
+ Use 1 declaration per line in a declaration block
+ Use lowercase and shorthand hex values
+ Use single quotes `''` e.g. `input[type='checkbox']`
+ *Where allowed*, avoid specifying units for zero-values e.g. `margin: 0`
+ Omit leading '0's in values or lengths between -1 and 1.
+ Include a space after each comma in comma-separated property or function values
+ Include a semi-colon at the end of the last declaration in a declaration block
+ Place the closing brace of a ruleset in the same column as the first character of the ruleset
+ Separate each ruleset by a blank line

```css
/* Bad */
.selector-1, .selector-2, .selector-3 { display: block; font-family: helvetica,arial,sans-serif; background: #fff; background: linear-gradient(#fff,rgba(0,0,0,.8)) }
.selector-a, .selector-b { padding: 10px }

/* Good */
.selector-1,
.selector-2,
.selector-3 {
  display: block;
  font-family: helvetica, arial, sans-serif;
  background: #fff;
  background: linear-gradient(#fff, rgba(0, 0, 0, .8));
}

.selector-a,
.selector-b {
  padding: 10px;
}
```

**[[⬆]](#TOC)**

## <a name='declaration-order'>Declaration Order</a>

Declare structurally important properties prior to all others.

```css
.selector {
  /* Positioning */
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 10;

  /* Display and Box Model */
  display: inline-block;
  overflow: hidden;
  width: 100px;
  height: 100px;
  margin: 10px;
  padding: 10px;
  border: 1px solid #ccc;

  /* Typography */
  font-family: sans-serif;
  font-size: 16px;
  line-height: 24px;
  text-align: right;
  vertical-align: baseline;
  white-space: nowrap;
  color: #333;

  /* Other */
  background: #fff;
  opacity: .75;
  cursor: default;
  content: '';
}
```

**[[⬆]](#TOC)**

## <a name='naming-conventions'>Naming Conventions</a>

Elements that **occur exactly** once inside a page should use IDs, otherwise, use classes. When in doubt, use a class name.

+ **Good** candidates for ids: header, footer, modal popups
+ **Bad** cadidates for ids: navigation, item listings

Use meaningful or generic ID and class names.

```css
/* Bad */
#yee-1901 {
  float: left;
}

.button-green {
  background: #060;
}

/* Good */
#gallery {
  float: left;
}

.primary {
  background: #060;
}
```

Use ID and class names that are as short as possible but as long as necessary.

```css
/* Bad */
#navigation {
  display: block;
}

.atr {
  font-weight: bold;
}

/* Good */
#nav {
  display: block;
}

.author {
  font-weight: bold;
}
```

Separate words in ID and class names with a hyphen.

```css
/* Bad */
.demoimage {
  border: 1px solid #ccc;
}

.error_text {
  color: #f00;
}

/* Good */
.demo-image {
  border: 1px solid #ccc;
}

.error-text {
  color: #f00;
}
```

Avoid qualifying ID and class names with type selectors.

```css
/* Bad */
ul#example {
  list-style: none;
}

div.error-block {
  background: #fff0f0;
}

/* Good */
#example {
  list-style: none;
}

.error-block {
  background: #fff0f0;
}
```

All code should be lowercase: This applies to element names, attributes, attribute values, selectors, properties and property values.

```css
/* Bad */
BODY {
  margin: 0;
}

/* Good */
body {
  margin: 0;
}
```

**[[⬆]](#TOC)**

## <a name='comments'>Comments</a>

```css
/* ==========================================================================
   Section comment block
   ========================================================================== */

/* Sub-section comment block
   ===================================== */

/**
 * This is a docBlock style comment
 *
 * This is a longer description of the comment, describing the code in more
 * detail. Limit these lines to a maximum of 80 characters in length.
 */

/* Basic comment */
```

**Example**:

```css
/* ==========================================================================
   Typography
   ========================================================================== */

p {
  margin: 0 0 20px;
  font-size: 16px;
}

/* Headings
   ===================================== */

h1,
h2,
h3,
h4,
h5,
h6 {
  margin: 0 0 20px;
  font-family: serif;
  font-weight: bold;
  text-rendering: optimizelegibility; /* Fix the character spacing for headings */
}
```

**[[⬆]](#TOC)**

## <a name='resources'>Resources</a>

**Blogs**

+ [CSS-Tricks](http://css-tricks.com/)

**Other Styleguides**

+ [GitHub CSS Style Guide](https://github.com/styleguide/css)
+ [Google HTML/CSS Style Guide](http://google-styleguide.googlecode.com/svn/trunk/htmlcssguide.xml)
+ [Principles of Writing Consistent, Idiomatic CSS](https://github.com/necolas/idiomatic-css)
+ [Isobar Front-end Code Standards & Best Practices](http://isobar-idev.github.com/code-standards/#_css)

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
