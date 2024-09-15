Syntactic sugar of functional-objects using **new** keyword [[011_New]]

```javascript
	class UserCreator {
		constructor(name, score) { 
			this.name = name;
			this.score = score;
		}
		
		increment() { this.score++ }
	}
	
	const user1 = new UserCreator('Eva', 1)]
	user1.increment()
```

