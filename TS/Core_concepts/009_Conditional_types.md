```typescript
class Foo {}
class Bar {}

type FooOrBar<T> = T extends 'foo' ? Foo : Bar // Terniary to return specific type

let foo = FooOrBar<'foo'> // Foo
let bar = FooOrBar<'xxx'> // Bar
```
