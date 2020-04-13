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

## Variables
Variables are lexically scoped. 


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
