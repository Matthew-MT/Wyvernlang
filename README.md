# Wyvernlang

## Semantic Requirements

### Return Statements

* `return if <bool>`
* `return <val> if <bool>`

### Context

* `[...]` list or map of `<val>`
* `{...}` list or map of `<stmt>`
* `(...)` list or map of variable assignments (equivalent to function parameters)
* `<...>` list or map of `<type>` or `<class>`

### Control Statements

* `if <bool>, then <stmt>;`
* `if not <bool>, then <stmt>;`
* `for key i in <list>, <stmt>;`
* `for value i in <list>, <stmt>;`
* `while <bool>, do <stmt>;`
* `do <stmt>, while <bool>;`

### Object Operations and Access

* `<obj>.<prop>` returns `<val> | <obj>`
* `<obj> + <obj>` returns `<obj>` where the returned object contains all values of the two added objects
* `<obj> U <obj>` returns `<obj>` same as above
* `<obj> N <obj>` returns `<obj>` returned object only contains common values between the input objects
* `<obj> is <class>` returns `<bool>`
* `<obj>.<prop>` equivalent to `. <obj> <prop>` by treating `.` as a function (see below)
  * It follows that `<obj>.<prop>.<prop>` is equivalent to `.. <obj> <prop> <prop>`

### Classes

* `define class myClass as {...};`
  * `{define myClass constructor(...) as <stmt>;}`
  * `{define <type> method myMethod(...) as <stmt>;}`
  * `{define <type> operator +(<val0>, <val1>) as <stmt>;}` operator overloading
  * `{define <type> context [<val0>, <val1>, ...] as <stmt>;}` context overloading

### Functions

* `define function myFnc(...) as <stmt>;`
* `fnc(<val0>, <val1>, ...);` equivalent to (for finite-ary functions only ((see spread operator below))) `fnc <val0> <val1> ...;` equivalent to (for 2-ary functions only) `<val0> fnc <val1>;`
* `define function complex(...)fnc(...) as <stmt>;`
  * Provides `complex(<val0>, <val1>)fnc(<val2>);` equivalent to `<val0> complex <val1> fnc <val2>;`
  * Note that the second possibility from trivial functions is absent for complex functions
  * Note that for the second possibility for complex functions to be used, function parameters must be `2,1,1,...` in order
* `define myFnc(...) as {if <val>, then statement[0]; else statement[1]; return;}`
  * Provides `myFnc(...) with statements = [{...}, {...}, ...];`

### Variables and Types

* `let myVar be <type> from <val>;` general variable declaration
* `let listVar be <list> from [<val00>, <val10>; <val01>, <val11>)];` 2-dimensional list declaration
* `assign <val> to <var>;` alternate form of `<var> = <val>;`
* `<val0> if <bool>, else <val1>` ternary qualifier
* An element from `<list>myValues` may be referred to as `<type>myValue[i]` by treating the trailing `s` as a qualifier
  * Unable to distinguish complex plurality, so `<list>myWolves` can only be accessed in this manner with `<type>myWolve[i]`, not `<type>myWolf[i]`

### Misc Language Features

#### Delimitation

* `,` level 0 delimeter
* `;` level 1 delimeter
* `;;` level 2 delimiter
* and so on

#### Indexed Values

* `...` spread/rest operator
  * `myFnc(...<list>);` applies each successive value in the list as a function parameter
  * `define function myFnc(...<list>) as <stmt>;` collect trailing parameters in a list
