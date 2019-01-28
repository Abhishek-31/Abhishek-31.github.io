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

Here ``alteration operaator`` | (single pipe) is used to do the work of OR operaror and thus this is the case.
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

Started with Javascript.

Object.key(Property_name)