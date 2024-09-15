```javascript
// NOT PURE
let name = 'Karl'
function greet() {
	console.log(name)
}

greet() // Karl
name = 'Alan'
greent() // Alan
```

```javascript
// PURE
function greet(name) {
	return name
}

greet('Karl') // Karl
greet('Alan') // Alan
```
**Pure function**: 
1. Same result with calling function with same argument
2. Needs to have a return statement