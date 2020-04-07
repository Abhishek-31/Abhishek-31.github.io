### Javascript handled by engine

As soon as we're making out JS code run, it is wrapped in execution context which makes two things, Global Object and 'this'. Each tab has its own Execution context and every context has these global objects. There is another global object(window) in case of normal js running and that is 'window'. If we're running node.js, then this global object would be something different. Now, suppose you are creating a variable and a function in Javascript, then they are actually bound in the global object, window and suppose


### Variables and functions

```
var a=5
z
function b()={

}
```

then actually they are saved as `a: 5    b: function b(){ }` and can be accessed as window.a and window.b
Javascript engine creates this global object. In the case as browser this is equivalent to window.
Now this all we are getting through the engine generated stuff.


### Hoisting

If we're declaring a function after it is called in javascript, no error comes. But if we are using a variable before it is declared then as a value of that variable, we get "undefined" but this will happen only when atleast somewhere in the future that variable is declared. If it is not declared then we will get Uncaught ReferenceError.

```
console.log(a)
a=5
//This will output undefined
```
```
console.log(a)
//this will output Uncaught Reference Error
```

```
b()
function b(){
console.log("Fuck off")
}
//this will work.
```


This is because of a phenomenon, _hoisting_.

Execution context is created in two phases.
1. Creation phase: Global object, this, outer environment set up. It also setups memory space and function and this is known as hoisting. Before code, gets executed line by line, the engine has allotted space for variables and functions and when it gets executed , it has already allotted space. Now variables and functions, functions has all the space alotted for its name and content also and so while executing, we expect that everything gets runned. In the case of variables, the values are alotted in execution phase and a placeholder is set as undefined.

2. Execution phase: Told earlier.

Do not rely on hoisting.

### Undefined

```
var a
console.log(a)
if(a===undefined)
console.log("a is undefined")   //Gets printed undefined
else
console.log("defined")
```

Although we can explicitly set a variable as undefined but that is something that we should never do. For example,
```
var a=5
console.log(a)   //Outputs the value of a
a=undefined
if(a===undefined)
console.log("a is undefined")       //Gets printed undefined
else
console.log("defined")
```
But now you can actually never say that whether the value was undefined from the beginning or it got undefined by you so problem in dbugging.
undefined means NOT-SET

### Execution phase

easy-peasy


### Single Threaded, Synchronous Execution


Although we have heard about Asynchronous requests, yep, AJAX.
Javascript is synchronous and it runs code in a sequence.

### Invocation

Running a function.
When the code is given to the engine, it creates a global exection phase but as soon as functions get called, a separate execution context for that particular function is created and this contains all the variables that are declared in the respective contexts.


### Scope chain

```
function b(){
console.log(myVar);
}
function a(){
var myVar=2;
b()
}
 var myVar=1;
 a()
```

Its output is 1, because each execution context has its own variables + *reference to outer environment* which in this case is global execution context and the variables which are called in the function are first checked in the local variable list and then in the global execution context. But this _reference to outer environment_ need not be global always. It depends upon the the lexical position of the function in which that function is present. In this case, it is global because lexically b, a, myVar is sitting in global context. This clearly means that the method of calling (execution stack) does not affects result. So execution context does not  depend upon the physical location of the code but it depends upon the invocation sequence of various functions. After syntax analysis, when global object and this are created, at the same time this reference to outer environment is also created because the syntax analyser know very well, where our code is present. So until it will find the reference of the variable, it will continue the chain and will give the expected output. Example:

```
function a()
{
    var varchar=8
    function b()
{
    console.log(varchar);
}
    b()
}

var varchar=1
a()
```

This will give output as 8.


```
function a()
{
    var varchar
    function b()
{
    console.log(varchar);
}
    b()
}

var varchar=1
a()
```

This will give output as undefined

```
function a()
{
    function b()
{
    console.log(varchar);
}
    b()
}

var varchar=1
a()
```

