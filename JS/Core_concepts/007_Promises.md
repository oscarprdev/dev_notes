https://developer.mozilla.org/en-US/docs/Web/API

```javascript
	function display(data) {
		console.log(data) // 2
	}
	const futureData = fetch('...') // Network request
	futureData.then(display);
	
	console.log('First'); // 1
```

**fetch**: Method to do a network request on the web browser
**then**: Execute methods stored on **Microtask queue**
**Microtask queue**: List of methods from promises executed before **call stack queue**

```javascript
	function display(data) { console.log(data) }; 
	function printHello() { console.log('Hello')}; 
	function blockFor300ms() { ... };
	
	setTimeout(printHello, 0); // 4 -> call stack queue
	
	const futureData = fetch('...');
	futureData.then(display); // 3 -> microstack queue
	
	blockFor300ms(); // 1
	
	console.log('First'); // 2
```

>[!info] Order of execution
>1. Call stack (sync code)
>2. Microtask queue (promises)
>3. Call stack queue ([[006_Timers]])




