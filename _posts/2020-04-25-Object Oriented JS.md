## Classical vs Prototypical Inheritance

Inheritance: One object gets access to the properties and methods of second object.

#### Classical Inheritance:
    It is very verbose and generally not flexible like the one whe implement in C++.

#### Prototype inheritance:
    It is flexible. This happens in JAVASCRIPT.

#### Object Prototype:

Whenever we find any prooperty linked to an object, firstly the engine finds it in the direct level of the object but later it finds it in the subobjects linked through prototype property. 
This is known as prototype chain.

![Image](https://github.com/Abhishek-31/Abhishek-31.github.io/blob/master/_includes/Proto.png?raw=true)

Thus through this way, we can actually call properties linked by prototype chain.

Suppose there is another obj2 with same proto{} which was having Prop2. In that case, obj2.Prop2 returns same memory location as obj.Prop2. It is same.
## Important Example
```
var person={
    firstname: "Generic",
    lastname: "Default",
    getFullname: function(){
        return this.firstname + " " + this.lastname;
    }
}

var john ={
    firstname: "john",
    lastname: "Doe"
}

john.__proto__=person;
console.log(john.getFullname());
console.log(john.firstname);

var jane= {
    firstname: "Jane"
}
jane.__proto__=person;
console.log(jane.getFullname());
```
Output:
```
john Doe
john
Jane Default
```
**You should never use above method in your work. This is only for demo use.**

###Everything is an Object or a primitive
```
a=[]
b={}
c=function(){ }

a.__proto__. has many functions which are available to array.
a.__proto__.__proto__   //It gives again base object.
a.__proto__.__proto__.__proto__ //This gives output as null
a.__proto__.__proto__.__proto__.__proto__ //This gives output as reference error.

b.__proto__    //It gives output as base Object{}. This is the lowest on proto level
b.__proto__.__proto__ //It gives output as null
b.__proto__.__proto__.__proto__ //It gives output as reference error

c.__proto__    //It gives function empty as its output
c.__proto__.__proto__   //It gives again base object.
c.__proto__.__proto__.__proto__ //This gives output as null
c.__proto__.__proto__.__proto__.__proto__ //This gives output as reference error.
```

### Reflection and Extend

Reflection: An object can look at itself listing and changing its properties and methods.
Extend uses Reflection.

**If you need to access a property using a variable then use square brackets and not dot operator.**
Example
```
a={
    name: "Abhishek",
    age: "20",
    college: "una"
};

for (var prop in a)
{
    console.log(prop);
    console.log(a[prop]);
}
```
Now in case we did as following:
```
var person={
    firstname: "Generic",
    lastname: "Default",
    getFullname: function(){
        return this.firstname + " " + this.lastname;
    }
}

var john ={
    firstname: "john",
    lastname: "Doe"
}

john.__proto__=person;

for (var prop in john)
{
    console.log(prop);
    console.log(john[prop]);
}
```
In the above case we will have output as
```
john
Doe
function(){
    return this.firstname + " " +this.lastname;
}
```
But what if I want to check if the property traversed by thhis loop is actually its own property or method or it is of its prototype. We can use ```hasOwnProperty``` property with each variable.
```
for (var prop in john)
{
    if(john.hasOwnProperty(prop))
    {
        console.log(john[prop]);
    }
}
```
There is something known as extend which is not present in formal JS but are made by many of the frameworks and libraries on their own. 

Code for extend:

```
var jane={
    address: '111 Main Street',
    getformalFullName: function(){
        return this.lastname + ', ' + this.lastname;
    }
}

var jim={
    getfirstname: function(){
        return firstname;
    }
}

_.extend(john,jane,jim): This will add the properties and methods of jane and jim into main object of john.

_.defaults() does not override the value whereas extend overrides the value in case there is any property with same name.
```


### new operator 

```
function person(){
    this.firstname="Abhishek";
    this.lastname="Agarwal";
}
var Abhishek = new person();
// This person is known as function constructor
```
As soon as new keyword is typed, it creates an empty object and calls the function person in such a way that this points to that empty object. Unless any Object is returned from person function, this will return that empty object with some properties or methods that were set inside this person function.

```
function person(firstname,lastname)
{
    this.firstname=firstname;
    this.lastname=lastname;
}
var Abhishek = new person("Abhishek","Agarwal");
var Sumo = new person("Sumo","Saxena");
```
Objects created by the use of such functions are called function objects and such functions are called function constructors.
Such objects have a proto set to that empty function, in this case, ```Abhishek.__proto__= person();```

### Function constructors and prototype 
As we know function has a name property which os optional. Then it has a code property which is invocable. Other methods binded to it. It also has a prototype property of a function which is the prototype of the objects it create.
```
person.prototype.getfullname= function(){
    return this.firstname + this.lastname;
}
```
Now all the objects created by person function will have properties and this function, getfullname().

So this is an amazing technique because we can add properties and methods all at once through person.prototype.prop_name


**We do not use methods inside these function constructors because then every object made by such constructors will have a memory space for these method. In this prototype method discussed above, we can have same copy of method for all objects.**

### Using new operator and primitives directly.

```
var a=3;
var b= new Number(3);
console.log(a==b);  //True
console.log(a===b);  //False because second line creates a new Object.
```

**Use moment.js when you're dealing with dates**

```
var a=3;
var b= Number(3);
console.log(a===b);  //This will return true.
```

There is a difference between ```new Number(3)``` and ```Number(3)``` because the latter creates objects and not primitives.

### Important: Arrays and for in 

```
var arr = ["Abhishek","Harsh","Shivansh"];
for (var prop in arr)
{
    console.log(arr[prop]);
}
```
This will give output as:
```
Abhishek
Harsh
Shivansh
```
Now if we add another property using ARRAY PROTOTYPE, then during for in usage like we did above, it will be shown too.

```
Array.proptotype.anewprop="Anewprop";
```
Then the same will output this too:
```
Abhishek
Harsh
Shivansh
Anewprop
```

**So avoid using ```for( var prop in object)``` in arrays and use ```for(var i=0;i<array.size;i++)```** 

Remember, the following example will not work:
```
var person={
    firstname: "Abhishek",
    lastname: "Agarwal",
    greet: function(){
        console.log("Hi "+firstname);
    }
}
person.greet();
```
This will not work because we've used ```firstname``` and not ```this.firstname``` because objects does not create their execution context so funciton checks in its execution context and then will switch to global execution context.

#### Difference between \_\_proto__ and prototype
prototype is the prototype of the constructor function. It is only present in functions. Now, everything in this world has \_\_proto__  and function has a \_\_proto__ property which points to function.prototype whose proto points to Object.prototype whose \_\_proto__ is null. Whereas the functions prototype points to functionname.prototype which has a constructor function that points to the function itself. functionnale.prototype has another \_\_proto__ which points to Object.prototype.
The object that is created will point to functionname.prototype.

#### Differene between object.create and new function(values)

Object.create builds an object that inherits directly from the one passed as its first argument.

With constructor functions, the newly created object inherits from the constructor's prototype, e.g.:

```var o = new SomeConstructor();```
In the above example, o inherits directly from SomeConstructor.prototype.

There's a difference here, with Object.create you can create an object that doesn't inherit from anything, ```Object.create(null);```, on the other hand, if you set 
```SomeConstructor.prototype = null;``` the newly created object will inherit from Object.prototype.

Object.create creates the variables and methods inside the \_\_proto__ of the newly formed object whereas new constructor will create variables inside the object directly. 

So instances are properly created by Object create.

Object.create creates empty object and gives inherent properties in its prototype.

```
var obj1={
    first:"first",
    last:"last"
}
var o=Object.create(obj1);
o.last="Abhishek";
console.log(o.last);
console.log(o);
```

When this is runned, this output is given:

```
{last: "Abhishek"}
last: "Abhishek"
__proto__:
first: "first"
last: "last"
__proto__: Object
```
That is whenever you set any property, it is stored in that variable as it is and the inherited property lies in \_\_proto__ and thus this if in case you change any property that is inherited it does not change the property's value in the parent object but it does change it in the child's direct context and not the protypical context.


If in case, you deal with browser that does not have Object.create then you can use _polyfill_

**What is polyfill?**
Code that adds a feature which the engine may lack.
```
if(!Object.create)
{   
    Object.create=function(o){

        if(arguments.length>1){
            throw new Error("Implementation wrong");
        }
        function F(){}
        F.prototype=o;
        return new F();
    };    
}
```
So now this would act as Object.create although this isn't exactly what Object.create() is.

### Classes in ES6

```
class Person{
    constructor(){
        this.firstname="Abhishek";
    }
    xyz(){
        return "Hi" + this.firstname;
    }
}
var abhi= new Person();
```
This would create firstname in direct Object's memory and this function xyz will be present in prototype of abhi.

### typeof and instanceof
typeof simply tells whether the object is object or function or string Number
array is an object.
```
var a =3
console.log(typeof a)   //Returns number
```
```
var e = new Person()
console.log( e instanceof Person)
```

If moving down the prototype chain, anywhere we do find Person then this would return true.

**typeof undefined === undefined**
**typeof null === object**  ###Strange but true. A bug in Javascript
**typeof returns output in string**


### Strict Mode
```
"use strict";
```
You can use it  on the top of your js file or you can use it on the first line of your function definition.

This would not let you define any variable without the usage of the word "var".


**Read Jquery code for proper understanding of advanced concepts. 




