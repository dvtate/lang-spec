# General Syntax
## Lexical Types
- Builtin operators
  - infix
  - prefix
  - postfix
- Literals
  - macros: `(: _________ )`
  - JSON:
    - objects
    - lists
    - strings
  - enumerated constants
    - null: invalid reference
    - empty (== undefined): default value for variables || no value passed
- Identifiers

## Syntactic Components

### Expression
- Combination of literals, identifiers, macros and/or operators resulting in a single value
- for example: `1 + 2`, `"fff"`, `a > 2 && !b`, etc.

### Statement
- A single expression with a terminating `;` for added clarity

### Macro
- `(: ___ )` where `___` is zero or more expressions

### Object
- mimicing JavaScript object syntax
- syntax: `{ key : value, key : value, ...}`
  - enclosed in braces
  - keys and values separated by `:`
  - key-value pairs separated by `,`
  - no limit to number of pairs
  - `key` is a string or identifier, 
  - `value` is an expression

### List
- Mimicing javascript object syntax
- syntax: `[ expression, expression, ...]`
  - zero or more expressions enclosed in square brackets and separated by commas

### Strings
- single or double quoted text-sequences
- can span multiple lines

### Numbers
- Valid Number representation
- 0x*, 0b*, 0* integer representations
- decimals, `e`, etc.

### Parenthesized Expressions
- parenthasis enclosed expression to indiciate order of operations

### Infix operators
- left and right expression operands

### Macro Invocation
- Macro literal/Identifier followed by a parenthesized expression containing argument
- ie: `f(1)`, `(: (arg + 1) * 2 )(66)`

### Indexing/Member Request
- bracket notation. Derived list/object followed by bracket enclosed expresssion resolving to a number/string.

### Dot operator
- object . identifier

### Varaiable declaration
- `let` followed by a list of comma-separated identifiers with optional initializations
- `const` followed by a list of comma-separated identifiers with optional initializations



## Builtin Structures
### conditionals
#### Ternary
- Syntax: `cond ? v0 : v1`

### Loops
#### While
syntax: `while <macro cond> <macro action>`
```
while (: a > 5) (:
  a = a - 1;
);

let n = 0;
let cond = (: n < 10 );
let action = (:
  n = n + 1;
  print(n);
);
```


## Keywords
- `let` 
- `if`
- `while`
- `for`
