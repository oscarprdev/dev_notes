```typescript
function listToDict<T>(
	list: T[], // List of T
	idGen: (arg: T) => string // Callback to get the id
): { [ k: string ]: T } => {
	const dict = { [k: sring]: T } = {}
	
	list.forEach(el => {
		const dictKey = idGen(el)
		dict[dictKey] = el // Store element under key
	})
	
	return dict
}
```
