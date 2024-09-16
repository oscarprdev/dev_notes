```typescript
function listToDict<T>(
	list: T[], // List of T
	idGen: (arg: T) => string // Callback to get the id
): { [ k: string ]: T } => {
	const dict = { [k: string]: T } = {}
	
	list.forEach(el => {
		const dictKey = idGen(el) // Obtain the id using the callback
		dict[dictKey] = el // Store element under key
	})
	
	return dict
}
```

## <span style="color: #2196F3;">Generic constraints</span>

*The hability to specify the minimum requirement an a type parameter*

```typescript
// Extends on a generic type to add minimum requirement
function listToDict<T extends { id: string }>(
	list: T[],
): { [ k: string ]: T } => {
	const dict = { [k: string]: T } = {}
	
	list.forEach(el => {
		dict[el.id] = el // Now we can access to id without any callback
	})
	
	return dict
}
```