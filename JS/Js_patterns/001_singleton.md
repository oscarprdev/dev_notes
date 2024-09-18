```typescript
let instance;
class Foo {
	constructor(...) {
		if (instance) {
			throw new Error("Only 1 instance")
		}
		instance = this
	}
}

const connection = Object.freeze(new Foo(...))

export default connection;
```