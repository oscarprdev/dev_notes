```javascript
// WITH SIDE EFFECTS

let thesis = {
	name: 'Hello',
	date: 123
}

function renameName(newName) {
	thesis.name = newName;
	console.log('done')
}

renameName('Foo')
thesis // { name: 'Foo', date: 123 }
```

**Side effect** Reading data from outside of the function and manipulating it

```javascript
 // NO SIDE EFFECTS
 const thesis = { name: 'Hello', date: 123 }
 function renameThesis(oldThesis, newName) {
	 return {
		 name: newName,
		 date: oldThesis.date
	 }
 }
 
 const thesis2 = renameThesis(thesis, 'Foo')
 thesis // { name: 'Hello', date: 123 }
 thesis2 // { name: 'Foo', date: 123 }
```

