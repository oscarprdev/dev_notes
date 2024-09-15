```javascript
let v;
typeof v // 'undefined'
v = "1";
typeof v // 'string'
v = 1;
typeof v // 'number'
v = true;
typeof v // 'boolean'
v = {};
typeof v // 'object'
v = Symbol();
typeof v // 'symbol'

v = null
typeof v // 'object'
v = function() {}
typeof v // 'function'
v = [1, 2, 3]
typeof v // 'object'
v = 42n
v = BigInt(42)
typeof v // 'bigint'
```

## <span style="color: #2196F3;">NaN</span>

```javascript
let age = Number(10) // 10
let nextAge = Number("n/a") // NaN
age - nextAge // NaN

nextAge === nextAge // false 

isNaN(nextAge) // true
isNaN("some string") // true  -> it's supposed to be false since it's string

// isNaN coerce the input to number first

Number.isNaN(nexAge) // true
Number.isNaN("some string") // false

```

*NaN is not equal to itself
NaN means: invalid number

## <span style="color: #2196F3;">Negative Zero</span>

```javascript
let rate = -0
rate === -0 // true

rate.toString() // "0" -> Not "-0"
rate === 0 // true -> Not false since rate is -0
rate < 0 // false
rate > 0 // false

Object.is(rate, -0) // true
Object.is(rate, 0) // false
```

## <span style="color: #2196F3;">Object.is</span>

```javascript
Object.is = function ObjectIs(x, y) {
	let xNegZero = isNegZero(x)
	let yNegZero = isNegZero(y)
	
	if (xNegZero || yNegZero) {
		return xNegZero === yNegZero;
	} else if (isItNaN(x) && isItNaN(y)) {
		return true;
	} else {
		return x === y;
	}
	
	function isNegZero(v) {
		return v === 0 && (1/v) === -Infinity; // (1/-0) is -Infinity
	};
	function isItNaN(v) {
		return v !== v // NaN is not equal to itself
	}
}
```
