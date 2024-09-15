
```typescript
// | declares either Foo or Bar type
type Foo = [1, 2, 3]
type Bar = [3, 4, 5]
type FooBar = Foo | Bar 

let fooBar: FooBar = [1, 2, 3] // Valid
let fooBar: FooBar = [3, 4, 5] // Valid
let fooBar: FooBar = [5, 6, 7] // Invalid

// & declares both types must be valid at same time
type A = { x: string }; 
type B = { y: number }; 
type AB = A & B; 

let ab: AB = { x: 'foo', y: 2 } // Valid
let ab: AB = { x: 'foo' } // Invalid
let ab: AB = { y: 2 } // Invalid
```

```typescript
const success = ['success', { name: 'Foo' }] as const;
const error = ['error', new Error("Error")] as const;
const outcome = [success, error]

const [first, second] = outcome
if (first === 'error') {
	second // error
} else {
	second // success
}
```

