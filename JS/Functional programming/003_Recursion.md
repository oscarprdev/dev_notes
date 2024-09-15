## <span style="color: #2196F3;">Iteration</span>
1. Imperative
2. Looping
3. Stateful
```javascript
function sum(numbers) {
	let total = 0
	for (i = 0; i < numbers.length; i++) {
		total += numbers[i]
	}
	
	return total
}

sum([0,1,2]) // 3
```
## <span style="color: #2196F3;">Recursion</span>
1. Functional
2. Self-referential
3. Stateless

```javascript
function sum(numbers) {
	if (numebrs.length === 1) {
		return numbers[0]
	} else {
		return numbers[0] + sum(numbers.slice(1))
	}
}

sum([0,1,2]) // 3
```
