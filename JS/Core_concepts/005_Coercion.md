*Implicit conversion of a value from one data type to another.

## <span style="color: #2196F3;">toString</span>

```javascript
2 // "2"
-0 // "0"

[] // "''"
{} // [Object, Object]
``` 

## <span style="color: #2196F3;">toNumber</span>

```javascript
"" // 0
"0" // 0
".0" // 0
"." // NaN

false // 0
true // 1
null // 0
undefined // NaN
```

## <span style="color: #2196F3;">Boolean</span>

```javascript
Boolean(undefined) // false
Boolean(null) // false
Boolean({}) // true
```

## <span style="color: #2196F3;">Cases of coercion</span>

```javascript
	if (value) { ... } // Bad
	if (!!value) { ... } // Correct
	if (Boolean(value)) { ... } // Correct
	
	if (value.length) { ... } // Bad
	if (value.length > 0) { ... } // Correct
```

## <span style="color: #2196F3;">Corner cases</span>

```javascript
Number("") // 0
Number(" \t\n") // 0
Number(null) // 0
Number(undefined) // NaN
Number([]) // 0
Number([1,2,3]) // NaN
Number([null]) // 0
Number([undefined]) // 0
Number({})

String(-0) // "0"
String(null) // "null"
String(undefined) // "undefined"
String([null]) // ""
String([undefined]) // ""

Boolean(new Boolean(false)) // true
```