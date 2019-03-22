Unlike DOM in javascript where by document.getElementById("page-title"), Here we use $sign which takes the id in the brackets and return the element in an array which is known as JQuery object.

[<h2>My name is Khan</h2>]
This means tha this object will have all JQuery methods to those objects.
We can change the css of any elemnt by using .animate() fi string value of attributes and numbers fo positioning left right etxc =properties.

So for example we have any var x=$(#something). So this means that it will come in an array. Such as x=[ <h2>something</h2>] and this x will have all the methos of jquery objects but if we use x[0], it will unwrap stuff if that array and that will not give var y=x[0], y=<h2>something</h2> And that will not use any methods.

            x.animate({left:20px;})
            x.css("background-color:blue")

Selectors are same as css, # for id, . for class, tag_name for simple tag.










