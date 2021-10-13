# Wyvernlang

## Semantic Requirements

### Return Statements

* `return if <bool>`
* `return <val> if <bool>`

### Object Operations and Access

* `<obj>.<prop> => <obj> | <val>`
* `<obj> + <obj> => <obj>` where the returned object contains all values of the two added objects
* `<obj> U <obj> => <obj>` same as above
* `<obj> N <obj> => <obj>` returned object only contains common values between the input objects
* `<obj> is <class> => <bool>`
* `<obj>.<prop>` equivalent to `. <obj> <prop>` by treating `.` as a function (see below)
  * It follows that `<obj>.<prop>.<prop>` is equivalent to `.. <obj> <prop> <prop>`

### Control Statements

* `if <bool>, then <stmt>;`
* `if not <bool>, then <stmt>;`
* `for key i in <list>, <stmt>;`
* `for value i in <list>, <stmt>;`

### Functions

* `define function myFnc(...) as <stmt>;`
* `fnc(<val0>, <val1>, ...); == fnc <val0> <val1> ... == <val0> fnc <val1>, ...;`
  * Note that the second and third possibilities differ in delimitation
* `define myFnc(...) as {if <val>, then statement[0]; else statement[1]; return;}`
  * Provides `myFnc(...) with statements = [{...}, {...}, ...];`

### Variables and Types

* `let myVar be <type> from <val>;` general variable declaration
* `let listVar be <list> from [<val00>, <val10>; <val01>, <val11>)];` 2-dimensional list declaration
* `assign <val> to <var>;` alternate form of `<var> = <val>;`
* `[...]` list or map of `<val>`
* `{...}` list or map of `<stmt>`
* `(...)` list or map of variable assignments (equivalent to function parameters)
* `<...>` list or map of `<type>` or `<class>`
* `<var> = <val0> if <bool>, else <val1>;` ternary qualifier

### Misc Language Features

#### Delimitation

* `,` level 0 delimeter
* `;` level 1 delimeter
* `;;` level 2 delimiter
* and so on
