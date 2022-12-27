# Lesson 2: More Basic Syntax

It is said that if you want to master programming you need to understand 
recursion and pointer arithmetic. The good news is that Java Script does not
have pointers; so one issue less. 

In this lesson we will tackle recursion and add an important part of the 
programing languages, functions. 

*lie to children*: Java Script, especially node.js uses allot of asynchronicity, 
that is lots of things happing out of order. It can be said that understanding 
asynchronous code is worse than pointer arithmetic. But we will cross that bridge
when we get there.

## Fibonacci

Here is out jup, weite a program that prints out Fibonacci numbers from 0 to 100.

If you don't know how to compute Fibonacci numbers, ask [Ada Lovelace]. She
is considered to be the first programmer and wrote a program computing 
Fibonacci numbers on the [Analytical Machine]. Too bad it was never compleated.

Since Ada is probably busy, here is the is the algorithm:

- the Fibonacci number of 0 is 0
- the Fibonacci number of 1 is 1
- the Fibonacci number of n is Fibonacci number of n-1 added to 
  Fibonacci number of n-2 

Or in something that looks more like math:

```
F(0) = 0
F(1) = 1
F(n) = F(n-1) + F(n-2)
```

[Ada Lovelace]: https://en.wikipedia.org/wiki/Ada_Lovelace
[Analytical Machine]: https://en.wikipedia.org/wiki/Analytical_Engine 

## Setting Up Your Project

I want you to create a fesh project in GitHub for Desktop and call it fibonacci.
And in this project I want to to create a file called fibonacci.js.

If you don't remember how this works, you can go back to [lesson 1] and see how 
you did it last time.

[lesson 1]: 1-fizzbuzz.md

## A for Loop

In our program we will first write a simple loop going from 0 to 100. 

You may copy the code from lesson 1. Yes, programmers copy and paste code. 
Copying code form other projects is not a bad thing, you get into trouble 
when you copy and paste within one project to much, we call that duplication.
But more on that later.

```js
for (let i = 0; i <= 100; i++)  {
  console.log(i);
}
```

I wrote a for loop. The for loop has all the bits we are saw in the while loop, 
just all put together. In a for loop you have first the initialization, then
the stop condition and finally the iteration. 

The initialization is simple, we create the variable `i` and set it to 0. This
is called once at the beginning of the loop.

The stop condition is a bit trickier, as long as i is less or equal to 100, 
the loop will continue. This is called at each step of the loop, also known 
as iteration, to check if the loop should continue.

The iteration is what is done each step, or iteration, to advance the loop. 
Here we increment `i` by one. In the previous loop we saw `i = i + 1`, well
`i++` does exactly that, just in a more compact syntax. 

Please note that you can do anything in these three steps. It is common to count 
up a counter, but that does not have to be the case.

## A function

```js
function fibonacci(n) {
  return n;
}

for (let i = 0; i <= 100; i++)  {
  let fi = fibonacci(i);
  console.log(fi);
}
```

I added the function `fibonacci`. It obviously does not compute a fibonacci 
number, yet. For now it just returns the given `n`. The `n` here is an argument. 
A argument is just a special variable, that happens to be given to a function.
It can be considered the input into a function. You can have an arbitrary 
number of arguments, but we only need one here. 

*lie to children*: In special circumstances, arguments can also be outputs, but
that is a different story.

The result of the function is handed back with the keyword `return`. It tells 
the function to stop executing. You may have multiple returns in a function.
Sometimes it makes sense to quickly stop executing if you don't need to do more
work. 

In our case the result of `fibonacci(i)` is stored in the variable fi.

## Handling 0 and 1

For a start we will start to handle 0 and 1. How do we do that, well this 
sounds like we need a condition. 

```js
function fibonacci(n) {
  if (n == 0) {
    return 0;
  }
  if (n == 1) {
    return 1;
  }
  return n;
}
```

Am I missing an else? Well, yes and no. You could add else, but since we are 
returning from the function, the else case is obsolete. This is often considered
as the "no else" pattern and greatly reduces function complexity. 

