# ES6 Javascript Tutorial For Beginners

> My basic guide for javascript and ES6 syntax comparison with sample code.

## Syntax Covers

1. Scope variables
2. Concatination
3. Object literals
4. Object Deconstructuring
5. Arrow functions
6. Object literals with `this` keyword
7. Constructor functions/ES6 Class syntax

### Scope variables

```
//code:1 javascript
var names = ["jino", "james", "edward"];
var myMoney = 20;
var myMoney = 10; //you can redaclare number multiple times :-( bad approach
console.log(number);
```

Redeclaring variables will give you future problem.

```
//code:2 javascript
var myName=500; //global variable money  
function mySelfFunc(){  
	var myMoney = "jino";
	alert(myName);  //you can access global variable inside `mySelfFunc` function
}  
console.log(myMoney); //but you cannot access this variable from `mySelfFunc` function
```

//ES6 syntax

There are two ways to declare a variable in ES6 they are the `let` and `const`

let and const are block scopes this means you cannot use variables anyware outside brackets take a look below example code

```
for(let i = 0; i < names.length; i++){
	console.log(names[i]);
}

console.log(i) //since let and const are blocked scopes it will give an error, but if you change `let i = 0;` to `var i = 0;` you can access it outside for loop but this is a bad practice.
```

### Concatination 

```
//code:1 javascript
//concatinate using `+`

var occupation = "Developer";
console.log("My occupation is a "+occupation); 
```

```
//code:2 ES6
//concatinate string template by backticks (`)

let occupation = "Quality Assurance Engineer";
var employee = {name: 'Jino Lacson'};
console.log(`I'am ${employee.name.toUpperCase()} my occupation is ${occupation}`);
```

### Object Literals 

```
//code:1 javascript
//old way of returning objects

function getEmployee(title,name,department){
	return{
		title: title,
		name: name,
		department: { department : department}
	}
}
console.log(getEmployee("Developer","Jino", "IT dep"));
```

```
//code:2 ES6
//clean way of returning objects

function getEmployee(title,name,department){
	return{
		title,
		name,
		department: { department }
	}
}
```

### Object Deconstructuring

```
//code:1 javascript
//deconstruct by dot using notation (.)

var employeeDetails = {
	firstName: "Jino",
	department : "IT"
};
console.log(employeeDetails.name)
```

```
//code:2 ES6
//deconstruct by using brackets ({})

const employeeDetails = {
	firstName: "Jino",
	department : "IT",
	progLanguages: ["C++", "Java", "C#"]
};
const {firstName, progLanguages} = employeeDetails;
console.log(firstName, progLanguages);
```

### Arrow functions

```
//code:1 javascript
//old way javascript function

function mentorGoals(goal){
	console.log(goal+"to establish and assist good programming practices for mentees");
}
mentorGoals("A mentor goal is: ");
```

```
//code:2 ES6
//using arrow function (=>)

const mentorGoals = (goal) => {
	console.log(`${goal} to establish and assist good programming practices for mentees`);
};
mentorGoals("A mentor goal is: ");
```

```
//code:3 ES6
//using arrow function (=>) in a single line code

const mentorGoals = (goal) => console.log(`${goal} to establish and assist good programming practices for mentees`);
mentorGoals("A mentor goal is: ");
```

### Object literals with `this` keyword 

```
//code:1 javascript
//problem in object literals 

var employeeDetails = {
 	firstName: "Jino Lacson",
 	occupation: "Developer",
 	myBio: function(){

 		//you can use `employeeDetails.firstName`
 		console.log("Hello my name is "+ this.firstName + " and i am a" + employeeDetails.occupation)

 		//Since `myDuties` is not a part of object `employeeDetails` you need to re-assign `this` to other variables
 		var self = this;

 		var myDuties = function(){
 			//using `self.occupation` will address undefined issues
 			console.log("My duty as a "+ this.occupation + " is to maintain and develop systems") 
 		}

 		myDuties();//will give you undefined duty :-( so needed to use `self.occupation` inside `myDuties` function
 	}
};
employeeDetails.myBio();
```

```
//code:2 ES6
//Using es6 no need to use `let self = this;` :-)

const employeeDetails = {
 	firstName: "Jino Lacson",
 	occupation: "Developer",
 	myBio: function(){

 		//you can use `${employeeDetails.firstName}`
 		console.log(`Hello my name is "${employeeDetails.firstName}" and i am a "${employeeDetails.occupation}"`)

 		//No need to re-assign `this` 
 		//let self = this;

 		const myDuties = function(){
 			console.log(`My duties as a "${employeeDetails.occupation}" is to maintain and develop systems`)
 		};

 		myDuties();//i can view now my duty :-)
 	}
};
employeeDetails.myBio();
```

### Constructor functions/ES6 Class syntax 

```
//code:1 javascript
function ClassEmployeeDetails(firstName, occupation, department, languages){
	this.firstName = firstName;
	this.occupation = occupation;
	this.department = department;
	this.languages = languages;
}

//console.log(new ClassEmployeeDetails("Jino Lacson", "Developer", "IT", ["C++, C#, Java"]));

//You can extend `ClassEmployeeDetails` with prototypes like:
ClassEmployeeDetails.prototype.myLanguages = function(){
	console.log(this.languages);
};

//console.log(new ClassEmployeeDetails("Jino Lacson", "Developer", "IT", ["C++, C#, Java"]).myLanguages());

function Developers(field, firstName, occupation, department, languages){
	//Call ClassEmployeeDetails()
	ClassEmployeeDetails.call(this, firstName, occupation, department, languages);
	this.field = field;
}

console.log(new Developers("Focusing Frontend", "Erik", "Designer", "IT", "Js"));
console.log(new Developers("Focusing backend", "Jino", "Developer", "IT", "C"));
```

```
//Code:2 ES6

class ClassEmployeeDetails{
	constructor (firstName, occupation, department, languages){
		this.firstName = firstName;
		this.occupation = occupation;
		this.department = department;
		this.languages = languages;
	}

	myLanguages(){
	  console.log(this.languages)
	}
}

//console.log(new ClassEmployeeDetails("Jino Lacson", "Developer", "IT", ["C++, C#, Java"]).myLanguages());

class Developers extends ClassEmployeeDetails{
	constructor (field, firstName, occupation, department, languages){
		super(firstName, occupation, department, languages);//Call base class = ClassEmployeeDetails.call(this..
		this.field = field;
	}

	myField(){
	  console.log(this.field)
	}
}

//console.log(new ClassEmployeeDetails("Jino Lacson", "Developer", "IT", ["C++, C#, Java"]).myLanguages());
//console.log(new Developers("Focusing Backend","Jino Lacson", "Developer", "IT", ["C++, C#, Java"]).myField());
```

Done.