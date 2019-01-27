### Regrets and Passion

Starting my journey as a web developer through freecodecamp can be a bit of a mistake because it does not cover all the topics and also, it takes everything for granted. So many things are just used but not explained which was something to be explained.

##### 09:22am
Started with EcmaScript.
Now as EcmaScript does allow a function to have a default parameter so for that this is used. But,

        var sum = function sum([a, b]) {
          // SyntaxError: "use strict" not allowed in function with destructuring parameter
          'use strict';
          return a + b;
        };
        

This can be converted into,
//If use strict is to be used inside.

        var sum = (function() {
          'use strict';
          return function sum([a, b]) {
            return a + b;
          };
        })();


If we can use use strict outside then,

        "use strict";
        var sum = function sum([a, b]) {
          // SyntaxError: "use strict" not allowed in function with destructuring parameter
        
          return a + b;
        };

This is not used much as by default we use ```"use strict``` and if we use use strict outside the function definition then there are no issues. But if we want other stuff to run in strict mode and just this function to run in use strict mode then we add a line inside the function, "use strict" and that is where problem starts so in the latter case, we use method defined above where it is necessary to assign a function to a variable.
FOR MAPS.
<https://codeburst.io/learn-understand-javascripts-map-function-ffc059264783>
FOR FILTER
<https://codeburst.io/learn-understand-javascripts-filter-function-bde87bce206>
FOR REDUCE
<https://codeburst.io/learn-understand-javascripts-reduce-function-b2b0406efbdc>
...array_name is the rest parameter for taking a lot of parameters.
just write this in funtion and then you can have an array with name array_name and then you can apply funcitonalities on this array.


Now this is something extraordinary in javascript and this is automatically invoked FUntion expression 
It’s an Immediately-Invoked Function Expression, or IIFE for short. It executes immediately after it’s created.

Consider the part within the first pair of parentheses: (function(){})();....it is a regular function expression. Then look at the last pair (function(){})();, this is normally added to an expression to call a function; in this case, our prior expression.

This pattern is often used when trying to avoid polluting the global namespace, because all the variables used inside the IIFE (like in any other normal function) are not visible outside its scope.
This is why, maybe, you confused this construction with an event-handler for window.onload, because it’s often used as this:

        (function(){
            // all your code here
            var foo = function() {};
            window.onload = foo;
            // ...
        })();
// foo is unreachable here (it’s undefined)
... is the spread operator and this unpacks the array. now suppose we have Math.max function which works when all the elements are sent inside the parameter list but here if we send an array then problem persists so what we do is ...array_name is sent and that returns the maximum value.

ctrl_shift_left/right is used for selecting an area within brackets.
ctrl_shift_up/down is used for multiple cursors in a line.

One way to initialise a variable with any property of any object is by using dot operator but second way is by using destructuring and by it we have,
suppose
        arr={1:"a",2:"b",3:"c"};
        a=arr.1;
        b=arr.2;
        c=arr.3;
        //Another way
        const{2:new_variable}=arr;
        //Through this we can have value 2 in new_variable.
for nested, example,
arr={1:"a",2:{1:"l",2:"u"}};
for this we have const{2:{2"new_variable}}=arr;
so now new_variable will contain "u".
const[a,b,...arr]=arr2; 

Only the fields which are required are to be sent in a function definition example you are sending an object then you just write important properties and rest of the properties are not used infact.

.splice function taked three parameters in which starting two parameters mean the starting index and the no. of parameters to delete.
 example, arr.splice(3,2);
 it means 0..1..2..3 So the function will start from 3rd index and star deletig 2 elements that is now my arr does not contain 3rd index and 4rth index's material.
 Also, splice returns the new array.

There is another function s```slice``` which copies or extracts the information of that array and copies it into another array and this way, it helps to extract certain information. 
It does not removes the elemeents and thus it lacks in third argument.
The element at second argument is not taken into consideration
 
 