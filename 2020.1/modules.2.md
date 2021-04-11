# Imports
SCL can currently only handle one file at a time. Modifying the VM to enable dynamic loading of additional bytecode files would be difficult. Thankfully the api is designed such that it could be replaced with a preprocessor/semantics.


## The API

```
// Import
let math = import('./math.scl')

// Export something
o("importing this file exports this value")
```


## The implementation
Copmiler replaces the import statement with the file's contents wrapped in a closure
```
let __math_scl_import = (:
	o({
		pi: 3.14,
		sqr: (: i + i ),
	})
)();
let math = __math_scl_import();
```
### Duplicate imports
Compiler will have to track what files have been imported already
```
// TODO demo, should be simple
```
### Cyclic imports
Will be in scope but uninitialized
```
// TODO demo showing use of local import
```
