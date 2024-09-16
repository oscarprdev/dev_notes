*Type checking against the type specified*

```typescript
interface Foo {
	id: string
	color?: 'red' | 'blue' | 'green'
}

const myFoo = { id: 'a', color: 'green' } as Foo
myFoo.color.substring(0, 2) // Error since color is undefined 

const myFoo2 = { id: 'a', color: 'green' } satisfies Foo
myFoo.color.substring(0, 2) // myFoo.color is 'green'
```
