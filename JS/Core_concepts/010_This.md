
*This keyword references the execution context for that call.

```javascript
function ask(question) {
	console.log(this.teacher, question) // Reference to the context where is called
}

var call1 = {
	teacher: 'Suzy',
	ask: ask
}

var call2 = {
	teacher: 'Kyle',
	ask: ask
}

call1.ask('Yes') // Suzy yes
call2.ask('Not') // Kyle not
```

```javascript
function userCreator(name, score) {
	const newUser = Object.create(userFunctionStore);
	newUser.name = name
	newUser.score = score
	
	return newUser
}

// not gonna work
const userFunctionStore() = {
	increment: function () {
		function add1() { this.score++ } // this -> global.this
		add1()
	}
}

// this with arrow functions*
const userFunctionStore() = {
	increment: function () {
		const add1 = () => { this.score++ } // this -> newUser 
		add1()
	}
}

const user1 = userCreator('Will', 3)
```

*Arrow functions not defined local bindings for this
This will be referenced to the first this founded on the upper [[008_Scope]]
