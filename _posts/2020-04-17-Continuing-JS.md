I've wasted a lot of time and now as we should always work to get better and it is never too late to start. I'm continuing that course.

Boolean(undefined, null,"") all of them returns false. 

In Javascript even if the function requires a parameter and you didn't send it, then also it doesn't care and it simply puts undefined at its place. 

```
greet=function(name){
    console.log("Hello" + name);
}
greet();
```
Here + has coerced undefined to a string value.

Before ES6, default arguments would be handled as
```
greet = function(name){
    var name=(typeof(name)!== "undefined") ? name : "abhishek" ;
    console.log("Hello" + name);
}
greet();
```
OR
```
greet = function(name){
    var name= name || "abhishek";
    console.log("Hello" + name);
}
greet();
```
Because operators are functions that return value.

typeof return type in string. 
After ES6, it will be like the same in C++

```
greet = function(name = "abhishek"){
    console.log("Hello" + name);
}
greet();
```

Suppose in HTML, we have multiple javascript files, then they are stacked in the sequence and in a way written after one another in the file and thus they're treated as a single file 
THUS

file1.js:
```
    var a="abhishek"
```

file2.js:
```
    var a="agarwal"
```

file3.js:
```
    console.log(a)
```

index.html:
```
    <script src="file1.js"></script>
    <script src="file2.js"></script>
    <script src="file3.js"></script>
```
This will give output: agarwal 
As this would mean:

index.html:
```
    var a="abhishek"
    var a="agarwal"
    console.log(a)
```

So as these are brought in open, they all come in the scope of window. 

So just to check whether anything is already present, you can do:

window.something = window.something || "value you want to put"

This will check if that something variable is already present or not.
Objects and Functions are related
### Objects and Dots

Objects are the collection of values of given name. Objects can be primitive property. Such as a Boolean, Number. This is primitive property. Object can have another Object. This is called Object property. Object can also contain a function and thus it is called method because it is associated witn an object. Thus Objects have properties and methods. 

Object is having a memory and a reference to a memory where its value is sitting. 


Syntaxes to create new Objects:

```
    var person = new Object();
    person["firstName"] = "Tony"
    person["lastname"] = "Stark"
    var first = "firstName"
    console.log(person)   :::Object
    console.log(first)    :::Tony
    console.log(person.firstName)   ::://No need for the double quotes
    person.address=new Object();
    person.address.street=1;
    person["address"]["city"]="Bareilly"

```

When you've to create an Object, new Object() line is necessary. It creates that variable as an Object and gives it an argument as \_proto\_ 

'.' has left ot right associativity. 


### Challenge: Add regular expressions inside [] operator of object to look for all such properties. 

Another way to create Object instead of new Object() is {}.

```
    var person3 = {}        //RHS is called object literal.
    console.log(person);    //Object
    var person2 = { firstname: 'Tony', lastname: 'Stark', age = 20};

var object2 = {
    firstname: 'Tony',
    lastname: 'Stark'
};
function greet(person)
{
    console.log('Hi ' + person.firstname)
}
greet(object2);         //Will give Hi Tony
greet({firstname : ' Mary', lastname : 'Jane'});
```

### Namespaces

We know what namespaces are, they are basically some spaces where few variables and functions reside. In javascript we don't have a separate namespace but we do we have a trick that works and that is of object. In the object, we can declare multiple variables and functions and then call them through object name thus same values could be present in multiple objects. For Example,
```
    abhishek={ school: 'bbl'}
    ishan = { school: 'grm'}
    console.log(abhishek.school)
    console.log(ishan.school)
    Now although these two schools are different and having same name but are unique through their link in object.
```

### JSON: Javascript Object Notation

