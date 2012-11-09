# JavaScript Style Guide

*A reasonable style guide for modern JavaScript development.*

## <a name='TOC'>Table of Contents</a>

1. [Objects](#objects)
1. [Arrays](#arrays)
1. [Strings](#strings)
1. [Functions](#functions)
1. [Variables](#variables)
1. [Conditional Evaluation](#conditional-evaluation)
1. [Blocks](#blocks)
1. [Comments](#comments)
1. [Whitespace](#whitespace)
1. [Leading Commas](#leading-commas)
1. [Semicolons](#semicolons)
1. [Naming Conventions](#naming-conventions)
1. [jQuery](#jquery)
1. [Resources](#resources)
1. [License](#license)

> ### "All code in any code-base should look like a single person typed it, no matter how many people contributed."
>*idiomatic.js*

## <a name='objects'>Objects</a>

Use the literal syntax for object creation.

```javascript
// bad
var item = new Object();

// good
var item = {};
```

Don't use [reserved words](https://developer.mozilla.org/en-US/docs/JavaScript/Reference/Reserved_Words) as keys.

```javascript
// bad
var superman = {
  class: 'superhero',
  default: { clark: kent },
  private: true
};

// good
var superman = {
  klass: 'superman',
  defaults: { clark: kent },
  hidden: true
};
```

**[[⬆]](#TOC)**

## <a name='arrays'>Arrays</a>

Use the literal syntax for array creation.

```javascript
// bad
var items = new Array();

// good
var items = [];
```

For [performance reasons](http://jsperf.com/array-direct-assignment-vs-push/5) use direct assignment over Array#push.

```javascript
var len = items.length,
    itemsCopy = [],
    i;

// bad
for (i = 0; i < len; i++) {
  itemsCopy.push(items[i])
}

// good
for (i = 0; i < len; i++) {
  itemsCopy[i] = items[i];
}
```

**[[⬆]](#TOC)**

## <a name='strings'>Strings</a>

Use single quotes `''` for strings.

```javascript
// bad
var name = "Bob Parr";

// good
var name = 'Bob Parr';
```

Strings longer than 80 characters should be written across multiple lines using string concatenation.

```javascript
// bad
var errorMessage = 'This is a super long error that was thrown because of Batman. When you stop to think about how Batman had anything to do with this, you would get nowhere fast.';

// bad
var errorMessage = 'This is a super long error that \
was thrown because of Batman. \
When you stop to think about \
how Batman had anything to do \
with this, you would get nowhere \
fast.';

// good
var errorMessage = 'This is a super long error that ' +
  'was thrown because of Batman.' +
  'When you stop to think about ' +
  'how Batman had anything to do ' +
  'with this, you would get nowhere ' +
  'fast.';
```

**[[⬆]](#TOC)**

## <a name='functions'>Functions</a>

Function expressions:

```javascript
// anonymous function expression
var anonymous = function() {
  return true;
};

// named function expression
var named = function named() {
  return true;
};

// immediately-invoked function expression (IIFE)
(function() {
  console.log('Welcome to the Internet. Please follow me.');
})();
```

Never declare a function in a non-function block (if, while, etc). Assign the function to a variable instead. Browsers will allow you to do it, but they all interpret it differently, which is bad news.

```javascript
// bad
if (currentUser) {
  function test() {
    console.log('Nope.');
  }
}

// good
if (currentUser) {
  var test = function test() {
    console.log('Yup.');
  };
}
```

**[[⬆]](#TOC)**

## <a name='variables'>Variables</a>

Always use `var` to declare variables. Not doing so will result in global variables. We want to avoid polluting the global namespace. Captain Planet warned us of that.

```javascript
// bad
superPower = new SuperPower();

// good
var superPower = new SuperPower();
```

Use one `var` declaration for multiple variables and declare each variable on a newline.

```javascript
// bad
var items = getItems();
var goSportsteam = true;
var drangonball = 'z';

// good
var items = getItems(),
    goSportsTeam = true,
    drangonball = 'z';
```

Assign variables at the top of their scope. This helps avoid issues with variable declaration and assignment hoisting related issues.

```javascript
// bad
function() {
  test();
  console.log('doing stuff...');

  // ...other stuff...

  var name = getName();

  if (name === 'test') {
    return false;
  }

  return name;
}

// good
function() {
  var name = getName();

  test();
  console.log('doing stuff...');

  // ...other stuff...

  if (name === 'test') {
    return false;
  }

  return name;
}
```

**[[⬆]](#TOC)**

## <a name='conditional-evaluation'>Conditional Evaluation</a>

Use `===` and `!==` over `==` and `!=`.  
Conditional expressions are evaluated using coercion with the `ToBoolean` method and always follow these simple rules:

+ **Objects** evaluate to **true**
+ **Undefined** evaluates to **false**
+ **Null** evaluates to **false**
+ **Booleans** evaluate to **the value of the boolean**
+ **Numbers** evalute to **false** if **+0, -0, or NaN**, otherwise **true**
+ **Strings** evaluate to **false** if an empty string `''`, otherwise **true**

```javascript
// when evaluating that an array has length
// bad
if (array.length > 0) ...

// good
if (array.length) ...

// when evaluating that an array is empty
// bad
if (array.length === 0) ...

// good
if (!array.length) ...

// when evaluating that a string is not empty
// bad
if (string !== '') ...

// good
if (string) ...

// when evaluating that a string is empty
// bad
if (string === '') ...

// good
if (!string) ...
```

**[[⬆]](#TOC)**

## <a name='blocks'>Blocks</a>

Use braces with all multi-line blocks.

```javascript
// bad
if (test)
  return false;

// good
if (test) return false;

// good
if (test) {
  return false;
}

// bad
function() { return false; }

// good
function() {
  return false;
}
```

**[[⬆]](#TOC)**

## <a name='comments'>Comments</a>

Use `//` for single line comments. Place single line comments on a newline above the subject of the comment. Put an emptyline before the comment.

```javascript
// bad
var active = true; // is current tab

// good
// is current tab
var active = true;

// bad
function getType() {
  console.log('fetching type...');
  // set the default type to 'no type'
  var type = this._type || 'no type';

  return type;
}

// good
function getType() {
  console.log('fetching type...');

  // set the default type to 'no type'
  var type = this._type || 'no type';

  return type;
}
```

Use `/** ... */` for multiline comments.

```javascript
// bad
// make() returns a new element
// based on the passed in tag name
function make(tag) {

  // ...stuff...

  return element;
}

// good
/**
 * make() returns a new element
 * based on the passed in tag name
 */
function make(tag) {

  // ...stuff...

  return element;
}
```

**[[⬆]](#TOC)**

## <a name='whitespace'>Whitespace</a>

Use soft tabs set to 2 spaces.

```javascript
// bad
function() {
∙∙∙∙var name;
}

// good
function() {
∙∙var name;
}
```

Place 1 space before the leading brace.

```javascript
// bad
function test(){
  console.log('test');
}

// good
function test() {
  console.log('test');
}
```

Place an empty newline at the end of the file.

```javascript
// bad
(function(global) {
  // ...stuff...
})(this);

// good
(function(global) {
  // ...stuff...
})(this);

```

**[[⬆]](#TOC)**

## <a name='leading-commas'>Leading Commas</a>

**Nope.**

```javascript
// bad
var once
  , upon
  , aTime;

// good
var once,
    upon,
    aTime;

// bad
var hero = {
    firstName: 'Bob'
  , lastName: 'Parr'
  , heroName: 'Mr. Incredible'
  , superPower: 'strength'
};

// good
var hero = {
  firstName: 'Bob',
  lastName: 'Parr',
  heroName: 'Mr. Incredible',
  superPower: 'strength'
};
```

**[[⬆]](#TOC)**

## <a name='semicolons'>Semicolons</a>

**Yup.**

```javascript
// bad
(function() {
  var name = 'Skywalker'
  return name
})()

// good
(function() {
  var name = 'Skywalker';
  return name;
})();
```

**[[⬆]](#TOC)**

## <a name='naming-conventions'>Naming Conventions</a>

Avoid single letter names. Be descriptive with your naming.

```javascript
// bad
function q() {
  // ...stuff...
}

// good
function query() {
  // ...stuff...
}
```

Use camelCase when naming objects, functions, and instances.

```javascript
// bad
var OBJEcttsssss = {};
var this_is_my_object = {};
var this-is-my-object = {};
function c() {};
var u = new user({
  name: 'Bob Parr'
});

// good
var thisIsMyObject = {};
function thisIsMyFunction() {};
var user = new User({
  name: 'Bob Parr'
});
```

Use PascalCase when naming constructors or classes.

```javascript
// bad
function user(options) {
  this.name = options.name;
}

var bad = new user({
  name: 'nope'
});

// good
function User(options) {
  this.name = options.name;
}

var good = new User({
  name: 'yup'
});
```

Use a leading underscore `_` when naming private properties.

```javascript
// bad
this.__firstName__ = 'Panda';
this.firstName_ = 'Panda';

// good
this._firstName = 'Panda';
```

**[[⬆]](#TOC)**

## <a name='jquery'>jQuery</a>

Prefix jQuery object variables with a `$`.

```javascript
// bad
var sidebar = $('.sidebar');

// good
var $sidebar = $('.sidebar');
```

Cache jQuery lookups.

```javascript
// bad
function setSidebar() {
  $('.sidebar').hide();

  // ...stuff...

  $('.sidebar').css({
    'background-color': 'pink'
  });
}

// good
function setSidebar() {
  var $sidebar = $('.sidebar');

  $sidebar.hide();

  // ...stuff...

  $sidebar.css({
    'background-color': 'pink'
  });
}
```

Scope jQuery object queries with find. [jsPerf](http://jsperf.com/jquery-find-vs-context-sel/13)

```javascript
// bad
$('.sidebar ul').hide();

// bad
$('.sidebar > ul').hide();

// bad
$('.sidebar', 'ul').hide();

// good
$('.sidebar').find('ul').hide();
```

**[[⬆]](#TOC)**

## <a name='resources'>Resources</a>

**The Spec**

+ [Annotated ECMAScript 5.1](http://es5.github.com/)

**Books**

+ [JavaScript: The Good Parts](http://www.amazon.com/JavaScript-Good-Parts-Douglas-Crockford/dp/0596517742) - Douglas Crockford
+ [Eloquent JavaScript (online version)](http://eloquentjavascript.net) - Marijn Haverbeke
+ [Learning JavaScript Design Patterns (online version)](http://addyosmani.com/resources/essentialjsdesignpatterns/book/) - Addy Osmani

**Blogs**

+ [Paul Irish](http://paulirish.com/)
+ [Addy Osmani](http://addyosmani.com/blog/)
+ [Rebecca Murphey](http://rmurphey.com/)
+ [JavaScript, JavaScript...](http://javascriptweblog.wordpress.com/)
+ [Adequately Good](http://www.adequatelygood.com/)

**Other Styleguides**

+ [Airbnb JavaScript Style Guide](https://github.com/airbnb/javascript) (which this guide was based on)
+ [Google JavaScript Style Guide](http://google-styleguide.googlecode.com/svn/trunk/javascriptguide.xml)
+ [jQuery Core Style Guidelines](http://docs.jquery.com/JQuery_Core_Style_Guidelines)
+ [Principles of Writing Consistent, Idiomatic JavaScript](https://github.com/rwldrn/idiomatic.js/)

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
