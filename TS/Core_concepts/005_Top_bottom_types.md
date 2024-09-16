## <span style="color: #2196F3;">Top types</span>

>[!danger] Top types
>Accept anything
>- Any
>- Unknown

```typescript
try {
	doSomething()
} catch (e: unknown) { // Use of unknown
	if (e instanceof Error) {
		e //		
	} else if (typeof e === 'string') {
		e //
	} else {
		console.log(e)
	}
}
```

**tsconfig.json** = *useUnknownInCatchVariables: true


## <span style="color: #2196F3;">Almost top types</span>

>[!danger] Almost Top types
>All casted values except primitives
>- Object

```typescript
let val: object = { status: 'ok' }
val = 'foo' // ERROR: string is not an object
val = null // ERROR*: null is not an object
val = () => 'ok' // OK: functions ar objects
```

**tsconfig.json** = *strictNullChecks: true

>[!danger] Almost Top types
>All values expect null and undefined
>- {}

```typescript
let val2: {} = 4 // Empty object type
val2 = 'abc' // OK
val2 = new Date() // OK
val2 = 4 // OK
val2 = null // Error
val2 = undefined // Error

// Remove null and undefined with intersection type 'T & {}' 
type foo = string | number | null | undefined
type bar = foo & {} // string | number
type foo2 = NonNullable<foo> // string | number
```

## <span style="color: #2196F3;">Bottom types</span>

>[!danger] Bottom types
>Do not accept any value, represent an impossibility 
>- never

```typescript
class Car { ... }
class Boat { ... }
class UnreacheableError extends Error {
	constructor(_: never, message: string) {
		super(message)
	}
}

let val: Car | Boat = ...

if (val instanceof Car) { ... }
else if (val instanceof Boat) { ... }
else {
	// val here will have NEVER type on compile time
	throw new UnreacheableError(
		val,
		"Error message"
	)
}
```

## <span style="color: #2196F3;">Unit types</span>

*Only one possible value

