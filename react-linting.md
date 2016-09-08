** These ES Lint rules are written for the ES lint react plugin

1) Basic Rules
* One react component per file, multiple stateless/pure components allowed
* Do not use `React.createElement`

2) Class vs React.createClass vs stateless
* Use ES6 syntax of class Thing extends React.Component over React.createClass
* If there is no state prefer regular old functions (not arrow), don't make a class if you don't need it

3) Naming
* Use .jsx extension for React Components
* Use Pascal Case for filenames, components etc.. and camelCase for the instances of react Components
* Filename === Component Name, except for index.jsx

4) Declaration
* Do not use displayName for naming components (example in docs but not sure if this is something we really need to worry about here)

5) Alignment
* If props fit on one line, keep it on one line
* Children get indented normally

6) Quotes
* Always use double quotes for JSX attributes `ex: <Foo bar="bar" />` as opposed to single quotes as JSX cannot contain escaped quotes. Everything else should still be single quotes (JSX attributes are mirroring HTML attributes here)

7) Spacing
* Always use a single space in self closing JSX tab ex: `<FOO />`
* Do not pad JSX curly braces with spaces! `<FOO bar={baz}>`

8) Props
* Always use camelCase for prop names
* [Up for debate]Omit the value of a prop when it is explicitly true
```
// bad
<Foo
  hidden={true}
/>

// good
<Foo
  hidden
/>
```
* always include alt on img tags
* Do not use works like image, photo, or picture in image alt tag because the screenreader already announces images as that, don't need to be redundant
* (Skipping something on ARIA roles because I don't think we really use them)
* Do not use accessKey
* Do not use an array index, but rather a unique ID as a KEY prop

9) Refs
* Use ref callbacks, not strings
```
// bad
<Foo
  ref="myRef"
/>

// good
<Foo
  ref={ref => { this.myRef = ref; }}
/>
```

10) Parentheses
* Return statements should be wrapped in Parentheses when they span more than one line, if just one line you can leave them out

11) Tags
* Always self close tags unless they have children
* If your component has multiline properties that must be split up, close them on a new line

12) Methods
* Use arrow functions to close over local variables
```
function ItemList(props) {
  return (
    <ul>
      {props.items.map((item, index) => (
        <Item
          key={item.key}
          onClick={() => doSomethingWith(item.name, index)}
        />
      ))}
    </ul>
  );
}
```
* [Code examples from Airbnb could be helpful with this one] Bind event handlers for the render method in the constructor of a component rather than within a return statement (otherwise, render will create a brand new function on every render)
* Do not use an underscore prefix  --> Everything should be treated as public
* Return a value in render statements always

13) Ordering
* React Docs have a list of ordering to be used

14) isMounted
* Do not use isMounted, it is an anti=pattern and not available within ES6 classes (on its way to being depracated)
