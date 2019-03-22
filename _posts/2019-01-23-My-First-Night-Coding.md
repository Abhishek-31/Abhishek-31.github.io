
# A long Blog about Javascript Data Structures And Algorithms

### Inspiration

<hr>

I have watched many movies related to computer science and in them I have seen people waking yp all throughout the night and making shit happen through their hands and the same is gonna happen with me today. I have to code throughout the night to learn javascript and this is final. I attended internstalk and I feel like I am not doing anything. Like anything....

#### 21:46 
Started through this idea and this is complete dope. I will do rest of the work only when I have javascript certification.

For functions inside a object instead of using propert_name=function(params){}
you can use propert_name(params){body}.
this. keyword is used for accessing different properties of the same object.

I read a very important thing and that was that const does not mean truly immutable. This means that 
                ````const a=5;
                a=10;````
This will work as const allows declaration and deletion. Only modifications will not work example a++; will not work.
Also, if you want to make anything truly constant then use Object.freeze(a);
Facebook's immutable.js is made specifically for this purpose.


Also there is something known as getters and setters. They are used whenever we hae to return any value(getters) and setters(when we have to modify value). In these we do not require to call them as we do for functions.

get function_name(){

}

a.function_name; will work instead of function_name();
set will have same function_name but with a parameter inside its definition.

import { } from file_name

export { } for exporting functions without parenthesis
                    OR
export const var a; for exporting variables.
 
 import * as object_name from "file_path";
 now you can use object_name.properties(present in file_path)
 now that export that we studied was named export. ANother type of export is default export. Here export default is used. And also when you will be dealing with imports related to this export then you will be using import function_name from module_name. In named export we used to import using curly brackets and function_name inside it.

