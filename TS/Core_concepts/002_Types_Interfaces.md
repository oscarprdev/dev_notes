```typescript
type Foo = string | number

interface Bar {
	foo: Foo
}
```

## <span style="color: #2196F3;">Open interfaces</span>

```typescript
declare global {
	interface window { // Asigning someProp to window
		someProp: number
	}
}

window.someProp
```

## <span style="color: #2196F3;">Recursive types</span>

```typescript
type Foo = number | Foo[] // Array of same type, array of nested numbers

const nums: Foo = [1,2, [3, 4, [5, 6]]] // Nested numbers
```

## <span style="color: #2196F3;">Type queries</span>

```typescript
type Foo = {
	name: string,
	bar: {
		foo: number
	}
}

let some: Foo['bar'] // { foo: number }
```

## <span style="color: #2196F3;">Keyof - typeof</span>

```typescript
const foo {
	name: 'Os',
	year: 2000
}
type Test1 = typeof foo // { name: string, year: number } -> Type of object
type Test2 = keyof typeof foo // 'name' | 'year' -> Keys of object
```

## <span style="color: #2196F3;">Type guards</span>

```typescript
type Card = any;

function isCard(card: any): card is Card { // returning a boolean and type Card
	return (
		card && typeof card === 'object' && typeof card['name'] === 'string'
	)
}

if (isCard(card)) {
	card // Card
}
```