## Recursion

Now onto the recursion bit. Remember the case for Fibonacci number of n.

```
F(n) = F(n-1) + F(n-2)
```

Well we just need to literally implement that:

```js
function fibonacci(n) {
  if (n == 0) {
    return 0;
  }
  if (n == 1) {
    return 1;
  }
  return fibonacci(n - 1) + fibonacci(n - 2);
}
```

We are literally calling the function again, but with different parameters. 

If you run the function you should get the following output:

```
C:\Users\seanf\Documents\GitHub\fibonacci>node fibonacci.js
0
1
1
2
3
5
8
13
21
34
55
89
```

And you also will notice that it is getting slower and slower the higher you get.
After a few minutes you probably should cancel the program, do that by clicking
into the terminal and hitting `CTRL+C`.

```
701408733
1134903170
1836311903
^C
C:\Users\seanf\Documents\GitHub\fibonacci>
```

This will bail you out of the program execution. `CTRL+C` will cancel any command
line program, that is well behaved. 

Ok so this program is correct and computes the Fibbonacci numbers, but is a bit
slow. You should commit your changes before we dig into a different approach
that may be faster. 

## Square Complexity

Why is the program slow? 

The first couple of numbers come out really fast, but as the numbers grow, it 
gets slower and slower. What is happening? 

Now let's think about what the program is doing:

For 0 it does the following:

```
F(0) = 0
```

For 1 it does the following:

```
F(1) = 1
```

But we know that already.

For 2 it does the following:

```
F(2) = F(1) + F(0)
F(1) = 1
F(0) = 0
```

For 3 it does the following:

```
F(3) = F(2) + F(1)
F(2) = F(1) + F(0)
F(1) = 1
F(0) = 0
F(1) = 1
```

That last `F(1) = 1` ist not a typo. It needs to compute `F(1)` once for `F(2)`
and once `F(3)`. 

For 4 it does the following:

```
F(4) = F(3) + F(2)
F(3) = F(2) + F(1)
F(2) = F(1) + F(0)
F(1) = 1
F(0) = 0
F(1) = 1
F(2) = F(1) + F(0)
F(1) = 1
F(0) = 0
```

For 5 it does the following:

```
F(5) = F(4) + F(3)
F(4) = F(3) + F(2)
F(3) = F(2) + F(1)
F(2) = F(1) + F(0)
F(1) = 1
F(0) = 0
F(1) = 1
F(2) = F(1) + F(0)
F(1) = 1
F(0) = 0
F(3) = F(2) + F(1)
F(2) = F(1) + F(0)
F(1) = 1
F(0) = 0
F(1) = 1
```

For 6 it does the following:

```
F(6) = F(5) + F(4)
F(5) = F(4) + F(3)
F(4) = F(3) + F(2)
F(3) = F(2) + F(1)
F(2) = F(1) + F(0)
F(1) = 1
F(0) = 0
F(1) = 1
F(2) = F(1) + F(0)
F(1) = 1
F(0) = 0
F(3) = F(2) + F(1)
F(2) = F(1) + F(0)
F(1) = 1
F(0) = 0
F(1) = 1
F(4) = F(3) + F(2)
F(3) = F(2) + F(1)
F(2) = F(1) + F(0)
F(1) = 1
F(0) = 0
F(1) = 1
F(2) = F(1) + F(0)
F(1) = 1
F(0) = 0
```

Well i think you get the picture. We call that square complexity, sometimes
refereed to a `O(n²)`. (I will not go into he O calcul, but if you ever see
`O(n²)` you know it is referring to an algorithms complexity.) It is called
square complexity, because for every item we add to the computation, we are
doubling the work that needs to be done. You can see that this quickly gets 
out of hand. 

Sometimes you can't avoid algorithms with square complexity, then you just 
need to just hope you will never need to compute large amount of values.

We will try to be a bit more cleaver about it. If you look at the lists above
you will see that the algorithm is computing many values over and over again.
Why don't we just remember what values we computed beforehand?

