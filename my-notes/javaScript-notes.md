
#### "==" and "===" operators

```
0==false   // true, because false is equivalent of 0
0===false  // false, because both operands are of different type
2=="2"     // true, auto type coercion, string converted into number
2==="2"    // false, since both operands are not of same type
```

*)  !== operator is strict non equality operator, which will take type into consideration while comparing two variables or two values.


#### if statement

````
var userType;
if (userIsYoungerThan18) {
  userType = "Minor";
} else {
  userType = "Adult";
}
````
Similar to :

```
var userType = userIsYoungerThan18 ? "Minor" : "Adult";
```

```
if (userIsYoungerThan21) {
  serveDrink("Grape Juice");
} else {
  serveDrink("Wine");
}
```
Similar to :
```
serveDrink(userIsYoungerThan21 ? "Grape Juice" : "Wine");
```

#### Default Operator ||

|| can be used to  assign a default  value in case the value is not present.

```
// Truthy
var newGallery = 1;
var current = newGallery || 'false';
alert(current); // Alert returns 1
````

````
// Falsey
var newGallery = 0;
var current = newGallery || 'false';
alert(current); // Alert returns false
````


#### Classes

```
function Person(first, last, age, eyecolor) {
  this.firstName = first;
  this.lastName = last;
  this.age = age;
  this.eyeColor = eyecolor;
}

var myFather = new Person("John", "Doe", 50, "blue");
var myMother = new Person("Sally", "Rally", 48, "green");
```

#### Prototype Property

The JavaScript prototype property also allows you to add new methods to objects constructors:

```
function Person(first, last, age, eyecolor) {
  this.firstName = first;
  this.lastName = last;
  this.age = age;
  this.eyeColor = eyecolor;
}
````

```
Person.prototype.nationality = "English";

Person.prototype.name = function() {
  return this.firstName + " " + this.lastName;
};
```


#### modules

We can export code as modules  using module.exports = hasAnAttribute

File name: class-attributes-helper.js
```
function hasAnAttribute(object,attributeName){

  if('undefined' !== typeof(object[attributeName])){
    return true;
  }else{
    return false;
  }
}

module.exports = hasAnAttribute;

```
We can import a module const hasAnAttribute = require('../util/class-attributes-helper');

```
const hasAnAttribute = require('../util/class-attributes-helper');

if( hasAnAttribute(result,'access_token')) {
  return 'tete';
} else {
  return 'toto';
}
```

https://www.smart-words.org/quotes-sayings/english-idioms-commonly-used.pdf

https://tylermcginnis.com/beginners-guide-to-javascript-prototype/
