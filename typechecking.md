/*
Preplan:
- Goal: prevent runtime type-errors
- Goal: minimally invasive
- Not goal: gaurantee "intended use"

Plan:
- Only functions/macros have types (operators are shortcuts for functions)
- Will need to implicitly polymorphise 
- User has to explicitly allow runtime typerrors
Structs: 
- Like interfaces in Java
- compatible types must have "at least" these members
- Auto: deduced/compatible type
- 
*/



struct Coord = {
	x: Auto,
	y: Auto,
};

let f = (:(Coord->Auto)
	arg.x + arg.y 
	// compiles to: (arg.x).__op+(arg.y)
);
...
