*A way to insert and populate declarations on same interface used externally

```typescript
// data/foo
class Foo {
	add(): void {}
}

declare module '../path/index' { // Inserting the interface on the path
	export interface TypeShared {
		foo: Foo
	}
}

// data/foo2
class Foo2 {
	add(): void {}
}

declare module '../path/index' { // Inserting the interface on the path
	export interface TypeShared {
		foo2: Foo2
	}
}

// path/index
export interface TypeShared {} // Exporting the interface empty

export function fetchSomething(
	arg: keyof TypeShared & string, // Asigning the keyof & string to arg
	id: string
)

// index
export { fetchSomething } from './path'

const doit = fetchSomething('foo', '1') // Able to use 
the key of the Foo
const doit = fetchSomething('foo2', '2') // Able to use the key of the Foo2
```