We have to send data through internet connection and there are manay ways of doing this and these are

 XML: Here the data is stored in the form of tags and thus like HTML, for each tag we've a closing tag also and thus sending it takes a lot of space.

 JSON: Unlike Object Literal Suntax which is ```ObjectLiteral={a:"a",b:"b","c":"c"}```, the properties could be in double quotes but in JSON, they need to be enclosed in double quotes i.e ```ObjectLiteral={"a":"a","b":"b","c":"c"}```.

 Every JSON are Object Literals but all object literals can't be JSON.

 To convert an object into JSON, We have a builtin function and that is ```JSON.stringify(objectname)```.
 And if there is a JSON and we've to convert it into object, we have a builtin function and that is ```JSON.parse('{ "firstname":"abhishek","lastname":"agarwal"}')``` and this will convert a string that is a JSON into javascript object.

### First class functions

In javascript, functions are objects.
whenever you can do with other types such as strings, objects etc., you can do the same with functions. You can assign them to a variable and pass them around or we can create them on fly. 
We can attach properties and methods with functions in JS. So it can attach primitive, object or a method in itself. 
>> A function in JS is basically an object with some extra properties such as Name (Although, this is optional) and the code, which is basically something written to a property of that object. The difference is that this property is invocable. 

```
 function greet(){
     console.log("Hey there!")
 }
 greet.language = 'english'
 console.log(greet)         //This will give the complete function as output.
 console.log(greet.language)
```

####### Function statement and expressions

Expressions are the lines of code that results in a value.
It doesn't have to save it to a variable [Although, it can.]

FUNCTION STATEMENT:
These do not return into any value:
```
    function greet(){
        console.log("Abhishek")
    }
```

###### FUNCTION EXPRESSION (ANONYMOUS FUNCTIONS):
These do return a value and these can look like:
```
    var greet=function(){
        console.log("Abhishek")
    }
    greet();
    Here the RHS of this statement is actually returning a function object to LHS. Also this RHS function does not have any name property set. Thus it is known as anonymous function.
```

But then we do have a variable that points to that area and we can invoke our function through it. 

This will also return value:
var f3=function f4(){ ... }
But this f4 has no significance and this can't be called such as f4() so there is no point in giving unnecessary name.

#### Important concept.
``` 
But we know the concept of hoisting and whenever we use this concept of anonymous functions, we're actually giving a function value to a variable and due to this if we call it before it is declared, unlike normal functions, we will get undefined.
```

``` 
    greet2();       //This will run.
    function greet2(){
        console.log("Abhishek")
    }
    greet();        //This will give undefined is not a function.
    var greet=function(){
        console.log("Abhishek")
    }
```
This concept of first class functions is called _functional programming_

### Call by Value and Call by reference

In Javascript, we have call by value and call by reference. In call by value, we assign a variable to another one and thus the values are copied into second variable. In call by reference, we have reference in matter and two variables point to the same memory location and thus they change into same memory location. 

```
Objects when assigned follow call by reference
```

```
    var a ={ name: 'Abhishek'}
    var b=a
    b.name = 'Rauf'
    console.log(b)
    console.log(a)
    These both will result into Rauf 
```

```Primitives by Call by Value and Objects by call by reference```

So now if the parameters in function are sent and they're objects then also due to call by reference, we'll that the values at same memory spaces are changed.

```Equal operator in case of call by reference gives birth to new memory location. ```

```
    c={
        firstname: "Abhishek"
    }
    d=c
    d.firstname="Bae"
    //This would change the values of parameter for both c and d
    d={ name: "BBL"}
    //Now equal operator will give rise to a different object and c will be { firstname: "Abhishek" } and d will be { name: "BBL"}
```


### Objects and Functions and 'this'

'this' keyword can be confusing at times. For example, in the following example:

```
var c = {
    name: 'The c object',
    log: function() {
        
        
        this.name = 'Updated c object';
        console.log(this);
        
        var setname = function(newname) {
            this.name = newname;    //This 'this' points to Window Object.
        }
        setname('Updated again! The c object');
        console.log(this);
    }
        }
```

Here this inside setname points to global object and this is a kind of error in Javascript manufacturing. But it should have pointed to c object. So, its better that to avoid this confusion, you can appoint a different value as reference to desired this object. As we will apply equal operator in objects, everything will happen and that will be call by reference. 

```
var c = {
    name: 'The c object',
    log: function() {
        var self = this;
        
        self.name = 'Updated c object';
        console.log(self);
        
        var setname = function(newname) {
            self.name = newname;   
        }
        setname('Updated again! The c object');
        console.log(self);
    }
}
```

