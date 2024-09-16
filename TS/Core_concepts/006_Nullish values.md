*null*: empty values explicity setted as empty (null)
*undefined*: values not defined yet

```typescript
type val = {
	foo?: string // undefined | string
	bar: null | string // null | string
}
```

## <span style="color: #2196F3;">Not null assertion</span>

*Check the possibility to be undefined

```typescript
type Foo = {
	fruits?: { a: string}[]
}
const foo: Foo = {} // Foo type but empty for now

foo.fruits.push({ a: 'a' }) // Error: fruits does not exist on foo value yet
foo.fruits!.push({ a: 'a' }) // Throw an error: USEFUL ON TESTS

// Real world usecase instead of using !
const { fruits } = foo
if (fruits) {
	fruits.push({ a: 'a' })
} else {
	// Error handling
}
```

## <span style="color: #2196F3;">Definite asignment assertion</span>

*Remove undefined values asserting it will not be undefined anymore

```typescript
class Foo {
	foo!: string // With ! is not throwing an error
	
	constructor() {
		 new Promise(() => {
			 this.foo = 'foo' // Async variable asignment
		 })
	}
}
```

*tsconfig.json: StrictPropertyInitialization = true
