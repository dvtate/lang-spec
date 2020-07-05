# async/multi threading planning
The VM in it's current state has the infastructure requred to handle this, including an event loop.

## basic macro syntax:
- literal: `(: )`
- input/argument: i
- output/return: o
	- when called returns to call site and puts argument on top of stack
- Unlike JS, there is no syntactic distinction between sync and async function definitions
	- this only changes way functions are invoked


## definitions
```
// Basic definition
let add2 = (: o(i + 2); );
// ASI + Implicit returns
let add3 = (: i + 3 );
```

## Invoke
### Immediately get return value
```
print(add2(12)); // 14
```
### Get value asynchroniously
```
// call add2 in another thread
let result = async(add2)(12);

// do some other stuff...

// await result
print(result()); // 14
```

### Get value in parallel
```
// call add2 in another process
let result = parallel(add2)(12);

// do some other stuff...

// await result
print(result()); // 14
```


## Some examples
### Equiv to JS window.setTimeout
```
// equiv to window.setTimeout
const set_timeout = (:
	using args = i; // rename i to args
	async((:
		sleep(args.delay);
		args.fun(args.i);
	));
);

// Invoke
set_timeout({ 
	fun: (: print('Hello, ' + i) ),
	delay: 6000,
	i: 'Steve'
});
```

### Creating a callback wrapper for an async call
```
// takes a function and returns a closure
// this is equiv to covnerting a promise to a fn with callback
const wrap_callback = (:
	using fn = i;
	// return a closure
	o((:
		using args = i;
		async((: args.callback(fn(args.i)) ));
	));
);

//
const sql_cb = wrap_callback(sql.query);
sql_cb({
	i: ['SELECT * FROM users WHERE name=?;', 'Steve'],
	callback: (: 
		print('We have ' + i.size() + ' users named Steve') 
	),
});
```

### Await the result of a callback
```
const users = (:
	// pass closure's return as callback function so that we return when it's called
	sql_cb({ i: ['SELECT * FROM users'], callback: o });
	
	// freeze execution of this thread until return or other trigger received
	halt();
)();

print('We have ' + users.size() + ' users');
```

### More
https://github.com/dvtate/lang-spec/blob/master/example_syntax/2020.7.4


# handling errors
- for sync calls errors go backwards through call stack until they are handled
- for async and parallel calls, invoking call-stack could have changed since they were invoked, so their backtrace will be shorter and exceptions will result in death of thread/process they're running in. 
