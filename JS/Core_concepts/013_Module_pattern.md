*Module pattern requires encapsulation
Runs as a singleton
Exposes minimal API

```javascript
// IIFE function
var workshop = (
	function Module(teacher) {
		var publicApi = { ask }
		return publicApi
		
		function ask(question) {
			console.log(teacher, question)
		}
	}
) ("Kyle")

workshop.ask("It's a module, right?")
// Kyle It's a module, right?
```

