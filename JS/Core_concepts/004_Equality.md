	== checks value (loose equality) // Not correct
	=== checks value and type (strict equality) // Not correct
	
	== Allows coercion (types different)
	=== Disallows coercion (types same) 


>[!info] How works ==
>1. If types are the same: ===
>2. If null or undefined: equal
>3. if non-primitives: toPrimitive
>4. Prefer: ToNumber

```javascript
// undefined == null -> true

let a = { foo: null }
let b = {}

// Bad
if (
	(a.foo === null || a.foo === undefined) && 
	(b.foo === null || b.foo === undefined)
) { ... }

// Correct
if (a.foo == null && b.foo == null) { ... }

```

## <span style="color: #2196F3;">Corner cases</span>

```javascript
[] == ![] // true

// [] == false
// "" == false
// 0 == false
// 0 === 0 -> true

```

>[!danger] When avoid ==
>1. with 0 
>2. with "" / " "
>3. == true / == false

