# JavaScript Style Guide

*A reasonable style guide for modern JavaScript development.*

## <a name='TOC'>Table of Contents</a>

1. [Objects](#objects)
1. [Arrays](#arrays)
1. [Strings](#strings)
1. [Functions](#functions)
1. [Properties](#properties)
1. [Variables](#variables)
1. [Conditional Evaluation](#conditional-evaluation)
1. [Blocks](#blocks)
1. [Whitespace](#whitespace)
1. [Leading Commas](#leading-commas)
1. [Semicolons](#semicolons)
1. [Naming Conventions](#naming-conventions)
1. [Comments](#comments)
1. [jQuery](#jquery)
1. [Resources](#resources)
1. [License](#license)

> ### "All code in any code-base should look like a single person typed it, no matter how many people contributed."
>*idiomatic.js*

## <a name='objects'>Objects</a>

Use the literal syntax for object creation.

```javascript
// Bad
var item = new Object();

// Good
var item = {};
```

Don't use [reserved words](https://developer.mozilla.org/en-US/docs/JavaScript/Reference/Reserved_Words) as keys.

```javascript
// Bad
var superman = {
    class: 'superhero',
    default: { clark: 'kent' },
    private: true
};

// Good
var superman = {
    klass: 'superman',
    defaults: { clark: 'kent' },
    hidden: true
};
```

**[[⬆]](#TOC)**

## <a name='arrays'>Arrays</a>

Use the literal syntax for array creation.

```javascript
// Bad
var items = new Array();

// Good
var items = [];
```

If you don't know array length use Array#push.

```javascript
var someStack = [];

// Bad
someStack[someStack.length] = 'abracadabra';

// Good
someStack.push('abracadabra');
```

When you need to copy an array use Array#slice.

``` javascript
var len = items.length,
    itemsCopy = [],
    i;

// Bad
for (i = 0; i < len; i++) {
    itemsCopy[i] = items[i];
}

// Good
itemsCopy = Array.prototype.slice.call(items);
```

**[[⬆]](#TOC)**

## <a name='strings'>Strings</a>

Use single quotes `''` for strings.

```javascript
// Bad
var name = "Bob Parr";

// Good
var name = 'Bob Parr';
```

Strings longer than 80 characters should be written across multiple lines using string concatenation.

```javascript
// Bad
var errorMessage = 'This is a super long error that was thrown because of Batman. When you stop to think about how Batman had anything to do with this, you would get nowhere fast.';

// Bad
var errorMessage = 'This is a super long error that \
was thrown because of Batman. \
When you stop to think about \
how Batman had anything to do \
with this, you would get nowhere \
fast.';

// Good
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
// Anonymous function expression
var anonymous = function() {
    return true;
};

// Named function expression
var named = function named() {
    return true;
};

// Immediately-invoked function expression (IIFE)
(function() {
    console.log('Welcome to the Internet. Please follow me.');
})();
```

Never declare a function in a non-function block (if, while, etc). Assign the function to a variable instead. Browsers will allow you to do it, but they all interpret it differently, which is bad news.

```javascript
// Bad
if (currentUser) {
    function test() {
        console.log('Nope.');
    }
}

// Good
if (currentUser) {
    var test = function test() {
        console.log('Yup.');
    };
}
```

Never name a parameter `arguments`, this will take precendence over the `arguments` object that is given to every function scope.

```javascript
// Bad
function nope(name, options, arguments) {
    // ...stuff...
}

// Good
function yup(name, options, args) {
    // ...stuff...
}
```

**[[⬆]](#TOC)**

## <a name='properties'>Properties</a>

Use dot notation when accessing properties.

```javascript
var luke = {
    jedi: true,
    age: 28
};

// Bad
var isJedi = luke['jedi'];

// Good
var isJedi = luke.jedi;
```

Use subscript notation `[]` when accessing properties with a variable.

```javascript
var luke = {
    jedi: true,
    age: 28
};

function getProp(prop) {
    return luke[prop];
}

var isJedi = getProp('jedi');
```

**[[⬆]](#TOC)**

## <a name='variables'>Variables</a>

Always use `var` to declare variables. Not doing so will result in global variables. We want to avoid polluting the global namespace. Captain Planet warned us of that.

```javascript
// Bad
superPower = new SuperPower();

// Good
var superPower = new SuperPower();
```

Use one `var` declaration for multiple variables and declare each variable on a newline.

```javascript
// Bad
var items = getItems();
var goSportsTeam = true;
var drangonball = 'z';

// Good
var items = getItems(),
    goSportsTeam = true,
    drangonball = 'z';
```

Assign variables at the top of their scope. This helps avoid issues with variable declaration and assignment hoisting related issues.

```javascript
// Bad
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

// Good
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

Use shortcuts

```javascript
// Bad
if (name !== '') {
    // ...stuff...
}

// Good
if (name) {
    // ...stuff...
}

// Bad
if (collection.length > 0) {
    // ...stuff...
}

// Good
if (collection.length) {
    // ...stuff...
}
```

**[[⬆]](#TOC)**

## <a name='blocks'>Blocks</a>

Use braces with all multi-line blocks.

```javascript
// Bad
if (test)
    return false;

// Good
if (test) {
    return false;
}

// Bad
function() { return false; }

// Good
function() {
    return false;
}
```

**[[⬆]](#TOC)**

## <a name='whitespace'>Whitespace</a>

Use soft tabs set to 4 spaces.

```javascript
// Bad
function() {
..var name;
}

// Good
function() {
....var name;
}
```

Place 1 space before the leading brace.

```javascript
// Bad
function test(){
    console.log('test');
}

// Good
function test() {
    console.log('test');
}
```

Place an empty newline at the end of the file.

```javascript
// Bad
(function(global) {
    // ...stuff...
})(this);
```

```javascript
// Good
(function(global) {
    // ...stuff...
})(this);

```

**[[⬆]](#TOC)**

## <a name='leading-commas'>Leading Commas</a>

**Nope.**

```javascript
// Bad
var once
  , upon
  , aTime;

// Good
var once,
    upon,
    aTime;

// Bad
var hero = {
    firstName: 'Bob'
  , lastName: 'Parr'
  , heroName: 'Mr. Incredible'
  , superPower: 'strength'
};

// Good
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
// Bad
(function() {
    var name = 'Skywalker'
    return name
})()

// Good
(function() {
    var name = 'Skywalker';
    return name;
})();
```

**[[⬆]](#TOC)**

## <a name='naming-conventions'>Naming Conventions</a>

Avoid single letter names. Be descriptive with your naming.

```javascript
// Bad
function q() {
    // ...stuff...
}

// Good
function query() {
    // ...stuff...
}
```

Use camelCase when naming objects, functions, and instances.

```javascript
// Bad
var OBJEcttsssss = {};
var this_is_my_object = {};
var this-is-my-object = {};
function c() {};
var u = new user({
    name: 'Bob Parr'
});

// Good
var thisIsMyObject = {};
function thisIsMyFunction() {};
var user = new User({
    name: 'Bob Parr'
});
```

Use PascalCase when naming constructors or classes.

```javascript
// Bad
function user(options) {
    this.name = options.name;
}

var bad = new user({
    name: 'nope'
});

// Good
function User(options) {
    this.name = options.name;
}

var good = new User({
    name: 'yup'
});
```

**[[⬆]](#TOC)**

## <a name='comments'>Comments</a>

Use `//` for single line comments. Place single line comments on a newline above the subject of the comment. Put an emptyline before the comment.

```javascript
// Bad
var active = true; // Is current tab

// Good
// Is current tab
var active = true;

// Bad
function getType() {
    console.log('fetching type...');
    // Set the default type to 'no type'
    var type = this._type || 'no type';

    return type;
}

// Good
function getType() {
    console.log('fetching type...');

    // Set the default type to 'no type'
    var type = this._type || 'no type';

    return type;
}
```

Use `/** ... */` for multiline comments.

```javascript
// Bad
// make() returns a new element
// based on the passed in tag name
function make(tag) {

    // ...stuff...

    return element;
}

// Good
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

## <a name='jquery'>jQuery</a>

Prefix jQuery object variables with a `$`.

```javascript
// Bad
var container = $('#container');

// Good
var $container = $('#container');
```

Cache jQuery lookups.

```javascript
// Bad
function setContainer() {
    $('#container').hide();

    // ...stuff...

    $('#container').show();
}

// Good
function setContainer() {
    var $container = $('#container');

    $container.hide();

    // ...stuff...

    $container.show();
}
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

**Tutorials**

+ [30 Days to Learn jQuery](https://tutsplus.com/course/30-days-to-learn-jquery/)

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
