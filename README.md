# Prototypal-Inhertiance in my own words

```
// Every object has a prototype with native properties and methods
var func = function(){};
var arr = [];
var obj = {};

// console.log(func);
// console.log(arr);
// console.log(obj);

// When JS can't find a property or method on the object, it will go up the prototype chain and look at its prototype to try to find it. 

// Which is why we can use someArray.push() on any array for example, as arrays are objects and have a prototype.

// Constructor function 
function Person(firstname, lastname) {
  console.log(this); // Empty object created by 'new,' this' points to here and object is returned
  this.firstname = firstname;
  this.lastname = lastname;
}

john = new Person('John', 'Doe')
console.log(john);

// An empty object, exists on all functions called prototype 
// When objects are created from a constructor function, this is those objects' prototype:
// Person.prototype

// All objects created from that function share the same prototype object, which means because of JS looking down the prototype chain, it will find the method to be used.
// Called differential inheritance because nothing is copied, only 'linked'. 
Person.prototype.someProp = 'Some Property';

// Proof -- These are the same object: 
console.log(Person.prototype);
console.log(john.__proto__);

// The prototype of Person.prototype is that base object with native method
// Proof
console.log(Person.prototype.__proto__);
console.log(john.__proto__.__proto__);

// Lastly, JS can use reflection
// JS is smart enough to search john's prototype, even though the hasOwnProperty method exists on the prototype of that prototype. 
console.log(john.__proto__.hasOwnProperty('someProp')); // true 


// We can use a method that exists on the prototype due to differential inheritance. 
console.log(john.toString());
console.log(john.__proto__.__proto__.hasOwnProperty('toString')); // true


```
