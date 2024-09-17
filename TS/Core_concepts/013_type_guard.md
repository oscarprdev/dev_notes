```typescript
export function isTypedArray<T>(
	arg: unknown[], 
	guard: (toTest: unknown) => toTest is T
): arg is T[] {
	return Array.isArray(arg) && arg.every(guard)
}
```

```typescript
export function isTeam(arg: unknown): arg is Team {
	return (
		typeof arg === 'object'
		&& 'name' in arg
		&& typeof arg.name !== 'undefined'
	)
}
```