#### 01:59am
Started with regular expressions.
Added adsense on github c/logging page. [https://mycyberuniverse.com/add-google-adsense-to-a-jekyll-website.html]

I followed this website for enabling google adsense into my github pages so, this will be done.

Javascript is the first place in coding languages where I have seen / forward slahes and that is in regex.
Regular Expressions. These are made so as to test whether a given substring is present in a string or not.
so substr=/abhishek/;
str="abhishek is a good boy"
substr.test(str); //will give true.
This will giv true or false values and thus will tell whether the substring is present or not.

Here ````alteration operaator```` | (single pipe) is used to do the work of OR operaror and thus this is the case.
Here if you use || so that won't work. Also you have to avoid unnecessary space between different OR operators.

```i flag``` are used for ignoring the case. Suppose regex=/abhishek/i will return true for abhishek, Abhishek, aBhIsHeK also.

NOw like test operator, we also have a match operator. ```.match``` is used to return the regex if found like ```str.match(substr)``` will return ["substr"]. THat is an object is returned.

```g``` flag is used for repeatedly finding a regex and that will return the number of substr prsent in 
this .match(substr) will return an array of all the occurences of that substring.

```.``` character is used for wild card entries and through this we will get all the word s starting with that sequence and and ending at something.
Example, hug, hum, hut can be seen by /hu./ regex.

Now suppose you have to search only fewer words but now All such as, there are words bof,bug,bpg and big. You want words big,bof,bug and not bpg then you can ```b[iou]g``` can be used which tells words only which start with given, end at given and in mid they can have iou and so on.

To tell about the ranges we can use ```-``` operator. This helps such as bat cat hat need to selected but not zat so you can use then ypu can use [abcdefgh]at or [a-h]at
Also it can include 0-9 so finally in the brackets we have /[a-h0-6]at/

So this can be used to get the words containing alphabets and numbers.
^ operator, caret character, helps in telling which all characters need not be counted.
<hr>

+ \+ operator helps to return the consecutive occurences of that string ex /a+/ will return abhishek agarwalaaa "a","a","a","aaa"
+ \* operator is used for telling whether that particular string is even present or not.

<hr>

example regex=/go*/ will return go in go, gooooo in gooooo and g in gau and null in sand

There are two types of regex and these are lazy and greedy.
so if you are doing t[a-z]*i then that means that any sequence that starts with t and ends with i and that too maximum one but *? operator helps in finding the minimum sequence between t and i

^ character helps in ignoring the characters we don't want to check but that is within the character set that is [^abhishek] but if it is outside of character set thn that means that whatever is written after it is checked whether it is present in the beginning or not.

If you want to check whether a string is present in the last then you can add ```$```, anchor character in the last and that would check whether a string sequence is present in the last or not.

\w+ is used for shorthand description of [a-z0-9_] and so /\w+/ is used for these stuff.
then /\w/g will be used for counting the number of characters in in the given string.
Now if you doesn't want alhanumeric characters then you can use /W/ and this will return all the characters which are not alphanumeric
\d is used for digits and similarly \D is used for non numbers.
Now suppoose you have to make a username filter due to which you can have string starting with alphabets but if numbers are present then that would be in last.
so for that for starting check for alphabets, we can have ^[a-z] and to check in the last we can have [0-9]*$ so for separating it in a single regex we can use minimum number of characters function we can have {2,} and this can work as a separator also. 
so ^[a-z]{2,}[0-9]$ now comma inside {} is used as we want to act on second condition also.
\s is used for white spaces.
\S for everything that are not white spaces.
{} These are quantity specifiers and are needed when you want to specify the number of times an alphabet occurs in your string.
Example, you can have regex=/a{3,5}/ That means there should be aaa or aaaa or aaaaa in your string.
Actually you have to pay a lot of attention during this as suppose you have to select oh with h between 3 to 6 then you have to use Oh{3,6} and not h{3,6} as then it would select words having greater than 6 bits of h thrn follow it by next characeter suppose \s for any  white space then h{3,6}\s but also then it would select all the words having 3 to 6 h before any white space so you have to use Oh{3,6}\s then that would mean 3 to 6 h between O and {}.

you can use .repeat(no. of times) function so as to repeat a single character sequence many times suppose, string="a".repeat(100);
it will have string as aaaa.....//till 100 times.

minimum 3 times so use {3,} Only three is used whenever you need exactly 3 number of occurences.

?, question mark is used for ignoring previous alphabet.

multiple regexes can be checked using ?= and ?! so /q(?=t)/ will return true and will match "q" in qt and similarly /q(?!u) will return return true and will return q.     

For repeated substrings you can use capture groups in which each of the capture group is numbered from 1 and capture groups which are covered in parenthesis.
Example /(\w+)(\s)(\w+)\1\2/ no here first parenthesis is 1 and then second parenthesis is \s.  This, thus, expands to \w+\s\w+\w+\s

.replace function is used for the first part which is the regex and second part is with which it is to be replaced.
example
                ```"Code Camp".replace(/(\w+)\s(\w+)/, '$2 $1');
                    Returns "Camp Code```

$2 signifies second \w+ and thus this signifirs Camp

                let wrongText = "The sky is silver.";
                let silverRegex = /silver/;
                wrongText.replace(silverRegex, "blue");

This is another example.


.trim() function helps in removing the white spaces from and from beginning. So hola=hola.trim() will work.


To reparate ^ and $ functionalities in javascript | funtion is too used sometimes.
exapmple /^\s+|\s+$/g will give white spaces in starting and in end. Now g is used so that it is repeatedly checked till last.

#### 25thJanuary-22:59

Completed Regular Expressions. Started with **Debugging**
<hr>

##### 26th January 00:59
Completed Debugging, Started with Basic Data Structures.
If we want to copy the elements of an array into another we can use 
````arr1=arr2````<br>

Now if we want to repeat the copies of a single array into another array then what can I do ?
<h5>Suppose we are having loop three times.</h5>

                newArr.push(arr);<br>
                OR newArr.push([...arr])

Now if arr=[1,2,3] then newArr=[[1,2,3],[1,2,3],[1,2,3]]
but if you do, ``` newArr.push(...arr)``` then it would be [1,2,3,1,2,3,1,2,3]. 

arr.indexOf(element) is used to get the index of a particular element.

delete obj.prop is used for deleting an object's property.

Now hasOwnProperty and in keyword are used for checking whether any property is in the object or not. Suppose 

                Object.hasOwnProperty(property_name);
        OR      property in Object both results back in true.

`.hasOwnProperty(prop1,prop2)` this is used for multiple properties.


#### 29th January 01:18


I have to learn machine learning but before it, I need to complete what looks more attractive in the present time and that is web development. Let's quickly cover it. So I am giving three days for web development in which backend and frontend will be completed.

Started with Javascript.

Object.key(Property_name)
```let user in obj``` : THis is used for iterating inside a for loop as the objects do not have indexes as arrays does.


.split('')breaks a string into an array of characters and then .join('') turns it back into a string and then .reverse reverses a string.
Strings are not saved as arraysbut can be converted into one by .split('')
So to reverse a string str,
```str.split('').reverse().join('');```

Learnt how to create a slug url. 


#### 29th January 12:58

Completed Basic Data structres

#### 18:35

Started with replace function. In the second parameter we can either send a new value or a function which will return a new value.

As the strings are immutable so replace function works in changing any character in strings.
To convert any string into character array we have to use str.split("") and then after it we can use as we did in character array. Only .length is to be used. Then to combine these broken strings, we can use .join keyword.

You can use splice to insert elements. For that you have to use str.splice(index_at_which to enter,0,element to insert)

example:- str.splice(4,0,'may')
at 4th index may will come
For replacing the elements by using splice(n,1,new_element)
at nth index new_element will come. by replacing one element.


If you just use = sign in arrays then it copies the address og both so use ```str1=str2.splice();``` This will help you in duplicating the string and returns a new array.

Splice modifies the string and if only one parameter is passed then all the elements after that index everything is vanished.


split and splice are functions of strings so they won't work on strings. However if you have to use in strings then forstly using split("") convert them into arrays and then apply sklice or splice.

At any time if you want to remove any false value from any array arr, you can use arr.filter(Boolean).
It just takes the truthfull values in arr and returns it.

In reduce function we have a callback fuucntion which can have upto four arguments. This is accumulator, element, current index, array.

arr.reduce((acc,v)=>{function_body return acc},initial_value)
This will give you the value if acumulato.

Suppose you have to use regexp in a variable such that /Variable_content/, then you can use 

                var Regex_name= new RegExp(Variable_name);

Second parameter of this type will give you the g or i flag. so suppose you have to check in which it does not matter if it is case sensitive or not then you can use,
second parameter as "i".

                var Regex_name= new RegExp(Variable_name);


Whenever you have to **interpolate** any variable inside a string output/message, you have to use backticks and then inside those backticks you have to use ${variable_name};

Constructor functions are used for creating the objects hence in their body keywords like this. are used.
All the objects made by a constructor function are said to be instances of that constructor and thus js provides ways to check that whether object was created with the help of that constructor function or not by instanceof operator 


crow instanceof Bird // was crow created using the constructor function Bird or not. If it was not created using the Bird function then it will return false.
Even if it has same properties then too if new keyword was not used, It will return false.


Now suppose you are making an object through constructor function. Then in that if a variable is present then all the instances of that function will have duplicated value and now suppose there are a lot of objects. Then in that case prototypes are used in which function_name.prototype.prop=prop_value;
Now this prop is shared among all the objects created by function_name.
But now the values which are added by prototype are not its individual properties so if we check for hasOwnProperty(shared_prop), then it would result in false.
                                function Dog(name) {
                                this.name = name;
                                }

                                Dog.prototype.numLegs = 4;

                                let beagle = new Dog("Snoopy");

                                let ownProps = [];
                                let prototypeProps = [];

                                // Add your code below this line 
                                for (let property in beagle) {
                                if(Dog.hasOwnProperty(property)) {
                                ownProps.push(property)
                                }
                                else {
                                prototypeProps.push(property)
                                }
                                }

instanceof of prototype properties also gives true 
.constructor also stores the construction function used to make that object but constructor property can be overwritten and thus, this is not gonna help you even a bit.

Now if we start using prototyping then it is good if we equalize an object for a prototype. Through this way we can supply properties for our object, That is,
Dog.prototype={
        prop_1: value,
        method_1:function(){

        }
        method_2:function(){

        }
}
But this way is dangerous as in this constructor value is deleted and undefined will come if we do object.constructor so remember in this way, always use constructor property and explicitly define it as the value of which the object was an instanceof.

To check whether the protype is inhereted or not 
parent.prototype.isprototypeof(child);

typeof prototype of any construction function is of object. and so function.prototype.protype will also exist and that is object.prototype which is universal superset for all construction functions. hasOwnProperty is present in Object.prototype
For inheriting a property you have to create an instance of that function through which a property is made .
That is suppose
function Dog(){
        name="Abhishek",
        dob="31-10-1999"
}
function Cat(){
        name="agarwal",
        dob="31-10-1999"
}
Now suppose if you were to make all the Dog instances with different name but same dob then we could have used Dog.prototype.dob="31-10-1999";
BUt now suppose different construction functions' objects have same properties then for that we could use 
function 

                                        ````Group.prototype(){}````
                                ````Construction_function.prototype=Object.create(Group.prototype);````


where group is a constructor function which contains same properties in different objects.


BUt this way you are again compromising with the properties and so this way is used walong with Construction_function.prototype.constructor=original function name without parenthesis

Another way for this is by using a mixin where you send an object and that  function on its own gives your object a property.
for this: function mixin_name(obj){
obj.method_name=function(){}'
obj.property_name=value;
}


Now if we are making anything in the object of the form let obj={a:something,b:something};
Then outside we can change it like obj.a=something_else;
To prevent this we can declare a variable inside the constructor function and  a property with this. keyword that returns variable_name and this way variables can be changed only through those functions and not by the keyword itelf.

Whenever anything is declared for the object inside constructor function then we do not have to use let keyword. Just this. will work but in the case of constructor and an variable(property) is made for that object.

Functions that can be assigned to a variable, passed into another function, or returned from another function just like any other normal value, are called first class functions. In JavaScript, all functions are first class functions.

#### Different types of functions

Callbacks are the functions that are slipped or passed into another function to decide the invocation of that function. You may have seen them passed to other methods, for example in filter, the callback function tells JavaScript the criteria for how to filter an array.

The functions that take a function as an argument, or return a function as a return value are called higher order functions.

When the functions are passed in to another function or returned from another function, then those functions which gets passed in or returned can be called a lambda.

In Functional Programming, you can;t change anything unexpected and this thus helps as as bugs decrease and this can lead to our solution

Equalizing two arrays like arr1=arr2 will make an alias name for arr2 and that is with name arr1.
But, you should use arr1=[...arr2]. This will create a new instance of that array.Changes making in arr1 will not affect arr2 in this case otherwise it would have changed the answer.



Suppose you have to use .map function in javascript then, you can use .map(function(val){return anything});

Implementing my own map function
                                var str=[1,2,3,4];
                                str.myMap(function(a){return 2*a});
                                Array.prototype.myMap=function(callback)
                                {
                                        var newarr=[];
                                        this.forEach((a)=>{newarr.push(callback(a))});
                                        return newarr;
                                }
Implementing my own filter method.
                                Array.prototype.myFilter = function(callback){
                                 var newArray = [];
                                for (let i=0; i<this.length;i++){
                                if(callback(this[i])=== true ){
                                newArray.push(this[i]);
                                }
                                }
                                
                                return newArray;

                                };

                                var new_s = s.myFilter(function(item){
                                return item % 2 === 1;
                                });

                                
These functions which are map and filter can be replaced by a for loop or a .forEach function.


#### 31st January 02:11 am                                

Still doing Javascript. Running days late according to the plans, but atleast something is happening which is of greater interest for me.

splice(start,end) return elements starting from start to end-1 index and crops the same from original array.(or if correct visualization is what is needed then splice starts fro index and takes end no. of elements and thus including startth index.)
splice(one) will return elements starting from one to n-1 index. So if you have to remove an element you can use splice(4,1);
slice takes starting element index and final element index+1.
Whereas splice means the number of elements of 

Can call it a day. This is me Abhishek Agarwal signing off.

#### 31st January 19:50 pm

If you are passing and array into a function and thnen modifying it in any way then changes are visible. If you want to make changes in an instance and not in the Global Value of that array then equalise it with an array variable by using spread operator.

Also, if you are sending a variable then any change in it will not be visible in global instance.
Also, if ou are sending an object and equalizing it to any variable then also changes to that variable will show changes in original instance also so to prevent it we have 
                                
                                newobj_name={...oldobj_name}

Or the another way for arrays duplication is to use .slice() function which returns a new array.

In splice both arguments are inclusive and thus it means that if 
                                
                                str="[1,2,3,4];
                                str.slice(0,2); 
                                //will give 1,2 
                                whereas 
                                str.splice(0,2); 
                                //will give 1,2,3;

Second argunment of splice gives the no. of elements to bee taken into picture.

.every is used to check fo reach element in an array a condition specified by a function. If all the elemeents of that function satifies the property then true is returned else false is returned. It works with arrays.

arr.every(function(curvalue){return curvalue>0;}); This will give you true only when all values are bigger than 0.

similarly .some function is used for checking if atleast one element is present which follows that property.

````.includes```` is a function that returns true or false whether arr.includes(i) is true or not. If it is true then, 

Array.prototype.slice.call(arguments) will return an array of arguments. Also, you can use ...arr so as to make an array name arr and that consists of all arrays,

Or Array.from(arguments); will return array of all arguments.


##### Using Delete operation

After deleting any array's element which you can do with the help of delete keyword as delete arr[i],You should use array.filter(Boolean) as delete actually creates null at that point.

So removing all with Boolean as false will really help.

Object.keys make an array of any object's keys. That is very useful so use Object.keys(source) so as to make an array of keys of any object named source,

Always remember that object's keys are accessed through square brackets and not by parenthesis.
````.every```` function demands a callback function which checks for every element a condition where we return true or false. As soon as a false is returned, .every will break on its own and thus false in lst is returned whereas if true is returned then it is firstly checked whether all are returning true. If yes then in last true is returned

                                function whatIsInAName(collection, source) {
                                // What's in a name?
                                var lama=Object.keys(source);
                                var arr = [];
                                // Only change code below this line
                                arr = collection.filter((x)=>lama.every(function(a){if(x.hasOwnProperty(a)&&x[a]===source[a])
                                return true;
                                else return false;}
                                )
                                );
                                
                                // Only change code above this line
                                return arr;
                                }



##### Difference between .forEach and .map

````.forEach```` does not return anything and so must be used when you just want to do something through all the elements of an array.<br>
Whereas map does change the value and hence must be used if you want to change values so that you can assign the value of returned array into something else.

In regex followed by is used by ?=[whatever] and this brings he cursor before whatever and thus this is useful we can add choices through ?=" "|_|[A-Z]. But this will work only when ?=[] is enclosed within parenthesis.

[] square bracket is the alternative for | operator
a|e|i|o|u is equivalent to [aeiou].

.match() keyword in regex returns an array of all occurences given in regex in a array.

We can replace slice with suubstr and that produces same results.


.includes work with string and arrays.

##### Difference between .charAt and []
.charAt is specific to strings and moreover [] is kind of primitive and it does not work in IE7. Although you know that you would be using [] but .charAt is better if only strings are conidered.

.charCodeAt works with a string and in the brackets I need to give the index which is required for getting the ASCII value.

str.charCodeAt(index); 
String.fromCharCode(ASCII) code returns the string.
However fromCharCode() expects a series of numbers rather than an Array!. So if you have any array of number.

//Read about sets in javascript.

Always use shift or pop to delete the elements from ends as usinf delete operator creates vacant spaces in an array and thus the array in return is known as sparse arrays.

Array.isArray(arr) is used to check whether arr is array or not and also it can be used inside an array with .some function so as to convert .some() into .some(Array.isArray) and this on its own sends data into the function and performs function.
It is like .forEach() as it just takes the name of the function and on its own gives the values to it.

.parseInt function takes string as the first parameter and the second parameter is optional which is basically the base from which conversion has to take place( the base of first parameter) and returns the integer(decimal) value.

