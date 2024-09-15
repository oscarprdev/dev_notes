Functions that receives functions as parameters or return functions.

```javascript
function copyArrayAndManipulate(array, instructions) {
	const output = [];
	for (let = 1; i < array.length; i++) {
		output.push(instructions(array[i]));
	}

	return output;
};

function multiplyBy2(input) { return input * 2 };

const result = copyArrayAndManipulate([1, 2, 3], multiplyBy2)
```

**Callback**: Functions inserted on functions as parameters.
**Call stack**: Place where memory is stored during functions executions.

	- multiplyBy2() <- Once executed (3 times), is stored on the scope of parent fn.
	- copyArrayAndManipulate() <- Once executed, stored on global() scope.
	- global()

## <span style="color: #2196F3;">First class functions</span>

A function that is used as input on another function