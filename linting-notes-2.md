9) Classes & Constructors
* In good old ES6 fashion, use class & avoid manipulating prototype directly
* use extends for inheritance
* Methods are ok to return this to help with method chaining
* An empty constructor function, or one that just delegates to a parent class is unnecessary
* Avoid duplicate class members

10) Modules
* [10.1, Up for debate], Always use import/exports instead of module.exports, don't use wildcard imports ``` import * as ```
* do not make import/exports one liners, separate them for consistency
* [10.4, Up for debate] Do not have duplicate imports (a.k.a only import a file in one place)
* Do not export mutable bindings (i.e. vars defined using let)
* prefer default export over named when single export
* Put all imports at top of files (they are hoisted anyways)

11) Iterators and Generators
* [11.1, up for debate] Do not use iterators, use JavaScript's higher order functions like map,filter, every, etc... instead of for in or for of loops
* (listed as 13.5) Do not increment/decrement with ++ or -- and instead use += or -=, these are subject to automatic semicolon insertion, can cause silent errors, or increment/decrement before they are supposed to

12) Properties
* [12.1, up for debate but I like], use dot notation to access properties rather than object['propertyName']
* [12.2, bracket notation] use bracket notation when accessing properties with a variable

13) Variables
* Use const, one const declaration per variable, not across multiple lines
* group your const, group your lets
* Assign variables where you need them, but they should be in a reasonable place
* Don't chain variable declarations, let a = b = c = 1 --> these become global, define them separately

14) Hoisting (not really rules, but good things to know)
* var gets hoisted, which is why you get strange errors within block declarations when trying to access variables that have not yet been defined, --> Why we want to use const and let
* anonymous/named functions hoist the variable name, but not the function assignment --> function expressions
* Function declarations will hoist their name and their function body

15) Comparison Operators & Equality
* Rule of threes! (Always use === and !== over == and !=)
* Objects, strings (if not empty), numbers (if not zero) --> evaluate to true in conditional statements
* objects, even empty ones will always evaluate to true!
* Undefined, null, 0, NaN, empty strings --> false in conditional statements
* Use shortcuts in if statements, aka ``` if( num !== 0) ``` vs. ``` if(num) ```
* [15.5, Up for debate, but I like it] With a switch/case statement if the case is defining a variable make sure to use braces around the case statement (when using: let, const, function, and class)
* [15.6 I like it, but up for debate] Ternaries should always be just one line, no nested ternaries (a.k.a. ternary within another ternary)
* Don't use a ternary with true/false, a? a: b (these are unnecessary)

16) Blocks
* Braces with all multiline blocks
* [16.2, up for debate but you kids best like it] for multiline blocks but your else on same line as closing brace

17) Comments
* [17.1 Up for debate] use "/*/" type comments for multiline comments
* // for single line comments
* Actionable comments should begin with TODO or FIXME

18) Whitespace
* [18.1, Up for debate] soft tabs set to 2 spaces
* [18.2] Place one space before the leading brace of a block
* One space before name of function or opening parens of a block
* Spaces in operators, they should not be const x=y+5
* [18.5, Up for debate] End files with a single newline character
* [18.6] Use indentation when making long method chains(more than 2) (use a leading dot to emphasize the line is a method call)
* Leave a blank line after blocks & before the next statement
* Do not pad blocks with blank lines
* Do not add spaces in parentheses, use (foo) not ( foo ), or within brackets [ 1, 2, 3 ] vs. [1, 2, 3]
* Add spaces within curly braces { clark: kent }
* Try to avoid lines of code longer than 100 characters (except for strings, as mentioned above)

19) Commas
* No leading commas
* [19.2, I like this, and think it's important] additional trailing commas for cleaner diffs, plus Babel will remove the additional trailing comma in transpiled code

20) Semicolons
* [20.1 AirBNB says Yup. What do you think?]

21) Type Casting & Coercion
* Type coercion at the beginning of a statement
* `this.reviewScore = 9`, use `const totalScore = String(this.reviewScore)` instead of a `toString()`
* Number or parse int, not new Number
* Always use a radix with parseInt (read more about this in the docs)
* again const hasAge = Boolean(age);

22) Naming Conventions
* [22.1, Up for debate] No single letter names
* use CamelCase, PascalCase only when naming constructors or classes
* No trailing or leading underscores as there is no concept of "private" methods/values in JavaScript
* Do not save references to this, use bind or arrow functions
* A filename should match exactly the name of its default export
