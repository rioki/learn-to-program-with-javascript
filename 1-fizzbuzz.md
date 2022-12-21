# Lesson 1: Basic Syntax

In this lesson I will show you how to get started and some basic Java Script.

We will be writing a small program called Fizz Buzz. This is a common programing
exercise to ensure the programer you want to hire can actually program. This
quite a simple program and so it is the perfect example to getting started.

## Fizz Buzz

Fizz Buzz is a game children play. The rules are as follows:

* starting at one you count up, our program will count to 100.
* each time the number is divisible by 3 we will print Fizz
* each time the number is divisible by 5 we will print Buzz
* each time the number is divisible by 3 and 5 we will say Fizz Buzz
* if the number is neither divisible bt 3 or 5 we will print the number

So for example the first couple of numbers will look as follows:

```
1
2
Fizz
4
Buzz
Fizz
7
8
Fizz
Buzz
11
Fizz
13
14
Fizz Buzz
```

## Setting Up Your Project

Now this may be overkill, but I want you to use version control for everything.
This is a good idea, because this allows you to see what you did and if you ever
get stuck you can roll back to a sate that worked, by just undoing the current 
changes.

In this vain open GitHub for Desktop. If you open it for the first time you
probably will be asked to log in. This is the account you created with GitHub 
in [lesson 0](../lesson0/README.md).

To create a new repositoy, that is a project under version control is called,
you use "File" and "New repository". We will call the repository fizzbuzz and put 
that into the Name" field. We will keep all other settings as is. If you like 
you can change the "Description" and "Local path", but the defaults are fine for now.
Don't worry you can change everything later

Now that you created the repository, how do you find it. Either you remember
what was in "Local path" or you use "Repository" and "Show In Explorer". 

Once you found your empty project, you can have a look around. There is a hidden
folder `.git` and a file called `.gitattributes`. For now we will ignore that. 
For the next step open the folder in VS Code. This can be done with right mouse
click into the folder and "Open with Code". 

If you really feel lazy, you can just use "Repository" and 
"Open in Visual Studio Code".

## Hello World

For a start we will create a file called `fizzbuzz.js`. This will contain our
program.

In this file write the following:

```js
console.log('Hello World');
```

This is our first program. What it does is, it will print `Hello World` onto
the command line. I will skipp over some details here, but just remember 
`console.log` is the means to quickly output some debug or diagnostic information
that you can use to figure out issues about your program. At a later stage we
will look into actually using a debugger, but for now we will just work 
`console.log` which is a quick way to understand programs.

How do we run the program? 

Visual Studio Code has at the bottom hidden pannel that you can pull up. This
contains the tab "TERMINAL". We will use that to run the program. Obviously
you can also open a terminal window directly and do the same thing there 
but this is a but more convenient, as we see and output and the code at the 
same time. 

To run the program type:

```
node fizzbuzz.js
```

The output should look something like this:

```
C:\Users\seanf\Documents\GitHub\fizzbuzz>node fizzbuzz.js
Hello World

C:\Users\seanf\Documents\GitHub\fizzbuzz>
```

As you can see it wrote `Hello World`, wich is not very suprising given the 
program.

Now commit you changes. That is, save the current state into version control. 
Change back to Github for Desktop and write something into the filed 
"Summary (required)", such as "Wrote Hello World program" and hit the button
"Commit to main". Now the changes have been committed and you can see them in
the history tab.

## Strings

Text in a program is denotes by quotes. In Java Script you may see both single
quotes, like `'Example'` or double quotes, like `"Example"`. In Java Script 
this is the same thing. As long as you use the same type of quote on the opening
and closing of the text, you are fine. Text is marked like this so the compiler
knows what is program code and what is just some text.

Bits of text are called a string. I will not go into detail why that is the case,
but on a high level text is a "string of characters", that is individual letters.

So if I say string, I mean a small bit of text. We will get into more detail
on strings later, but for now just understand that `'Hello World'` is a string
that we pass to the `log` function. 

## Variables

In any program that does something sensible, you nee to store information. 
One piece of information, is stores in something we call a variable. It is 
variable, because we can change it. A variable is creates like so:

```js
let a = 1;
```

You can think of it as "let a have the value 1". 

*lie to children*: In addition to `let` it also exists `var` and `const`. 
If you ever see code with either `var` or `const`, just pretend it's `let`. 

The nice thing about variables is that you can do something with them, 
for example you can do math. Take the following small program:

```js
let a = 1;
let b = 2;
let c = a + b;

console.log(c);
```

To play around, just replace the contents of `fizzbuzz.js` with the above 
code and execute it in the terminal with `node fizzbuzz.js`. (Don't forget
to save the file `fizzbuzz.js`.)

The output should not be:

```
C:\Users\seanf\Documents\GitHub\fizzbuzz>node fizzbuzz.js
3

C:\Users\seanf\Documents\GitHub\fizzbuzz>
```

You don't have to create a new variable for each new value, you also change
existing values, like so:

```js
let a = 1;
let b = 2;
a = b + 2

console.log(a);
```

The output should not be:

```
C:\Users\seanf\Documents\GitHub\fizzbuzz>node fizzbuzz.js
4

C:\Users\seanf\Documents\GitHub\fizzbuzz>
```

Now that we understood what how variables work on a basic level, we will undo 
our changes, since the previous state of the program is a bit closer
to Fizz Buzz than the current one.

To undo the changes go to GitHub for Desktop and richt click "fizzbuzz.js" and
select "Discard changes". You will see a pop up asking you if you are certain 
you want to discard the changes and with great certainty select "Discard changes".

Now your program `fizzbuzz.js` is back to:

```js
console.log('Hello World');
```

## Let's Start

