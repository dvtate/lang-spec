#async/muli threading


## basic macro syntax:
- literal: `(: )`
- input/argument: i
- output/return: o
	- when called returns to call site and puts argument on top of stack

## definitions
```
let sync_fn = (: o(i + 2) )
let async_fn = (async: o(i + 2))
```

## (sync) use return value 
`print(sync_fn(12))`


## (async) get return value via callback
async function returns another async function
this function is called with result when function finished
which you can pass a callback to in order to
``` 
async_fn(12)((: print(i) ));
async_fn(12)(print);
```

## equivalent to `await` syntax
```
let await = (: i(o) );
print(await(async_fn(12)));
```

## Parallel macro
- `(parallel: )` ?
- all references to outside values must be immutable
- Likely automatic optimization determined at compile time
- Depends on input so should be replaced at invocation


# handling errors
errors go backwards through call stack until they are handled, even for async functions**
- is this possible? probably not, esp w/ parallel fxns
