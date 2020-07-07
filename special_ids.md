# Special Identifiers
There is a general preference to make things callable identifiers instead of keywords as this makes tools more accessible to the user and allows the langauge to more easily be extended by the user.

## Context Specific
It's reccomended for the user to alias these with `using` or copy them with `let` or `const` as they get shadowed as the scope deepens.

### i - Input
This holds the input for the curren function
- At a global scope this holds command line args

### o - Output
This function returns to the previous scope
- At a global scope this also exits the program
- At a top-level `async` call, this kills the thread and puts the return value into the relevant future value
- This will stop instructions below it from being run if the jump is successful

## Globals
### empty `:: Empty`
Sentinel value empty (will eventually be replaced with a literal)
- Some languages call this `unit` or `undefined`
- Everything is an expression; this is a placeholder for lack of value

### print `:: Any -> Empty`
Writes a value to the console

### input `:: Empty -> Str`
Reads a line from console as a string

### if `:: [Bool, a, b] -> a()|b()|a|b`
If statment and/or ternary
- Pass functions as arguments and the corresponding one gets run
- Pass values as arguments and the corresponding values gets returned

### Str `:: Any -> Str`
String constructor, converts to string

### Num `:: Any -> Num`
Number constructor, converts to number

### Vars `:: Empty -> Empty`
Print identifiers for debugging VM (note these are mutiliated for performance reasons).

### Async ` :: (a -> b) -> (a -> (Empty -> b))`
Makes async wrappers for functions so that they can be run on other threads
- async returns an async wrapper to a given function
- calling the wrapper runs the original function in a new thread and returns a future functor
- calling the future functor joins the threads and eventually results in the original function return value
```
let load = (: (User -> UserData) ... );
let load_wrap : (User -> Future<SaveData>) = async(load);
let load_future : Future<SaveData> = load_wrap(user);
let data = load_future(); // load_future.get() in other langs
```
