*Intermediate layer between data and action, good for data validations*

*action ---> proxy ---> data

*keywords:*
1. *new Proxy(target, implementation)
2. *Reflect.get(target, property)*
3. *Reflect.set(target, property, value)*

```typescript
const user = {
	name: 'foo',
	age: 10
}

const userProxy = new Proxy(user, {
	get: (target, property) => {
		return Reflect.get(target, property)
	},
	set: (target, property, value) => {
		if (...validations...) {
			throw new Error('error message')
		}
		return Reflect.set(target, property, value)
	}
})

userProxy.name // 'foo'
userProzy.age = 12
```
