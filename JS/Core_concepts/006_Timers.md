```javascript
	function printHello() { console.log('Me second') }; // 2
	
	setTimeout(printHello, 1000)

	console.log('Me first') // 1
```


```javascript
	function printHello() { console.log('Hello') }; // 3
	function blockFor1Sec() { ... }
	
	setTimeout(printHello, 0); // callback queue
	blockFor1Sec(); // 1
	console.log('Me first'); // 2
```

**Callback queue**: List of functions stored in order waiting for be executed once **call stack** and **global execution context** is empty.
**Event loop**: callback queue functions being stored on the call stack

>[!danger] Timers
>- The timer declared on second argument of setTimeout declares the order to set the function on the callback queue