## Arrays

First we need to have a place to save the values. Where do we save values? 
Variables. 

We could do the following:

```js
let fib_0 = 0;
let fib_1 = 1;
let fib_2 = fib_1 + fib_0;
let fib_3 = fib_2 + fib_1;
```

But like in the last lesson, this will not work well if we want to compute an
arbitrary number of values.

Luckily there exists a special variable type that can be used to store 
many values: array. 

To create an array of values we write the following:

```js
let fruits = ['banana', 'orange', 'pineapple'];
```

To access elements in an array we can index into the array, starting at 0:

```js
console.log(fruits[0]);
console.log(fruits[1]);
console.log(fruits[2]);
```

Or with a loop:

```js
for (let i = 0; i < fruits.length; i++) {
  console.log(fruits[i]);
}
```

Output:

```js
banana
orange
pineapple
```

*lie to children*: There are a few other ways to create arrays, but these 
involve understanding objects and we will see these later.

## Using Memory

That's nice, how do we create an array of 101 elements? We can, but for now
we will create and empty array and fill in the values. The nice thing about
Java Script arrays is, you can put any value into the array, if there is 
none there it will create it for you. 

Here is an empty array, that will be our cache:

```js
let fibonacci_cache = [];
```

And we need to write a function to fill the cache:

```js
function fill_fibonacci_cache(max) {
  for (let i = 0; i <= max; i++)  {
    if (i == 0) {
      fibonacci_cache[i] = 0;
    }
    else if (i == 1) {
      fibonacci_cache[i] = 1;
    }
    else {
      fibonacci_cache[i] = fibonacci_cache[i-1] + fibonacci_cache[i-2];
    }
  }
}
```

This function almost looks like the original fibonacci function. This time we
not not have recersion, we work through a loop. Because of that we need to read
the else blocks.

```js
function fibonacci(n) {
  return fibonacci_cache[n];
}
```

Our fibonacci function just reads from the cache. We are assuming that it was 
sufficiently. 

And the rest of the code looks like such:

```js
fill_fibonacci_cache(100);
for (let i = 0; i <= 100; i++)  {
  let fi = fibonacci(i);
  console.log(fi); 
}
```

First we will the cache, then we retrieve values and print them.

Now this looks quite good, time to commit your changes.

## More Flexibility

What if we want to compute other Fibonacci numbers? What if we want to hide the
fact that we use a cache? Can we do better?

Here is an idea, why not check if we have a value in the cache and only if 
we do not have a value in the cache compute the value.  

First, let's be smart about the cahce, we KNOW that the first two values are 0
and 1. We could add some more, but these are defined to be that way, so we 
just put them into the cache.

```js
let fibonacci_cache = [0, 1];
```

Then we rewrite the function to be as follows:

```js
function fibonacci(n) {
  if (fibonacci_cache[n] != undefined) {
    return fibonacci_cache[n];
  }
  
  fibonacci_cache[n] = fibonacci(n - 1) + fibonacci(n - 2)
  return fibonacci_cache[n];
}
```

First we check if the value defined. The `undefined` keyword allows us to check
if a value is undefined, and if it's not undefined, it must be something usable.
Kowing that we have a useable value, we just return that value.

If we do not have a defined value, we compute the Fibonacci number recursively 
and first save it in the cache, than return the value from the cache. The nice
thing is that the functions we call for n-1 and n-2 will also check if they have
the value. As a result the cache gets filled quite quickly, even if you start at 
value 1000.

Aren't we missing the case for 0 and 1? Actually no, since we already put the 
values into the cache, they will always be in the cached case.

And the rest of the progam is again in it's old glory:

```js
for (let i = 0; i <= 100; i++)  {
  let fi = fibonacci(i);
  console.log(fi); 
}
```

And to prove a point, I also added this line:

```js
console.log(fibonacci(1000)); 
```

Now this concluded our lesson 2. Commit your changes and go and ask Ada what
she thinks about it.

You can see my code here: https://github.com/rioki/fibonacci
