```typescript
class Foo {}
class Bar {}

type FooOrBar<T> = T extends 'foo' ? Foo : Bar // Terniary to return specific type

let foo = FooOrBar<'foo'> // Foo
let bar = FooOrBar<'xxx'> // Bar
```

## <span style="color: #2196F3;">Extract</span>

*Find types that are equivalent on a specific type*

```typescript
type Foo = {
	'a', 
	'b',
	{ a: string }
}

type Foo1 = Extract<Foo, string> // 'a' | 'b'
type Foo2 = Extract<Foo, { a:string } // { a: string }
```

## <span style="color: #2196F3;">Exclude</span>

*Exclude what match the type*

```typescript
type Foo = {
	'a', 
	'b',
	{ a: string }
}

type Foo1 = Exclude<Foo, string> // { a: string }
type Foo2 = Exclude<Foo, { a:string } // 'a' | 'b'
```

## <span style="color: #2196F3;">Infer</span>

*Extract the type inferred from a generic type*

```typescript
type UnwrappedPromise<P> = 
	P extends PromiseLike<infer T> // If P matches then return the T type
		? T
		: P
		
type foo = UnwrappedPromise<Promise<string>> // T = string
```

## <span style="color: #2196F3;">Constraints Infer</span>

```typescript
type Foo<T> = T extends readonly [
	infer S extends string // Allow to return the value if extends to string
] ? string : never

const t1 = ['foo', 1, 2] as const
const t2 = [1, 2] as const

let first: Foo<typeof t1> // string
let second = Foo<typeof t2> // never
```
