*Remove all properties that does not match with the type specified*

```typescript
type FilteredKeys<T, U> = {
	[P in keyog T]: T[P] extends U ? P : never
}[keypof T] & keyof T
```