### Arrays

```
var arr = new Array();
var arr = [1,2,3];
console.log(arr[0]);
var arr = [1, false, 3, "Abhishek", { firstName: "Abhishek}, function(name){
    console.log("Hello" + name);
}];
arr[5](arr[4].firstName)
```

### Arguments and spread

"arguments" holds all the values of all the parameters passed in function. Actually even if you don't pass parameters to a functions that actually desire some, we can have space allocatted for them and that space is given by the engine to those variables by the concept of hoisting. 

```
    function comname(firstname, lastname, midname)
    {
        console.log(arguments)
    }
    comname("Abhishek");
```
// This will assign undefined value to lastname and midname and if we want to show arguments then it would be _["Abhishek"]_. This is an **array-like** and not exactly array because if it has been a normal array, it would be [], and it will give _[]_ which is not exactly array. **Array-Like** means that all functionalities of arrays are not given.

If we're not sending the parameters to these functions then we do not receive error so only way that we can check for the errors is by this arguments length.

```
       function comname(firstname, lastname, midname)
    {
                if(arguments.length === 0)
            {
                console.log("Parameters are not enough");
                return;
            }
        console.log(arguments);
        arguments[1]("Abhishek");
        console.log("---------------")

    }
    comname("Abhishek",function(name){console.log("Hey"+ name)},true);
    comname();
```

Due to this arguments concept, we don't have to add a separate variable name for each argument and thus could pass other parameters as:

```
    function extra(a,b)
    {
        console.log(arguments.length) //This will output 6
    }
    extra(1,2,3,4,5,6);
```

In modern browsers, we have spread operator "..."
```
    function spread(a, b, ...c)
    {
        console.log(arguments)
        console.log(a,b,c)
    }
    spread(1,2,3,4,5,6)
```

### Function Overloading

No overloading of functions is possible. 

### Syntax Parsers & Semicolon Insertion:

Automatic semicolon insertion is possible in Javascript but actually this could be dangerous so try to insert the semicolon all by your own.
```
    function getPerson(){
        return 
        {
            firstname: 'TONY'
        }
    }
    console.log(getPerson());
```
This would result into ```undefined``` because this would automatically insert 'semicolon' after return.
So generally try to use semicolon on your own.
This happened because it saw an enter after return. Generally try to use everything in a line.

Use as many comments as possible

### Immediately invoked function expressions (IIFE)s:

There is something known as IIFE and they get executed at the same time when it is getting made.
```
var greeting = function(name){    
    return "Hello " + name;
}("Abhishek);
console.log(greeting);
    //This greeting is now a string.
```

###Stand-Alone Function Expressions
```
{
    console.log("Abhishek);
};
```
This would not give any error and thus this would be a stand-alone expression.
Can we trick our syntax parser to have stand alone functions?
YES
But wait a minute, standalone functions? Standalone function expressions.
```
    function(name){
        console.log("Hello" + name)
    }
```
**This would give an error** because as soon as the statement begins with function , syntax parser thinks that it is a function statement. 
So we can use parenthesis and write this function inside of it.

```
(function(name){
    console.log("Hello" + name);
});
```
**This would not give any error**

### Stand-Alone IIFE
```
(function(name){
    console.log("Hello" + name);
}("John"));
```
```
(function(name){
    console.log("Hello" + name);
})("John");
```
These both works.

So, now if you create such a function in global context, so will the variables created inside such a function bother the variables existing outside in the global context? Answer is NO.

As soon as an IIFE is made, a separate execution context is formed. So see this,
```
var greeting = "Hola"

(function(name){
    var greeting = "Hello"
    console.log(greeting + name);
}(" Abhishek"));

console.log(greeting);
OUTPUT:
Hello Abhishek
Hola
```
```
Remember that whenever you're making such standalone functions, add a semicolon in the previous statement of code before defining that function because parenthesis adds other sense too.
```
```
If you want to effect the global variable on your choice, then you can actually send the window object too and effect its parameters.
```
