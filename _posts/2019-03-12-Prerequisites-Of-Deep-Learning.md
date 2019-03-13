I thought to officially complete courses on numpy stack in python and completing all tools completely.
So here is a blog doing and learningg it.
A+A will add the array with itself.
In python if we did this then it means that I am concatenating the same array.
np.array([]) is used to make an array.
np.sqrt(), np.log(), np.exp(name_of_array) will help in element wise operations.
For loops are avoided as they are very slow in python also.
zip function is used to combine elements of various array having same indexes and to unxip then we use * keyword so that we get back the arrays we want, like :
nam=["ABhishek","Manjeet","Kaur"]
roll=[1,2,3]
so now 
mapped=zip(nam,roll)
now change mapped as you want to show it, it depends upon what do you want with your zipped variable.
You can show them as an array so that,
list(mapped) or as a set by set(mapped) Now to unzip you can use
name,rollno=zip(*mapped)
now name would contain,
["ABhishek","Manjeet","Kaur"]
and roll will contain,
[1,2,3]
Now to dot product two vectors, say
a=[1,2,3]
b=[1,2,3]
onw way= for e,f in zip(a,b)
dot+=e*f
another way to do same is to use a*b num.sum(a*b). or (a*b).sum()
or by using dot function of numpy as,
np.dot(a,b);
or a.dot(b);
To get the angle between two vectors, we can use the formula as specified below,
cosangle-a.dot(b)/ np.sqrt((a*a).sum())*np.sqrt((b*b).sum())
np.arccos(cosangle) will gove us the angle between vectors a, and b
And always use np method( that is a.dot(b) or np.dot(a,b)) as it is a lot times faster than simple loops.
np.random.random((10,10)) will give 10 by 10 matrix
for random numbers, you can use np.random.randn(10,10). YOu have to send individual parameters.
Now .mean() and .variance() will give you respectively those parameters.

setTimeout() is an asychronous function.

