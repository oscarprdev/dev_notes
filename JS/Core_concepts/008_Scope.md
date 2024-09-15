```javascript
var teacher = 'Kyle'

function anotherTeacher() {
	var teacher = 'Suzy'
	console.log(teacher) // Suzy -> Scope of anotherTeacher
}

anotherTeacher()

console.log(teacher) // Kyle <- global scope
```

## <span style="color: #2196F3;">Hoisting</span>

*Taken variables/methods at compile time and define situations where they can be used

```javascript
// Hoisting variables
student;
teacher;
var student = 'you'
var teacher = 'kyle'

// Hoisting functions
var teacher = 'kyle'

getTeacher() // Kyle 

function getTeacher() {
	return teacher
}
```