Here firstly the value would be searched in b's context, then it will find it in a's context because b is lexically present in a. Now again varchar is not present here so it will find for it in global context because a is lexically present in global context level. Hence, chaining is done and this is known as Scope-Chaining.


```
function a()
{
    function b()
{
    console.log(varchar);
}

    b()
    var varchar=3
}

var varchar=1
a()
```

Now, let us explain what, is happening here. Here a() is called and then b is defined. Now b exists inside a and hence it is lexically present inside a. So if anything is not found in b, it will be found until it gets found by the concept of chaining. Now b is called just after function b is defined so no value for varchar is assigned. So it checks in the context level of a but now varchar is allotted space after creation phase but its value is not found so due to the concept of hoisting, the variable is given undefined value by the engine.

```
function a()
{
    function b()
{
    console.log(varchar);
}

    var varchar=3
    b()

}

var varchar=1
a()
```

Here the value 3 is given.

```
function a()
{
    function b()
{
    console.log(varchar);
}

    var varchar
    b()

}

var varchar=1
a()
```

Here undefined is given as output.

### let vs var

We can also use let instead of var but it will give error if the variable is declared later.
Example,

```
console.log(a)
var a=7
```
This will print undefined

```
console.log(a)
let a=9
```

This will give UncaughtReference Error.


```
function a()
{
    varchar=10
    console.log(varchar)
}

var varchar=1
console.log(varchar);
a()
console.log(varchar);
```

This will give output as :
1 <br>
10 <br>
10 <br>

```
function a()
{
    var varchar=9
    varchar=10
    console.log(varchar)
}

var varchar=1
console.log(varchar);
a()
console.log(varchar);
```

This will give output as :
1 <br>
10 <br>
1 <br>

This is because when we write normal varchar, then it references to the one according to scope chain,

```
function b()
{

function a()
{

    varchar=10
    console.log(varchar)
}
var varchar=9
console.log(varchar)
a()
console.log(varchar)
}

var varchar=1
console.log(varchar);

b()
console.log(varchar);
```
 This will give output as:
 1 <br>
 9 <br>
 10 <br>
 10 <br>
 1 <br>


### Event Loop and Asynchronous functionalities.

So long we've been talking about the contexts. All this is taken care by the runtime of various engines and in the case of Chrome its V8 engine. So basically there is heap and stack. setTimeOut, DOM, HTML Requests and these are not present in V8!
Web APIS are extra things that our browsers actually provide us and these has setTimeOut, DOM and HTML Requests. Then there is event loop and callback queue.
Single Thread means that the language has a single call stack and that everything gets through that stack only.

```
function foo(){
    throw new Error('Oops');
}
function bar(){
    foo();
}
function baz(){
    bar();
}
baz();
```
Inside console:
UncaughtError: Oops<br>
foo<br>
bar<br>
baz<br>
(anonymous function) <br>

Now Image requests, HTTP Requests are slow. Now, suppose something appears on the stack, then due to its slow nature, it will actually block my code to run forward. So we need to be asynchronous in our practices so that speed can be ensured. Now browsers will be stuck in middle if such thing occurs. So these slow things, we can't actually push into stack, so what we do is that we wrap those inside something that browser provides as an extra thing and that are known as WEB-APIs which are threads which we cannot use directly but can only make requests to. In the case of Node.JS, instead of WEB-APIs, we have these C++ APIs.
So runtime can actually do one thing at a time but browser comes with more things than just runtime and hence concurrency is established.

```
console.log('hi');
setTimeout(function cb(){
    console.log('there');
},5000);
console.log('Bye')
```
OUtput:<br>
hi<br>
Bye<br>
there<br>


Now this statement setTimeout.... is pushed into stack and as it is the webapi, instantly it is popped from stack and pushed into webapi section where timer runs and then the output is sent to taskqueue or known as callback queue. Now the work of event loop? It checks the stack, if the stack is empty, then it removes the front element of taskqueue and pushes it on the stack. That is function, cb, gets pushed into stack after event loop sees that okay the stack is empty and now it is the time to make the taskqueue empty.

