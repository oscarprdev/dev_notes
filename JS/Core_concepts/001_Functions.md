**Thread of execution**: In JS only 1

```javascript
const num = 3;

function multiplyBy2(inputNumber) {
	const result = inputNumber*2;
	return result;
}

const output = multiplyBy2(num) // 6
```

**Parameter**: inputNumber
**Argument**: value of inputNumber
**Execution context**: Scope of function stored on call stack
**Local memory**: Scope of memory inside a function

>[!info] Return
>- Find location of constant **result**  to return the value located in local memory of **multiplyBy2**
>
