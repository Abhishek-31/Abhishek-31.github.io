This blog is about revision of javascript from a book and practising node.js. 

var a=setTimeout(function,time in milliseconds)
setTimeout(function,time), clearTimeOut(funtion,time in milliseconds)
setInterval(function,time between intervals) runs the function in loop)

clearTimeout helps in cancelling the effect caused by setTimeout. You can make this conditional for applicational purposes.
function func_name(){
    trying animation code
id=requestAnimationFrame(func_name) }
func_name() 
requestAnimationFrame helps in easy rendering of animations
cancelAnimationFrame(id)
all the global variables stay inside the object of window and you can access them through window.property name and suppose
<script>
    var a;
    alert(window.a==a)                  // answer will be true
</script>
A variable which is not declared using var is always global and that if simply var_name=value , then that variable will survive locally. 
Javascript does not support block scoping that is { variable_name } does not mean that that variable will survive in that block only.
There is a concept of *hoisting/ variable hoisting/* in which before a function is run in javascript, it actually scans complete function to see that whether any variable is declared or not. If yes, it declares that variable with undefined and this results in undefined result in the following example 
var a="abhishek"
function()
alert(a);                   //results undefined

var a="agarwal"
alert(a);
}
Another thing regarding scopes is closures which will come later
Closures is a very important thing which comes into picture when multiple functions are present inside a function and there are variables in outer function which are needed in inside function also. This, in Javascript, creates a closure in which if internal function is returned somewhere else and if it is used then those outer variables are bound in the closure created by javascipt of inner function
Example,
function(){
    var var1;
    function-2(){
        return function-2
    }
}
var 2=function();
now var 2 will be pointing to inner function which can be later called through parenthesis as var 2() so now I need var1 in function-2 which will be without any doubt used due to closure, which binds var1 along with function-2 and keeps them in var 2.

when after var 2 is used then function() is vanished but what remains are the shared variables which are used by both the functions.

Always keep js in separate file and that the linking of javascript file along with html/css file should be in bottom as 
```
<script src="">
```
Data types can be primitive(string,number, boolean, null, undefined) or of object type.
There are some of the basic predefined objects:
```
Array: Helps store, retrieve, and manipulate a collection of data 
Boolean: Acts as a wrapper around the boolean primitive; still very much in love with true and false 
Date: Allows you to more easily represent and work with dates
Function: Allows you to invoke some code among other esoteric things
Math: The nerdy one in the group that helps you better work with numbers
Number: Acts as a wrapper around the number primitive
RegExp: Provides a lot of functionality for matching patterns in text
String: Acts as a wrapper around the string primitive

```
var a=["a","b","c"];
var b=new Array("a","b","c");

Although both would look as same, but they are not typeof(a) and typeof(b) are different.

var movie="abhishek"
var big movie=new String("abhishek");
For adding/concatenating we can use + or str.concat(str2,str3,str4)
For taking a part of the string we can either use slice, or split. or substr. Whereas for array we can use slice and splice where splice is destructive. Slice works as a.slice(beginning index, last index) if negative numbers are used then calculations will be done from last.
str.substr(index,length)
For slitting the string into array you can use str.split("on which you want to split") 
Then for finding a substring in a string, you can use string.indexOf(" ",a) where a specifies the index after which I have to search a subtring.
If it is not present then -1 is returned.
lastIndexOf() is used to give starting index of last occurence of desired string.
match keyword is used to check the regular expressions in the string in which we use string.match(regex) It returns the part of string which follows that regex.
string.toLowerCase() returns string which is now in lower case
string.toUpperCase() returns string which is now in upper case

Then if you use var a="abhishek". Then using '.' keyword will give us the liberty of using methods associated with that string. But the typeof a is of string and not the object String where methods can be present. The answer to this lies in the fact that, javascript temporarily creates object of that variable and hence after using methods it converts them back into our cute primitives. This is known as primitive morphing.
So during a.length it makes string as an object and uses its methods. But still typeof(a) will give string and not object.whereas if
a=new String(" "), then this would give typeof(a) as object.
.push() is used to push elements in an array whereas .unshift() will be used to push elements in the beginning of the array.

shift removes first element and pop removes last element.

.indexOf() returns the occurence of that element in even an array.

concatenating array :
array1.concat(array2)
In javascript, Number include number, hexadecimal,exponential, decimal etc. Everyone is converted to 64 bit floating point numbers.
There is order to solve problems. such as parenthesis exponential, multiply, divide, add, subtract in that order.
Infinity and NaN are two keywords to denote very big number and NaN denotes that you have done an invalid numeric operation on the numbers examples: Math.sqrt(-1);
You can use var a=[] to make an array and var b={} to create an object.
ALso, this can be like var b=new Object();
we can use b.property=something
or b["property_name"]=something
or b{
    property_name: something
}
__proto__ is present which is present in every object and that contains some of the properties like .hasOwnProperty(), .isPrototypeOf() etc.

If many objects are present which have almost same properties then we can also make an object as a parent to all of these objects and then later that object will have prototype of Object in which prototype is again present which points to null.
If we want to make some of the methods common to all the objects, then we should make a common object through which properties are inhereted and this is made by Object.create(name_of_common_object). A keyword this is used which is used for pointing a in the following example:
a=Object.create(b)
and in b there is fcuntion which uses this.first_name and this.last_name and this does not create error and this is because this points to a and also the finding is done through all the prototypes till the prototype starts pointing to null and the properties of this. Meaning:
c=Object.create(d)
e=Object.create(c)
f=Object.create(e) and this checks all the properties till it finds Prototype which points to null and that is the case when last object is made in which prototype points to Object whose prototype points to null.
In JS, classes are not present and through this only we have inheritance.
By Array.prototype.method_name=function(){}
we can make a built in method for arrays.
Now if we are making any variable as var a=[] then a would have a property named method_name.


If boolean or string ir anything else is made simply then the type is boolean, string or other simple stuff but when Arrays are created simply the type is object.
Whereas if they are made as new String(), new Boolean(), new Array() then the type would return object.
For arrays for determining whether it is an array or not we can use Array.isArray(Array_name). This would return true in both kinds of declarations of array_variable.
If you have some truthy values then pass them in Boolean function so that to force it to return true whereas if you have to send false, then pass some falsy values(0,NaN,null, undefined,0,nothing) in as the parameter of Boolean.
Now if any object is present although it contains false then also it is true. Example,

            var Bool=new Boolean(false)
            if(Bool)
            {
                console.log("true");            This will print true.
            }

Type coercion is present which means that single use of == will ignore the type of values and simply check values that is 42=="42" Yes!. To make difference, you have to use ===
but if we are equalising two objects then they give unexpected results. Example,
new String("abhishek")==new String("abhishek")
new String("abhishek")===new String("abhishek")
Both will give false.
ypeof(null) will give object.
If you want to check null==undefined then it is tru but null===undefined then false
and also, if you have to check that whether the element contains undefined or not. Then best way to do is to check:

            if(typeof(element)==="undefined")

It will give desired output.

var a=document.querySelector("css-selectors"); will return first element that is matched by that css selector.
Further, a.textContent("") This is used to modify the text content of the element of whose query was selected.
a.getAttribute("any_attribute_name")
document.name_of_tag.setAttribute("attribute_name","value"). Also, we can use querySelectorAll so that it returns an array of all the elements which follow the property of selector element. Then use a for loop and make changes accordingly.

To add a style use, element.style.property_name=value;
float has a different meaning in javascript so use cssFloat in that case.

Suppose you have dessired element in a 
1. You can use a.classList to view all the classes of element a.
2. You can use classList.add("new_class_name")
3. You can use classlist.toggle("class_name"): It removes the class, if present and adds the class if not present. 
4. You can use classList.contains("class_name"):If it contains it, then true will be returned.
 
 and then you have to work on firstChild of that element. So,
a.firstChild
a.children will give the array in which each element consists of html entities.
You can also, add or remove DOM elements.
var a= document.createElement("tag-name")
now select parent through query selector(say b), and then
b.appendChild(a)
document.body.appendChild(a)
document.body.insertBefore(a,"name-of-tag-before-which-you-want-to-display")
If you want to insertAfter , then insertAfter is not present but you can use,
document.body.insertBefore(a,"name-of-tag-after-which".nextSibling)
.parentNode returns the parent node 
document.body.removeChild(new_element) to remove element.
a.cloneNode(false) this would give reference to a-just a and not its contents. Whereas, if I use a.cloneNode(true) then that would create clone of complete a node containg its children and so on.
Later save it in a variable say b such that, b=a.cloneNode(false) and then you can append b anywhere in you document.   
a.addEventListener is used to add the listener to an element a which is generally a DOM element. But, it can be body, document's element also.
a.addEventListener(Event, Event Handler(name of function on encounter with event, Event), true/false)
Event such as dblclick, click, mousemove, mouseover, load as event.

Qutting few chapters as I was really bored.

# Starting Node.js course finally


nodejs uses v8 which is made on c++.
nodejs has global but browser does not.
instead of document in brower, we have process in nodejs
and typing process in nodejs we can get the various methods on nodejs

Never push node_module folder as while cloning use npm install
Some of the dope libraries:
chalk, validator etc these are local npm modules
INstalling global you can use -g
You can use process to get the argv, first two are filled with file name and path. Alternative for this, you want to use yargs
yargs.command({
    command:command_name,
    describe:description of command,
    handler: function(){
        console.log("Abhishek Agarwal");
    }
})
process.argv return array.
yargs.argv return an object which is like {_:[],'$0':'app.js'}
where [] will be populated with the arguments passed.
JSON.stringify(object_name)             //Returns strings.
JSON.parse(string)              //Returns object.
WHile storing data as JSON, it gets saved as its own binaryb composition which gets displayes, once we are displaying it through the JSON file we can't just directly display it, as it make sno sense so what I do in its place is that I convert the file into string through the use of function of .toString(), so
```
const DataBuffer=fs.readFileSync("1-JSON.json')
const dataJSON=dataBuffer.toString()
const finalObjet=dataJSON=JSON.parse(dataJSON);
```

There is a difference between .toString() and JSON.stringify() and that is that the rpevious method actually creates the string out of the normal json syntax. whereas .stringify converts the parameter present in double quotes.
JSON file consists of data in string format.

##### Arrow functions 
Arrow functions do not have their own this binding. This makes them poor candidate for methods like
object={
    value1: something,
    value2: something_else,
    method1=()=>{
        console.log(this.value1)                //This will result into undefined.
    }
}
Instead of this, at places like these we should use,
object={
    value1: something,
    value2: something_else,
    method1=function(){                         //This will be working
        console.log(this.value1)
    }
}
But they are useful for another purpose and that is,
object={
    value1:something,
    value1.5:[]
    value2: something_else,
    method1:function(){
        console.log(this.value1)
    this.value1.5.forEach(function(){
        do something with this keyword              // result will be undefined
    })
    }
    
}
This is because these type of functions have their own this binding and thus, they should be avoidede at such situations, Its solutions are,
*Solution 1:
object={
    that:this
    value1:something,
    value1.5:[]
    value2: something_else,
    method1:function(){
        console.log(this.value1)
    this.value1.5.forEach(function(){
        do something with that keyword              // result will be shown as that points to outer this.
    })
    }
    
}
*Solution 2:
Us arrow functions in which you don't have your own this binding and it just uses outer this functionality.

object={
    value1:something,
    value1.5:[]
    value2: something_else,
    method1:function(){
        console.log(this.value1)
    this.value1.5.forEach(()=>{
        do something with this keyword              // result will be shown.
    })
    }
    
}
debugger can be used so as to stop at a point in a program where we want to know, which all vatiables are present and that is helpful.For this node inspect app.js................ is used
Also, in chrome, open, chrome://inspect and that helps, Also, if you are having 