Ok, let's start to actually write Fizz Buzz:

```js
console.log('1');
console.log('2');
console.log('Fizz');
console.log('4');
console.log('Buzz');
console.log('Fizz');
console.log('7');
console.log('8');
console.log('Fizz');
console.log('Buzz');
console.log('11');
console.log('Fizz');
console.log('13');
console.log('14');
console.log('Fizz Buzz');
```

And if you run the program you will get:

```
C:\Users\seanf\Documents\GitHub\fizzbuzz>node fizzbuzz.js
1
2
Fizz
4
Buzz
Fizz
7
8
Fizz
Buzz
11
Fizz
13
14
Fizz Buzz

C:\Users\seanf\Documents\GitHub\fizzbuzz>
```

Almost there, right? 

For 15 entires this is quite simple to do, but what about 100 or even 1000?
You quickly will see that this is not feasible. We need to write a program 
that can count to an arbitrary number.

You should commit these changes, since we got a bit closer to our goal.

## Loops

Since Fizz Buzz is outside of our capabilities, let's just write a program that
can count to 100. To do this we will use a loop, a while loop to be specific.

```js
let i = 1;
while (i <= 100)  {
  console.log(i);
  i = i + 1;
}
```

In this program we create a variable `i`, this will be our counter, or index. 
Remember math, where the count variables i, j and k are used? We programers
do the same thing. Normally we take care to name our variables something sensible,
but i, j, and k are automatically assumed to tbe counters.

We set i to 1, since the first value we need to output is a 1. 

Then we have a while loop. The keyword `while` tells the compiler that we will 
now have a loop and everything within the curly braces will be repeated, as 
long as the condition inside the round braces is true. 

As long a the variable i is less or equals 100, the program will output
the current value and then add 1 to the counter.

And the output looks like so:

```
C:\Users\seanf\Documents\GitHub\fizzbuzz>node fizzbuzz.js
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30
31
32
33
34
35
36
37
38
39
40
41
42
43
44
45
46
47
48
49
50
51
52
53
54
55
56
57
58
59
60
61
62
63
64
65
66
67
68
69
70
71
72
73
74
75
76
77
78
79
80
81
82
83
84
85
86
87
88
89
90
91
92
93
94
95
96
97
98
99
100

C:\Users\seanf\Documents\GitHub\fizzbuzz>
```

Wow, it can count until 100 and that is allot of output. From now on, I will
trim the output. Just use you judgement if the output is correct or not. 

*lie to children*: There are more types of loops. A common one is the for loop
but more on that later.

This is one step closer to Fizz Buzz, so commit the changes.

## Conditionals

This is all fine and well, we can count to 100, but we need to call out Fizz
and Buzz at the right time.

To do that we need to make a decision. To do that we use an "if / else" statement.

Let's check for Fizz, that is is the number divisible by 3. But before we can
get to programing, we need to think about how can we check if a number is 
divisible by 3, with math? 

A number is divisible by 3, when the result of the division is a while number
or in other words, the remainder is 0. In this vain, we have a special operator
that will only compute the remainder, the modulo operator. The modulo operator
is denoted with the `%` sign. So if you see the percent sign in a program, 
it's modulo, not percent... I know it's a but confusing.

```js
let i = 1;
while (i <= 100)  {
  if (i % 3 == 0) {
    console.log('Fizz');
  }
  else {
    console.log(i);
  }
  i = i + 1;
}
```

We add a if block in which we check if the number if divisible by 3 and then 
output Fizz, if that is not the case we have an else block that will just 
output the number as before.

And the output is:

```
C:\Users\seanf\Documents\GitHub\fizzbuzz>node fizzbuzz.js
1
2
Fizz
4
5
Fizz
7
8
Fizz
10
11
Fizz
13
14
Fizz
16
```

Not bad. 

This is one step closer to Fizz Buzz, so commit the changes.

## More Conditionals

Lets add Buzz to the program:

```js
let i = 1;
while (i <= 100)  {
  if (i % 3 == 0) {
    console.log('Fizz');
  }
  else if (i % 5 == 0) {
    console.log('Buzz');
  }
  else {
    console.log(i);
  }
  i = i + 1;
}
```

As you can see you can chain if / else blocks. This allows us to check more than
one condition, this is what we call an "else if".

The output is as follows:

```
C:\Users\seanf\Documents\GitHub\fizzbuzz>node fizzbuzz.js
1
2
Fizz
4
Buzz
Fizz
7
8
Fizz
Buzz
11
Fizz
13
14
Fizz
16
```

Not bad. Have you spotted the bug? 15 should be Fizz Buzz, not just Fizz. We
will get to this next.

This is one step closer to Fizz Buzz, so commit the changes.

*lie to children*: The construct "else if" does not exist. Its actually a 
special case of `if () {} else {if () {}}`. We can omit the curly braces 
for single line if and else blocks, but except for "else if" this it 
not a good idea and a source for many bugs.

## Boolean Operators

As you can see 15 is "Fizz" and not "Fizz Buzz". But why? 

If you look at the program, you can see we first check of division by 3, then
division by 5. If a number if divisible 3, it will output Fizz and not check 
anything further. 

We need to add the case where the number if divisible by 3 and divisible by 5.

To do this, we use boolean operators and to be specific we will use the and
operator that is denoted by `&&`.

Here is the program:

```js
let i = 1;
while (i <= 100)  {
  if ((i % 3 == 0) && (i % 5 == 0)) {
    console.log('Fizz Buzz');
  }
  else if (i % 3 == 0) {
    console.log('Fizz');
  }
  else if (i % 5 == 0) {
    console.log('Buzz');
  }
  else {
    console.log(i);
  }
  i = i + 1;
}
```

