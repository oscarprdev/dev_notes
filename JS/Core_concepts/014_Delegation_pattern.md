*Object with methods assigned to other method in order to share functionalities between them referencing **[[010_This]]** to same entity

```javascript
var AuthController = {
	authenticate() {
		server.auth(
			this.username, // Reference to LoginFormController
			this.password  // Reference to LoginFormController
		) { 
			this.handleResponse.bind(this) // Reference to AuthController
		}
	},
	handleResponse(res) {
		if (!res.ok) this.displayError(res.msg) // Reference to LoginFormController
	}
} 

var LoginFormController = Object.assign(
	Object.create(AuthController), // AuthController unified to LoginFormController
	{
		onSubmit() {
			this.username = this.$username.value()
			this.password = this.$password.value()
			this.authenticate() // Reference to AuthController
		},
		displayError(msg) { alert(msg) }
	}
)
```
