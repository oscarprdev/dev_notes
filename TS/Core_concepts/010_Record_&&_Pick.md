## <span style="color: #2196F3;">Mapped type</span>

```typescript
type Foo = {
	cherry: 'a',
	apple: 'b'
}

type MyRecord = { [FruitKey in 'cherry' | 'apple']: Foo }

function useFoo(foo: Foo) {
	foo.apple // Allowed
	foo.cherry // Allowed
	foo.other // Error, other does not exist on Foo
}
```

## <span style="color: #2196F3;">Record</span>

```typescript
type Foo = {
	cherry: 'a',
	apple: 'b'
}

type MyRecord = Record<'cherry' | 'apple', Foo> // Same as mapped type above

function useFoo(foo: MyRecord) {
	foo.apple // Allowed
	foo.cherry // Allowed
	foo.other // Error, other does not exist on Foo
}
```

## <span style="color: #2196F3;">Pick</span>

```typescript
type Foo = {
	cherry: 'a',
	apple: 'b',
	other: 'c'
}

type MyFoo = Pick<Foo, 'cherry' | 'apple'> // Select the specific types

function useFoo(foo: MyFoo) {
	foo.apple // Allowed
	foo.cherry // Allowed
	foo.other // Error, other has not been "picked" from Foo
}
```

## <span style="color: #2196F3;">Pick with Exclude</span>

```typescript
type Foo = {
	cherry: 'a',
	apple: 'b',
	other: 'c'
}

type MyFoo = Pick<Foo, Exclude<keyof Foo, 'other'>>  

function useFoo(foo: MyFoo) {
	foo.apple // Allowed
	foo.cherry // Allowed
	foo.other // Error, other has not been "picked" from Foo
}
```
