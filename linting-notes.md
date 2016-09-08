## React & JS Style Guide for Looking For Front End
#### EsLint:
* How we store & keep these style guide rules as a part of the project forever, (On top of documentation explaining syntax rules)
* Can be used for traditional linting as well as style guide checks
* Personal style preferences can be set in a ```.eslintrc``` which will get created after running ```eshint --init```
* rules are configured in eslintrc file like so:
```
{
    "rules": {
        "semi": ["error", "always"],
        "quotes": ["error", "double"]
    }
}```

* Semi and quotes in the above snippet are rules in ESLint
* While these are both set as errors, that first param can be set as either off, warn or error as well
* ESLint supports JSX as used by react, but is a configuration that must be enabled.
* While this can be configured to specifically look at JSX or JS syntax, there is also an eslint-plugin-react to specifically focus on React linting rules

#### Air BNB JavaScript Rules
(Airbnb has ESLint rules stated next to their preferred linting rules)

1) Types:
* Primitive types should be accessed directly while a complex type is accessed via  reference to its value
ex: var foo = 1, console.log(foo); var foo = [1, 2], console.log(foo[0]);

2) References:
* use const for all references, avoid using var
``` eslint: prefer-const, no-const-assign ```
* or, if you must reassign references, use let instead of var
``` eslint: no-var ```
* Both let and const are block-scoped & only exist in the blocks they are defined in. It's generally good practice to avoid reassigning references which is what happens with var

3) Objects:
* use literal syntax for object creation (const item = {})
* [Up for Debate?, 3.5] Use object method shorthand so that if an object is defined it's method is not defined as ```addValue: function(value){the rest here}``` but instead as ```addValue(value){return the rest here}```
* [3.6, up for debate] Use property value shorthand so that when a property is identical to its value you use the shorthand.
```
//bad
const obj = { lukeSkywalker: lukeSkywalker };
//good
const obj = { lukeSkywalker };
```
* [3.7, based on 3.6] If you decide to use shorthand declarations, group them at the beginning of an object declaration with multiple properties
* Only use quoted properties ('foo': 3) when the identifier is invalid and requires quotes (optimization advantage here), ```ex: 'data-blah': 5```
* Do not call Object.prototype methods directly, cache the lookup once in a module scope ``` const has = Object.prototype.hasOwnProperty```, object could be null which could cause problems

4) Arrays
* again, use literal syntax for creation
* use push instead of direct assignment to add items to an array
* Use an array spread to copy arrays const itemsCopy = [...items];
* Use Array.from() to convert array like objects to an array
```
const foo = document.querySelectorAll('.foo');
const nodes = Array.from(foo);
```
* Use return statements within array method callbacks like map, reduce or filter. If there's a case where you've got an if else and the else is just return false you can omit the else and just have return false at the end with a return statement within the if. This is only necessary however if the array callback method is longer than one line. So it is fine to have ```[1, 2, 3].map(x => x + 1)```

5) Destructuring
* Use object destructuring to prevent creating temporary references for those properties
```
instead of...
function getFullName(user){
  const firstName = user.firstName;
  const lastName = user.lastName;
  return `${firstName} ${lastName}`;
}
do this...
function getFullName({firstName, lastName}){
  return `${firstName} ${lastName}`;
}
```
* use array destructuring
```
const arr = [1, 2, 3, 4];

// bad
const first = arr[0];
const second = arr[1];

// good
const [first, second] = arr;
```
* [5.3] Use object destructuring for multiple return values instead of arrays so that order is not an issue when extrating values
```
function processInput(input){
  return { left, right, top, bottom };
}

const {left, top} = processInput(input);
```

6) Strings
* single quotes
* [6.2, Up for debate, I like it] string declarations should not be written across multiple lines even if they go over 100 characters. It is harder to see, and harder to search.
* When building strings use template strings instead of concatenation
```
function sayHi(name) {
  return `How are you, ${name}?`;
}
```
* Never use eval() on a string
* Do not unnecessarily escape characters in strings (aka double quotes within a single quoted string do not need to be escaped)

7) Functions
* use function declarations over function expressions (this makes it possible to always use arrow functions in place of function expressions)
* Wrap immediately invoked function expressions in parentheses (it is its own thing, make it look like it!)
* Don't declare a function in a non-function block (i.e. if, while) and instead assign it to a variable (a block is a list of statements, and a function declaration is not a statement)
* Never name a parameter arguments as this will override the arguments object given to every function scope
* Also, don't really ever use arguments. Use instead the rest syntax ...args because it is a real array and arguments is just an array like object
* Use default parameter syntax ``` function doStuff(opts = {})```
* Avoid default param side effects, example given is don't do math as a default value
* Always put default params last
* Never use the function constructor to create a new function
* Use spacing in a function signature ``` const x = function () {}``` when adding or removing a name you won't have to worry about spaces
* [7.12, Up for debate] Don't mutate parameters as it can cause unwanted side effects in the original caller
* for variadic functions prefer the use of the spread operator

8) Arrow functions
*[8.1, debate] When you must use function expressions (i.e. anonymous function), use the arrow function notation
* If the function is a one liner, omit the braces and use implicit return
* [8.3, debate] If the function spans multiple lines, use parentheses for readability
* If your function takes a single argument and doesn't use braces then remove the parentheses around the argument
* Try not to confuse error syntax with comparison operators
