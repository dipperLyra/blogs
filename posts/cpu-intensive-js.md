CPU Intensive Applications

Working with io bound applications can be a breeze in Node.js but same cannot be said when it becomes CPU heavy. 
This became more obvious to me as I was fiddling with gcc compiling options during the weekend and I hit me that when programming servers in Node.js that I do not know any obvious way to ask the interpreter to help with performance optimisations.

I was playing with array of integers in C without using SIMD just checking how far I get with compiler flags.


While programming applications that are io bound in Node.js you feel like a king. The async await model is really easy to use. The issue is what happens when you occassionally jam a CPU bound task, like manipulating a huge array.

Playing around with gcc compiler flags, the

with network compilers and I tend towards day job but when I can control