```
console.log("Hi")
function b(){

    setTimeout(function f(){
        console.log("Check");
    },1000);
        setTimeout(function f(){
        console.log("Check2");
    },0);
        setTimeout(function f(){
        console.log("Check3");
    },0);
}
b();
console.log('Bye')
```

Output: <br>
Hi<br>
Bye<br>     //Now the normal stack is empty
Check2<br>
Check3<br>
Check<br>


So, just for an example, we have .forEach function which is synchronous. We can write an asynchronous version of .forEach utility also.
```
[1,2,3,4,5].forEach(function(i){console.log(i)});
```
This would be synchronous.

Asynchronous function:

```
asyncforeach([1,2,3,4,5],function (i){console.log(i)});

function asyncforeach(array,cb){
    array.forEach(function () {
        setTimeout(cb,0);
    })
}
```


### Types and Javascript

_Dynamic Typing_ is the technique in which we do not tell what is the type of the variable but the engine recognises it all by itself. A vaiable can hold different type of values, because the typing is decided at execution time but in case of _Static Typing_, the variable has the fixed type, that is the case in C++.
Different types of data in which a variable can be stored:

Primtive type is a single value. We know that a object is a name, value pair but primitive type is a single value and Javascript has 6 types of primtitve types:<br>
```
1.undefined: lack of existence of value<br>
2.NULL: this also means lack of existence but this generally is suggested to feed as value in case of telling that the variable doesn;t has any value yet. By default after constructing phase, when space is allotted for the vairiables, they are given value as undefined. <br>
3.Boolean: "true" or "false"<br>
4.Number: javascipt has only this type for numerical figures and this is floating decimal point number and at times it can make maths weird.<br>
5.String: A sequence of characters. Both ' ' and " " can be used. <br>
6.Symbol: Used in ES6. We will not talk about it here.
```


### Operators

It is a function that is syntactically written in some other manner.

>> Operator precedence and associativity:
Functions are called in according to the precedence and associativity of those operators. When the operator functions have same precedence, then in that case associativity kicks in.

        console.log(a=5) _This will output 5 in the screen_

As operators have the property of a function, that's why it returns some value to screen.


 
### Coercion

Converting one type into another type. This happens frequently in javascript because it is dynamically typed language.

'+'
+ adds two numbers
+ concatenate strings
+ treats number as string:  1 + '2'='12'

Please remember that coercion is something that is constantly happening whenever different types are used with operators. 

>> Output of the following statement: ```console.log(1<2<3)``` This will output into true. But ```console.log(3<2<1)```. The output will be true because 3<2 gives 0 as this is false which is less than 1 so that all works.

There is a function Number() and this tells that Number(true)=1.
This is all coercion. 
Okay, so whenever the expression does not explicitly return anything, we get undefined as output. So some standard functions such as console.log(5) gives 5 and undefined because 5 is printed but as nothing is returned by console.log so undefined.

Number(undefined) return ==NaN==. So undefined cannot be coerced so it returns NaN, which is not primtive data type but can be used as one. Further Number(null) return 0. There are times when we don't want coercion. We can check the type by "===" sign in javascript.

> 3 == 3 return true.
> "3" == 3 return true.
> var a == false;
> a == 0 returns true;
> ==There are some exceptions such as null == 0. Here null is not coerced to 0 and hance this will result in false. But in some other cases such as null < 1, null is coerced into 0.==
>""==false this will give true
>""==0
If you want to avoid this game of coercion, use ```===```

==So generally use === in your code.==

NaN != NaN and NaN !==NaN

==Much better than === is Object.is(op1,op2)
This return false with +0,-0 and return true with NaN,NaN. and for rest of the cases, it give same result as === .== 



This is me signing off. I'll be talking to my bae, Saumya now. I love you babe... I know you will never read this :P
