Mostly inspired by python syntax... Was my idea for what would be shortest possible closure syntax. Was told it's kinda had to read tho so prob gonna switch to curlies or sth.


```
////////////////////////////
// before
////////////////////////////
// Single expression closure (no semi needed)
let add5 = (: i + 5 );

// Multi-expression closure
let sum = (:
	let n = i, total = 0;
	while((: n < max ), (:
		n -= 1;
		total += n;
	));
	o(total);

let seven = (: i + 4 )(3);

////////////////////////////
// Automatic Semicolon insertion
// + Implicit returns
////////////////////////////

let add5 = (: i + 5 )
let sum = (:
	let n = i, total = 0
	while((: n < max ), (:
		n -= 1
		total += n
	))
	
	// return total
	total
)

let seven = (: i + 4 )(3);

////////////////////////////
// New closure syntax
////////////////////////////

// Single-line example
let add5 = : i + 5

// Multi-line example
let sum = :
	let n = i, total = 0
	while (: n < max, :
		n -= 1
		total += n
	)
	total

// Note: can still use same syntax as before	
let seven = (: i + 4 )(3);
```
