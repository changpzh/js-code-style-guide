# <a name="main"></a>JavaScript Guidelines

Aug 1, 2019

* [In: Introduction](#S-introduction)
* [O: Old Style Guide](#S-oldGuide)
* [CP: Common code problems](#S-CommonCodeProblems)

# <a name="S-introduction"></a>In: Introduction

Introduction summary:

* [In.target: Target readership](#SS-readers)
* [In.aims: Aims](#SS-aims)
* [In.not: Non-aims](#SS-non)
* [In.force: Enforcement](#SS-force)
* [In.struct: The structure of this document](#SS-struct)
* [In.sec: Major sections](#SS-sec)

# <a name="S-oldGuide"></a>O: Old Style Guide

* [O.list: List of Rules](#SS-ruleList_Old)
* [O.packageJson: "package.json" Rules](#SS-packageJson_Old)
* [O.Language: Language Rules](#SS-languageRules_Old)
* [O.style: Style Rules](#SS-style_Old)
* [O.git: Git Rules](#SS-git_Old)
* [O.design: Design Rules](#SS-design_Old)
* [O.testing: Testing Rules](#SS-testing_Old)
* [O.howTo: How to create rule](#SS-howTo_Old)

## <a name="SS-ruleList_Old"></a>O.list: List of Rules

* [Rule 1. Avoid manual edits of package.json files](#T-rule1_Old)
* [Rule 2. Always use declarations with `var`](#T-rule2_Old)
* [Rule 3. Always use semicolons](#T-rule3_Old)
* [Rule 4. All variables and functions should be declared before used](#T-rule4_Old)
* [Rule 5. Define variables where they're needed](#T-rule5_Old)
* [Rule 6. You can use nested functions](#T-rule6_Old)
* [Rule 7. Do not declare functions within blocks](#T-rule7_Old)
* [Rule 8. Write your entire code in the strict mode](#T-rule8_Old)
* [Rule 9. Avoid using `continue` statement](#T-rule9_Old)
* [Rule 10. Avoid using `with` statement](#T-rule10_Old)
* [Rule 11. Avoid using of the comma operator](#T-rule11_Old)
* [Rule 12. Avoid doing assignments in the condition part of `if` and `while` statements](#T-rule12_Old)
* [Rule 13. Use `let` instead of `var` if you don't need function scope (supported from node.js v4.0.0)](#T-rule13_Old)
* [Rule 14. You can use exceptions](#T-rule14_Old)
* [Rule 15. Use `for-in` loops for object/map/hash only](#T-rule15_Old)
* [Rule 16. Never use `Array` as a map/hash/associative array](#T-rule16_Old)
* [Rule 17. Use `Array` and `Object` literals instead of `Array` and `Object` constructors](#T-rule17_Old)
* [Rule 18. Never modify the prototypes of bulid-in objects (like `Object` or `Array`)](#T-rule18_Old)
* [Rule 19. `eval` is Evil](#T-rule19_Old)
* [Rule 20. Be careful about not intuitive boolean expressions](#T-rule20_Old)
* [Rule 21. `&&` and `||` binary boolean operators are short-circulated, and evaluate to the last evaluated term](#T-rule21_Old)
* [Rule 22. Use underscore map, filter, reduce, find on arrays when it's possible](#T-rule22_Old)
* [Rule 23. Chain map, filter, reduce, find, etc.. when possible](#T-rule23_Old)
* [Rule 24. Always use Promises to write asynchronous code](#T-rule24_Old)
* [Rule 25. Always use non-blocking I/O functions](#T-rule25_Old)
* [Rule 26. Naming Conventions - Generally use CamelCase and ...](#T-rule26_Old)
* [Rule 27. Use four spaces for the indentation](#T-rule27_Old)
* [Rule 28. Avoid really long lines](#T-rule28_Old)
* [Rule 29. Do not modify input parameters in functions if it's not necessary](#T-rule29_Old)
* [Rule 30. Functions that change input parameters should have names that suggest it](#T-rule30_Old)
* [Rule 31. Use `===` instead of `==` unless you're completely sure you want behavior of `==` operator](#T-rule31_Old)
* [Rule 32. Be careful to not follow a + with + or ++](#T-rule32_Old)
* [Rule 33. Always start your curly braces on the same line as whatever they're opening](#T-rule33_Old)
* [Rule 34. Large initializing structures should be broken into lines](#T-rule34_Old)
* [Rule 35. When possible, all function arguments should be listed on the same line, otherwise wrap them in readable way](#T-rule35_Old)
* [Rule 36. Wrap entire invocation expression in parens if you invoke the function immediately](#T-rule36_Old)
* [Rule 37. Use newlines to group logically-related pieces of code](#T-rule37_Old)
* [Rule 38. Use blanks for setting off the sections of code that are logically related](#T-rule38_Old)
* [Rule 39. Double-quotes for strings `"` are preferred](#T-rule39_Old)
* [Rule 40. Do not declare multiline strings](#T-rule40_Old)
* [Rule 41. Deferred initialization is fine](#T-rule41_Old)
* [Rule 42. Use parentheses only where required](#T-rule42_Old)
* [Rule 43. Be generous with comments, ideally write self-commenting code](#T-rule43_Old)
* [Rule 44. Use JSDoc syntax for anything which needs to be commented](#T-rule44_Old)
* [Rule 45. Use eslint for static code analysis, catching up above mentioned errors and more](#T-rule45_Old)
* [Rule 46. Prefer `git pull --rebase` over `git pull` (proposal)](#T-rule46_Old)
* [Rule 47. Use meaningful names for branches](#T-rule47_Old)
* [Rule 48. Use functional style instead of object-oriented when possible](#T-rule48_Old)
* [Rule 49. Testing is mandatory for all parts of the code](#T-rule49_Old)
* [Rule 50. Use `TDD` for writing your tests (or at least try to use)](#T-rule50_Old)
* [Rule 51. Use `zurvan` if you want to test timeouts / have timeouts in code](#T-rule51_Old)
* [Rule 52. Use Path.normalize when working with directories](#T-rule52_Old)

## <a name="SS-packageJsonOld"></a>O.packageJson: "package.json" Rules

### <a name="T-rule1_Old"></a>Rule 1. Avoid manual edits of package.json files

Use `npm install [@<scope>/]<name> --save|--save-dev --save-exact` for adding new packages to packages.json
![remark][remark] You can use aliases: `npm i [@<scope>/]name -S -E`. See https://docs.npmjs.com/cli/install

![rationale][rationale] Rationale:

The before mentioned command does alphabetical sort and reformatting of the package.json file - it is convenient to use and keeps the file clean and ordered.
Mixing manual changes and "npm install way" of working creates unnecessary problems with the merge conflicts.

***

## <a name="SS-languageRules_Old"></a>O.Language: Language Rules

### <a name="T-rule2_Old"></a>Rule 2. Always use declarations with `var`

![rationale][rationale] Rationale:

When you fail to specify `var`, the variable gets placed in the global context, potentially clobbering existing values. Also, if there's no declaration, it's hard to tell in what scope a variable lives (e.g., it could be in the Document or Window just as easily as in the local scope). So always declare with `var`.

***

### <a name="T-rule3_Old"></a>Rule 3. Always use semicolons

![rationale][rationale] Rationale:

* Relying on implicit insertion can cause subtle, hard to debug problems.
* JavaScript requires statements to end with a semicolon, except when it thinks it can safely infer their existence.
* The closing brackets are not enough to signal the end of the statement.
* Javascript never ends a statement if the next token is an infix or bracket operator.

![remark][remark] Remark:

* Semicolons should be included at the end of function expressions, but not at the end of function declarations:

```javascript
var foo = function() {
    return true;
}; // Semicolon here

function foo() {
    return true;
} // No semicolon here
```

***

### <a name="T-rule4_Old"></a>Rule 4. All variables and functions should be declared before used

![rationale][rationale] Rationale:

JavaScript does not require this, but doing so makes the program easier to read and makes it easier to detect undeclared variables that may become implied globals. Implied global variables should never be used. Use of global variables should be minimized.

***

### <a name="T-rule5_Old"></a>Rule 5. Define variables where they're needed

![rationale][rationale] Rationale:

JavaScript does not have block scope, so defining variables in blocks can confuse programmers who are experienced with other C family languages. Be careful about hoisting.

***

### <a name="T-rule6_Old"></a>Rule 6. You can use nested functions

![rationale][rationale] Rationale:

Nested functions can be very useful, for example in the creation of continuations and for the task of hiding helper functions. Feel free to use them.
However, inner functions should follow the `var` statement. This helps make it clear what variables are included in its scope.

***

### <a name="T-rule7_Old"></a>Rule 7. Do not declare functions within blocks

![rationale][rationale] Rationale:

![warning][warning] Do not do this:

```javascript
if (x) {
    function foo() {}
}
```

While most script engines support Function Declarations within blocks it is not part of ECMAScript (see: [ECMA-262](http://www.ecma-international.org/publications/standards/Ecma-262.htm), clause 13 and 14). Worse implementations are inconsistent with each other and with future ECMAScript proposals.
ECMAScript only allows for Function Declarations in the root statement list of a script or function:

```javascript
if (x) {
    var foo = function() {};
}
```

***

### <a name="T-rule8_Old"></a>Rule 8. Write your entire code in the strict mode

![rationale][rationale] Rationale:

Strict Mode ("use strict") is a new feature in ECMAScript 5 that allows you to place a program, or a function, in a "strict" operating context. This strict context prevents certain actions from being taken and throws more exceptions.

Strict mode helps out in a couple ways:

* It catches some common coding bloopers, throwing exceptions.
* It prevents, or throws errors, when relatively "unsafe" actions are taken (such as gaining access to the global object).
* It disables features that are confusing or poorly thought out.

***

### <a name="T-rule9_Old"></a>Rule 9. Avoid using `continue` statement

![rationale][rationale] Rationale:

It tends to obscure the control flow of the function.

***

### <a name="T-rule10_Old"></a>Rule 10. Avoid using `with` statement

![rationale][rationale] Rationale:

The `with` statement should [not be used](http://yuiblog.com/blog/2006/04/11/with-statement-considered-harmful/)

***

### <a name="T-rule11_Old"></a>Rule 11. Avoid using of the comma operator

![rationale][rationale] Rationale:

This does not apply to the comma separator, which is used in object literals, array literals, `var` statements, and parameter lists.

***

### <a name="T-rule12_Old"></a>Rule 12. Avoid doing assignments in the condition part of `if` and `while` statements

![rationale][rationale] Rationale:

Is

```javascript
if (a = b) {
```

a correct statement? Or was

```javascript
if (a === b) {
```

intended? Avoid constructs that cannot easily be determined to be correct.

***

### <a name="T-rule13_Old"></a>Rule 13. Use `let` instead of `var` if you don't need function scope (supported from node.js v4.0.0)

![rationale][rationale] Rationale:

`let` make variables to be block scoped. This gives more control where variables are visible.

***

### <a name="T-rule14_Old"></a>Rule 14. You can use exceptions

![rationale][rationale] Rationale:

You basically can't avoid exceptions if you're doing something non-trivial (using an application development framework, etc.).

***

### <a name="T-rule15_Old"></a>Rule 15. You should not use `for`, `while` and `for-in` loops for iterating through containers like arrays or objects

![rationale][rationale] Rationale:

These kinds of loops are not used in functional programming which is the main paradigm for megazone project (see rule 48). Concepts like map or each (forEach) should rather be used to traverse containers. There are also utilities to transform object keys/values into array over which you can later iterate. `for-in` loops are often incorrectly used to loop over the elements in an array. This is however very error prone because it does not loop from `0` to `length - 1` but over all the present keys in the object and its prototype chain.

Here are a few cases where it fails:

```javascript
function printArray(arr) {
    for (var key in arr) {
        print(arr[key]);
    }
}

printArray([0, 1, 2, 3]);  // This works.

var a = new Array(10);
printArray(a);  // This is wrong.

a = document.getElementsByTagName("*");
printArray(a);  // This is wrong.

a = [0, 1, 2, 3];
a.buhu = "wine";
printArray(a);  // This is wrong again.

a = new Array;
a[3] = 3;
printArray(a);  // This is wrong again.
```

![remark][remark] Always use each or map when using arrays:

```javascript
function printArray(arr) {
    _.each(arr, function(elem) {
        print(elem);
    });
}
```

![remark][remark] Always use each or map with keys or values combination when using objects:

```javascript
function printObjKeys(obj) {
    _.each(_.keys(obj), function(key) {
        print(key);
    });
}

function printObjValues(obj) {
    _.each(obj, function(val) { // _.each and _.map iterate over values by default when passed an object
        print(val);
    });
}
```

***

### <a name="T-rule16_Old"></a>Rule 16. Never use `Array` as a map/hash/associative array

![rationale][rationale] Rationale:

Associative arrays are not allowed... or more precisely you are not allowed to use non number indexes for arrays. If you need a map/hash use `Object` instead of `Array` in these cases because the features that you want are actually features of `Object` and not of `Array`. `Array` just happens to extend `Object` (like any other object in JS and therefore you might as well have used `Date`, `RegExp` or `String`).

***

### <a name="T-rule17_Old"></a>Rule 17. Use `Array` and `Object` literals instead of `Array` and `Object` constructors

![rationale][rationale] Rationale:

![warning][warning] Array constructors are error-prone due to their arguments.

Because of this, if someone changes the code to pass 1 argument instead of 2 arguments, the array might not have the expected length:

```javascript
// Length is 3.
var a1 = new Array(x1, x2, x3);

// Length is 2.
var a2 = new Array(x1, x2);

// If x1 is a number and it is a natural number the length will be x1.
// If x1 is a number but not a natural number this will throw an exception.
// Otherwise the array will have one element with x1 as its value.
var a3 = new Array(x1);

// Length is 0.
var a4 = new Array();
```

To avoid these kinds of weird cases, always use the more readable array literal:

```javascript
var a = [x1, x2, x3];
var a2 = [x1, x2];
var a3 = [x1];
var a4 = [];
```

![remark][remark] Object constructors don't have the same problems, but for readability and consistency object literals should be used. So the following code:

```javascript
var o = new Object();

var o2 = new Object();
o2.a = 0;
o2.b = 1;
o2.c = 2;
o2["strange key"] = 3;
```

should be written as:

```javascript
var o = {};

var o2 = {
    a: 0,
    b: 1,
    c: 2,
    "strange key": 3
};
```

![remark][remark] Use arrays when the member names would be sequential integers. Use objects when the member names are arbitrary strings or names.

***

### <a name="T-rule18_Old"></a>Rule 18. Never modify the prototypes of built-in objects (like `Object` or `Array`)

![rationale][rationale] Rationale:

Modifying built-ins like `Object.prototype` and `Array.prototype` are strictly forbidden. Modifying other built-ins like `Function.prototype` is less dangerous but still leads to hard to debug issues in production and should be avoided.

***

### <a name="T-rule19_Old"></a>Rule 19. `eval` is Evil

![rationale][rationale] Rationale:

The `eval` function is the most misused feature of JavaScript. Avoid it.

1. Improper use of eval opens up your code for injection attacks
2. Debugging can be more challenging (no line numbers, etc.)
2. eval'd code executes more slowly (no opportunity to compile/cache eval'd code)

***

### <a name="T-rule20_Old"></a>Rule 20. Be careful about not intuitive boolean expressions

![rationale][rationale] Rationale:

The following are false in boolean expressions

* `null`
* `undefined`
* `""` -- the empty string
* `0` -- the number

![warning][warning] But be careful, because these are all true:

* `"0"` -- the string
* `[]` -- the empty array
* `{}` -- the empty object

***

### <a name="T-rule21_Old"></a>Rule 21. `&&` and `||` binary boolean operators are short-circulated, and evaluate to the last evaluated term

![rationale][rationale] Description:

`||` has been called the default operator, because instead of writing this:

```javascript
function foo(opt_win) {
    var win;
    if (opt_win) {
        win = opt_win;
    } else {
        win = window;
    }
}
```

you can write this:

```javascript
function foo(opt_win) {
    var win = opt_win || window;
}
```

***

### <a name="T-rule22_Old"></a>Rule 22. Use underscore map, filter, reduce, find on arrays when it's possible

![rationale][rationale] Rationale:

It's more readable, name of method you're using shows why you are iterating over array. Use underscore versions, because it's usually faster than native versions.

![badExample][badExample] map bad code example:

```javascript
function changeToSeconds(timesInMiliseconds) {
    var timesInSeconds = [];
    timesInMiliseconds.forEach(function(timeInMillisecond) {
        timesInSeconds.push(timeInMillisecond / 1000);
    });
    return timesInSeconds;
}
```

![goodExample][goodExample] map good example:

```javascript
function changeToSeconds(timesInMiliseconds) {
    return _.map(timesInMiliseconds, function(timeInMilisecond) {
        return timeInMilisecond / 1000
    });
}
```

![badExample][badExample] filter bad code example:

```javascript
function getManagedObjectsWithClass(managedObjects, className) {
    var matchingManagedObjects = [];
    for (var i = 0; i < managedObjects.length; ++i) {
        if(managedObjects[i].className === className) {
            matchingManagedObjects.push(managedObjects[i]);
        }
    }
    return matchingManagedObjects;
}
```

![goodExample][goodExample] filter good code example

```javascript
function getManagedObjectsWithClass(managedObjects, className) {
    return _.filter(managedObjects, function(managedObject) {
        return managedObject.className === className;
    });
}
```

![remark][remark]  use `_.find` instead of `filter` if you want only one element from array:

![badExample][badExample] reduce bad example

```javascript
function countWords(words) {
    var countedWords = {};
    words.forEach(function(word) {
        countedWords[word] = countedWords[word] + 1 || 1;
    });
    return countedWords;
}
```

![badExample][badExample]![badExample][badExample] reduce **very bad** example

```javascript
function countWords(words) {
    return words.length;
}
```

![goodExample][goodExample] reduce good example

```javascript
function countWords(words) {
    return _.reduce(words, function(countedWords, word) {
        countedWords[word] = countedWords[word] + 1 || 1;
        return countedWords; //remember to always return from reduce
    });
}
```

***

### <a name="T-rule23_Old"></a>Rule 23. Chain map, filter, reduce, find, etc.. when possible

![rationale][rationale] Rationale:

This improves readability by showing operation flow. Also start each step from new line.

![badExample][badExample] Bad example

```javascript
function getActiveFaultsCount(faults) {
    return _.reduce(activeFaults, function(count, fault) {
        if (!isActiveFault(fault)) {
            return count;
        }
        return count + 1;
    });
}
```

![badExample][badExample] Bad example

```javascript
function getActiveFaultsCount(faults) {
    var activeFaults = _.filter(faults, function(fault) {
        return isActiveFault(fault);
    });
    return _.reduce(activeFaults, function(count, fault) {
        return count + 1;
    });
}
```

![goodExample][goodExample] Good example

```javascript
function getActiveFaultsCount(faults) {
    return _.chain(faults)
        .filter(isActiveFault)
        .reduce(function(count, fault) {
            return count + 1;
        })
        .value();
}
```

***

### <a name="T-rule24_Old"></a>Rule 24. Always use Promises to write asynchronous code

![rationale][rationale] Rationale:

Callbacks tend to become more and more nested when chaining multiple async operations. This obfuscates the code and makes flow of operations harder to follow.

Promises greatly improve readability of such code and make it look like it was synchronous code, so the flow of operations is easy to follow. It also reduces indentations to almost single level.

bluebird is our library of choice for Promises so you should not use native Promises from ES standard.

![badExample][badExample] Bad example

```javascript
doSomeAsyncOperation(param, function(err, result) {
    if (err) {
        return handleError(err);
    }
    return anotherAsync(result, function(err, something) {
        if (err) {
            return handleSpecificError(err);
        }
        var nextArg = syncOp(something);
        return anotherCallbackedOperation(nextArg, function(err, whatever) {
            if (err) {
                return handleError(err);
            }
            return youCanSeeWhereItIsGoing(whatever, function(err, yeah) {
                if (err) {
                    return handleError(err);
                }
                return toBeautifulChristmasTree(yeah, function(err, bummer) {
                    if (err) {
                        return handleError(err);
                    }
                    return soHardToReadAndThisHasOnlyLinearFlow(bummer);
                });
            });
        });
    });
});
```

![goodExample][goodExample] Good example

```javascript
doSomeAsyncOperation(param)
    .then(anotherAsync)
    .then(function(something) {
        return anotherPromisifiedOperation(syncOp(something));
    })
    .then(nowYouCanSee)
    .then(thatThisIsMuchEasierToRead)
    .then(andFollow)
    .then(especiallyWhenYouDefineAllStepsAsSeparateFunctions)
    .then(thereIsNoChristmasTreeAtTheEnd)
    .catch(specificError, alsoErrorsAreEasierToHandle)
    .catch(asYouCanHandleThemAlsoInGenericWay);
```

***

### <a name="T-rule25_Old"></a>Rule 25. Always use non-blocking I/O functions

![rationale][rationale] Rationale:

Node.js is single threaded runtime environment, using blocking I/O functions affects whole application and makes it non-responsive.

![badExample][badExample] Bad example

```javascript
var fs = require("fs");
var fileContent = fs.readFileSync("filename.ext", "utf8");

doSomeAction(fileContent);
```

![goodExample][goodExample] Good example

```javascript
var Promise = require("bluebird");
var fs = Promise.promisifyAll(require("fs"));

fs.readFileAsync("filename.ext", "utf8").then(doSomeAction);
```

***

## <a name="SS-style_Old"></a>O.style: Style Rules

### <a name="T-rule26_Old"></a>Rule 26. Naming Conventions - Generally use CamelCase and ...

![rationale][rationale] Rationale:

In general, use `functionNamesLikeThis`, `variableNamesLikeThis`, `ClassNamesLikeThis`, `EnumNamesLikeThis`, `methodNamesLikeThis`, `CONSTANT_VALUES_LIKE_THIS`, `foo.namespaceNamesLikeThis.bar`, and `filenameslikethis.js`.

Do not use $ *(dollar sign)* or \ *(backslash)* in names.
Do not use _ *(underbar)* as the first or last character of a name. It is sometimes intended to indicate privacy, but it does not actually provide privacy. If privacy is important, use the forms that provide [private members](http://javascript.crockford.com/private.html).

Most variables and functions should start with a lower case letter.
Constructor functions that must be used with the [`new` prefix](http://yuiblog.com/blog/2006/11/13/javascript-we-hardly-new-ya/) should start with a capital letter. JavaScript issues neither a compile-time warning nor a run-time warning if a required new is omitted. Bad things can happen if `new` is not used, so the capitalization convention is the only defense we have.
Global variables should be in all caps. (JavaScript does not have macros or constants, so there isn't much point in using all caps to signify features that JavaScript doesn't have.)

![remark][remark] Be consistent

***

### <a name="T-rule26_Old"></a>Rule 26. Use four spaces for the indentation

![rationale][rationale] Rationale:

The unit of indentation is four spaces. Use of tabs is not allowed because (as of this writing in the 21st Century) there still is not a standard for the placement of tabstops. The use of spaces can produce a larger filesize, but the size is not significant over local networks, and the difference is eliminated by [minification](http://yuiblog.com/blog/2006/03/06/minification-v-obfuscation/).

***

### <a name="T-rule28_Old"></a>Rule 28. Avoid really long lines

![rationale][rationale] Rationale:

When a statement will not fit on a single line, the context becomes hardly readable and it may be necessary to break it. Place the break after an operator, ideally after a comma. A break after an operator decreases the likelihood that a copy-paste error will be masked by semicolon insertion. Let the IDE layout your code.

***

### <a name="T-rule29_Old"></a>Rule 29. Do not modify input parameters in functions if it's not necessary

![rationale][rationale] Rationale:

This improves code reusability.

***

### <a name="T-rule30_Old"></a>Rule 30. Functions that change input parameters should have names that suggest it

![goodExample][goodExample] Good example

```javascript
function insertParameterToManagedObject(managedObject, parameter) {
    managedObject.parameters.push(parameter);
}
```

![badExample][badExample] Bad example

![warning][warning] do not do this:

```javascript
function calculateSomething(someObject) {
    someObject.calculations = someObject.a + someObject.b;
    return someObject.calculations;
}
```

***

### <a name="T-rule31_Old"></a>Rule 31. Use `===` instead of `==` unless you're completely sure you want behavior of `==` operator

![rationale][rationale] Rationale:

You can find equality table of `==` operator here https://dorey.github.io/JavaScript-Equality-Table/. If you're sure it is what you want, you can use it.

***

### <a name="T-rule32_Old"></a>Rule 32. Be careful to not follow a + with + or ++

![rationale][rationale] Rationale:

this pattern can be confusing. Insert parens between them to make your intention clear:

```javascript
total = subtotal + +myInput.value;
```

is better written as:

```javascript
total = subtotal + (+myInput.value);
```

![warning][warning] so that the `+ +` is not misread as `++`.

***

### <a name="T-rule33_Old"></a>Rule 33. Always start your curly braces on the same line as whatever they're opening

![rationale][rationale] Rationale:

There should be no space between the name of a function and the `(` *(left parenthesis)* of its parameter list. There should be one space between the `)` *(right parenthesis)* and the `{` *(left curly brace)* that begins the statement body. The body itself is indented four spaces. The `}` *(right curly brace)* is aligned with the line containing the beginning of the declaration of the function.

```javascript
function outer(c, d) {
    var e = c * d;

    function inner(a, b) {
        return (e * a) + b;
    }

    return inner(0, 1);
}
```

If a function literal is anonymous, there shouldn't be any space between the word `function` and the `(` *(left parenthesis)*.

```javascript
div.onclick = function(e) {
    return false;
};

that = {
    method: function() {
        return this.datum;
    },
    datum: 0
};
```

***

### <a name="T-rule34_Old"></a>Rule 34. Large initializing structures should be broken into lines

![rationale][rationale] Rationale:

Single-line array and object initializers are allowed when they fit on a line.

```javascript
var arr = [1, 2, 3];
var obj = {a: 1, b: 2, c: 3};
```

Multiline array initializers and object initializers are indented 4 spaces, with the braces on their own line.

```javascript
var stuff = {
    top: 10,
    right: 20,
    bottom: 30,
    left: 40
};

var people = [
    "\"Mark\" <mark@nokia.com>",
    "\"Tom\" <tom@nokia.com>",
    "\"Travis\" <travis@nokia.com>"
];

foo.bar.doSomething(baz, {
    id: 123,
    margin: stuff,
    color: "black"
}, people, "Hello World!");
```

***

### <a name="T-rule35_Old"></a>Rule 35. When possible, all function arguments should be listed on the same line, otherwise wrap them in readable way

![rationale][rationale] Rationale:

To save space, you may put each argument on its own line to *enhance readability*.

Examples:

```javascript
// Four-space, one argument per line. Works with long function names,
// survives renaming, and emphasizes each argument.
// Arguments are indented twice to show separation with function code.
mz.foo.bar.baz.doThatThingThatIsVeryDifficultToExplain = function(
        veryDescriptiveArgumentNumberOne,
        anotherVeryDescriptiveArgumentNumberTwo,
        tableModelEventHandlerProxyThing,
        descriptorAdapterIteratorControllerThingy) {
    // ...
};
// Keep 'em aligned
if ((functionA() === functionB()) ||
    (functionC() && functionD())) {
    // ...
}

if (searchableCollection(allYourStuff).contains(stuffYouWant) &&
    !ambientNotification.isActive() &&
    (client.isAmbientSupported() ||
     client.alwaysTryAmbientAnyways())) {
    // ...
}

foo.bar.reallyLongFunctionName("whatever", function(a1, a2) {
    // ...
});

var stuff = foo.bar.myExcellentMapFunction(
    someCollectionNameThatsVeryLong,
    function(item) {
        // ...
    }
);
```

***

### <a name="T-rule36_Old"></a>Rule 36. Wrap only the function expression in parens if you invoke the function immediately

![rationale][rationale] Rationale:

```javascript
var collection = (function() {
    var keys = [], values = [];

    return {
        get: function(key) {
            var at = keys.indexOf(key);
            if (at >= 0) {
                return values[at];
            }
        },
        set: function(key, value) {
            var at = keys.indexOf(key);
            if (at < 0) {
                at = keys.length;
            }
            keys[at] = key;
            values[at] = value;
        },
        remove: function(key) {
            var at = keys.indexOf(key);
            if (at >= 0) {
                keys.splice(at, 1);
                values.splice(at, 1);
            }
        }
    };
})();
```

***

### <a name="T-rule37_Old"></a>Rule 37. Use newlines to group logically-related pieces of code

![rationale][rationale] Rationale:

This improves the code readability and tracking the flow of a scenario.

Don't use braces to wrap around those fragments of code. ES5 has no block scoping of variables so this is valid, but might cause confusion.

***

### <a name="T-rule38_Old"></a>Rule 38. Use blanks for setting off the sections of code that are logically related

![rationale][rationale] Rationale:

Blank lines improve readability by setting off sections of code that are logically related.
Blank spaces should be used in the following circumstances:

* A keyword (with the exception of `function`) followed by `(` *(left parenthesis)* should be separated by a space.

```javascript
while (true) {
```

* A blank space should not be used between a function value (or keyword `function` for anonymous functions) and its `(` *(left parenthesis)*.
* All binary operators except `.` *(period)* and `(` *(left parenthesis)* and `[` *(left bracket)* should be separated from their operands by a space.
* No space should separate a unary operator and its operand except when the operator is a word such as `typeof`.
* Each `;` *(semicolon)* in the control part of a for statement should be followed with a space.
* Whitespace should follow every `,` *(comma)*.

***

### <a name="T-rule39_Old"></a>Rule 39. Double-quotes for strings `"` are preferred

![rationale][rationale] Rationale:

To be consistent with the rest of the code.

***

### <a name="T-rule40_Old"></a>Rule 40. Do not declare multiline strings

![rationale][rationale] Rationale:

![badExample][badExample] Here:
```javascript
var myString = "A rather long string of English text, an error message \
                actually that just keeps going and going -- an error \
                message to make the Energizer bunny blush (right through \
                those Schwarzenegger shades)! Where was I? Oh yes, \
                you\'ve got an error and all the extraneous whitespace is \
                just gravy. Have a nice day.";
```

the whitespace at the beginning of each line can't be safely stripped at compile time. Whitespace after the slash will result in tricky errors and while most script engines support this, it is not part of ECMAScript.

![goodExample][goodExample] Use string concatenation instead:

```javascript

var myString = "A rather long string of English text, an error message " +
    "actually that just keeps going and going -- an error " +
    "message to make the Energizer bunny blush (right through " +
    "those Schwarzenegger shades)! Where was I? Oh yes, " +
    "you\'ve got an error and all the extraneous whitespace is " +
    "just gravy. Have a nice day.";
```

***

### <a name="T-rule41_Old"></a>Rule 41. Deferred initialization is fine

![rationale][rationale] Rationale:

It isn't always possible to initialize variables at the point of declaration, so deferred initialization is fine.

***

### <a name="T-rule42_Old"></a>Rule 42. Use parentheses only where required

![rationale][rationale] Rationale:

Use sparingly and in general only where required by the syntax and semantics.
Never use parentheses for unary operators such as `delete`, `typeof` and `void` or after keywords such as `return`, `throw` as well as others (`case`, `in` or `new`).

***

### <a name="T-rule43_Old"></a>Rule 43. Be generous with comments, ideally write self-commenting code

![rationale][rationale] Rationale:

It is useful to leave information that will be read at a later time by people (possibly yourself) who will need to understand what you have done. The comments should be well-written and clear, just like the code they are annotating. An occasional nugget of humor might be appreciated. Frustrations and resentments will not.

It is important that comments be kept up-to-date. Erroneous comments can make programs even harder to read and understand.

Make comments meaningful. Focus on what is not immediately visible. Don't waste the reader's time with stuff like:

```javascript
i = 0; // Set i to zero.
```

![remark][remark] Generally use line comments. Save block comments for formal documentation.

***

### <a name="T-rule44_Old"></a>Rule 44. Use JSDoc syntax for anything which needs to be commented

![rationale][rationale] Rationale:

Names for functions, properties and methods should be descriptive on a level which enables developers to conclude easily what they were intended to do. All files, methods and properties can be documented with [JSDoc](http://code.google.com/p/jsdoc-toolkit/) comments with the appropriate [tags](https://google-styleguide.googlecode.com/svn/trunk/javascriptguide.xml#JSDoc_Tag_Reference) and [types](https://google-styleguide.googlecode.com/svn/trunk/javascriptguide.xml#JsTypes). Textual descriptions for properties, methods, method parameters and method return values can be included unless obvious from the property, method, or parameter name.

***

### <a name="T-rule45_Old"></a>[Rule 45. Use eslint for static code analysis, catching up above mentioned errors and more

***

## <a name="SS-git_Old"></a>O.git: Git Rules

### <a name="T-rule46_Old"></a>Rule 46. Prefer `git pull --rebase` over `git pull` (proposal)

![rationale][rationale] Rationale:
This simplifies history of branch by not creating merge commits every pull.

***

### <a name="T-rule47_Old"></a>Rule 47. Use meaningful names for branches

![rationale][rationale] Rationale:

![goodExample][goodExample] Good examples:

`RefactoringOfTests`, `FeatureMz3_4_Implementation`

![badExample][badExample] Bad examples:

`branch1`, `ares`, `fgjdoif`, (random letters)

***

## <a name="SS-design_Old"></a>O.design: Design Rules

### <a name="T-rule48_Old"></a>Rule 48. Use functional style instead of object-oriented when possible

![rationale][rationale] Rationale:

This is official paradigm used in our megazone projects.

![remark][remark] Remark:

You can use nested functions. Nested functions can be very useful, for example, in the creation of continuations and for the task of hiding helper functions.

***

## <a name="SS-testing_Old"></a>O.testing: Testing Rules

### <a name="T-rule49_Old"></a>Rule 49. Testing is mandatory for all parts of the code

![rationale][rationale] Rationale:

* Do not create legacy code; write Clean Code.
* JavaScript and all other dynamic programming languages are in dire need of tests since there is no compile-time checking.
* Tests ensure that the application behaves as expected.
* Tests give developers confidence to make changes to existing code.
* Who does not want testable, maintainable, readable, well-designed, modular, and working code?

***

### <a name="T-rule50_Old"></a>Rule 50. Use `TDD` for writing your tests (or at least try to use)

![rationale][rationale] Rationale:

* Better understanding of what you're going to write
* Enforces the policy of writing tests a little better
* Speeds up development

***

### <a name="T-rule51_Old"></a>Rule 51. Use `zurvan` if you want to test timeouts / have timeouts in code

![rationale][rationale] Rationale:

Waiting 30s for timeout in tests is unnaceptable. `zurvan` lets you instantly forward time.

***

### <a name="T-rule52_Old"></a>Rule 52. Use Path.normalize when working with directories

![rationale][rationale] Rationale:

If path is not normalized, there is a chance that directory will not be located due to difference in file separators per operating system.

***

## <a name="SS-howTo_Old"></a>O.howTo: How to create rule

Template:

```markdown

### <a name="T-rule(number)_Old"></a> Rule (number). (Name)

![rationale][rationale] Rationale:
(Description)

***

```

Use this construction for JS Code:

    ```javascript
    // example JS Code
    ```




[rationale]: images/help_16.png
[remark]: images/information.png
[warning]: images/warning.png
[goodExample]: images/check.png
[badExample]: images/error.png

# <a name="S-CommonCodeProblems"></a>CP: Common code problems

Common code problems

Take a deeper look on the page taking into the consideration common code problems (described below).
This will help you to avoid misleading results of some functions and test utils usage.

The problems described here have been found in numerous places, primarily in test code, but some of them are also relevant to production code. Please take the time to read this carefully; hopefully we can greatly improve the quality and robustness code tests by understanding and fixing these problems.

After working with nodeoam tests - trying to make them run with `grunt test` so we could always execute all of them, and not waste lots of time as it's right now with runner - I've been able to identify some common problems with code you are write in tests, as well as some that can also be found in actual production code.

* [CP.promises: Promises](#SS-CP.promises)
* [CP.timeintests: Time in tests](#SS-CP.timeintests)
* [CP.pac: Promises and continuations](#SS-CP.pac)

## <a name="SS-CP.promises"></a> Promises

Let's start with some trivial ones. First of all, when you create promise chains, you need to handle them properly. If you are not using a test promise wrapper (testPromiseMinimal or bimTestFrame - more about this one later), you should not return the promise and expect everything to work. In this case, you are supposed to attach at least two continuations at the end of the chain:

* `.then(test.done)`
* `.catch(test.done)`

This way, successful executions will end the test properly, and ones where there's an exception thrown will *fail* the test (as they are usually supposed to). Missing `.catch()` is quite frequent - it works when the test passes, but kills the process when it is not (and we want to execute all tests and see all the failed ones - not just kill everything when the first one fails).

There can be also other reasons for killing the process, this is crucial to also take them into the consideration during fault analysis:

* Unhandled promise `reject`
    * Due to throwing an exception
    * Due to unhandled promise rejection without `test.done()` call
    * Due to handled promise rejection without `test.done()` call
* Just missing `test.done()` call

Attaching a `.finally(test.done)` doesn't quite cut it - this way all exceptions thrown are mostly ignored (`test.done` is called by that, so test ends up being successful, and we do not yet have a global way of properly handling unhandled rejections in all cases). However, one should remember that calling `.finally(test.done("This will fail this tests case"))` will result in fail, even inside the `.finally` structure. Such construction can be also often met in our tests.

Unfortunately, sometimes even `.catch()` at the promise chain can be useless, especially when something in the code happens asynchronously, apart from the promise chain. Such situation would require us to maintain a global exception handler, for entire test case.

![remark][remark] Examples:

1. Example:

    ![badExample][badExample] **Wrong**
    ```javascript
    getPromise().then(function() {
       potentiallyThrowingOperation();
    }).finally(test.done);
    ```
    ![goodExample][goodExample] **Correct**
    ```javascript
    getPromise().then(function() {
        potentiallyThrowingOperation();
    }).then(test.done).catch(test.done);
    ```

2. Example:

    ![badExample][badExample] **Wrong**
    ```javascript
    getPromise().then(function() {
        potentiallyThrowingOperation();
    }).then(test.done);
    ```
    ![goodExample][goodExample] **Correct**
    ```javascript
    getPromise().then(function() {
        potentiallyThrowingOperation();
    }).then(test.done).catch(test.done);
    ```

## <a name="SS-CP.timeintests"></a> Time in tests

Please be aware that in both SiteOAM and NodeOAM a library for "mocking" the timers exists - it resides in `testutils/chronos.js`. Please do not use real time in tests.

It is important to realize that handling of mocked timeouts works differently in promise environment and can be not intuitive (placeholder for the code example).

![warning][warning] EXAMPLE NEEDED

```javascript
404 - example not found // TODO
```

## <a name="SS-CP.pac"></a> Promises and continuations

It seems quite frequent for you to wrongly pass a continuation function to `.then` (or `.catch` and `.finally`), especially when a single function is supposed to be called with some arguments as a callback; this is a problem in both test and production code.

![badExample][badExample] Take a look at this example snippet:

```javascript
function f(i) { console.log(i); }
getSomePromise().then(f(3));
```

This can be seen often, and most of the time results in warnings saying that `.then` only takes a function, not an object. The above is wrong, because `f(3)` will be called immediately, and not after the promise resolves.

![goodExample][goodExample] One of the correct ways to do this (the other involves calling `.bind` on the function, but that's arguably less readable):

```javascript
getSomePromise().then(function() {
    f(3);
});
```

This way, `f(3)` will be called after the promise is fulfilled, not immediately, before attaching a continuation. Of course the first example would be fine if `f(3)` returned a function that's supposed to be called when the promise is resolved. In all cases, same goes for `.catch` and `.finally`.

![remark][remark] Other examples:

1. Example:

    ![badExample][badExample] **Possibly wrong**
    ```javascript
    getPromise().then(f(3));
    ```
    ![goodExample][goodExample] **Correct**
    ```javascript
    getPromise.then(function() {
        f(3);
    });
    ```

2. Example:

    ![badExample][badExample] **Possibly wrong**
    ```javascript
    getPromise().then(f(3));
    ```
    ![goodExample][goodExample] **Correct**
    ```javascript
    getPromise().then(_.partial(f, 3));
    ```
