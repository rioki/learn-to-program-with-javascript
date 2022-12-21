# Lesson 0: Setting up Your Environment

In this "lesson" I will talk you though setting up your programing environment.
We could be using one of the many online programing environments, but you
will quickly learn that, except for quick experiments, these are not a feasible
option to get things done. So in this vain, we will set up and environment 
on your machine locally.

*lie to children*: I have chosen tools that are both effective and sufficiently 
simple to use for a novice. There obviously are more in depth tools. In
some cases, such as *github for desktop*, they are just nice UIs around powerful
command line tools. It makes sense to learn these tools at some point, but
for now this would just be a waste of time.

## Browser: Chrome

As we will be building something for the web, you obviously need a web browser. 
You probably already have one and that is fine. I will use [Chrome], because
of it's well designed developer tools. Other browser also have quite capable
developer tools, but I will not take the time to address these.

[Chrome]: https://www.google.com/chrome/

## Editor: Visual Studio Code

The choice of editor can spark religious wars, but we need a capable editor. 
Here we will be using [Visual Studio Code], as it a power full but also simple 
editor.

[Visual Studio Code]: https://code.visualstudio.com/

## Version Control: GitHub

Every programmer needs version control. It a means to store versions and look 
back into the past. You don't **need** it to learn to program, but it is a good
idea and will save you allot of hair pulling when you broke your program and
don't know why.

We are using git, but since git is a complicated system, we will use a user 
friendly wrapper [GitHub]. GitHub comes in two bits, a service that allows you 
to store your changes online and thus never loose them, even when your computer
dies or share them with others, like this tutorial.
To work with changes locally we will use [GitHub for Desktop]. 

You should create an account with GitHub, it's free. The free account is has
limited capabilities, but for now that is ok.

[GitHub]: https://github.com/
[GitHub for Desktop]: https://desktop.github.com/

## Execution Environment: node.js

[node.js] is a Java Script execution environment that allows you to run Java 
Script directly on your machine. This is tha backbone for many web services
that are implemented in Java Script.

Although we will focus mostly on browsers, we will use node.js for some mall
examples and some small tools. You should make sure that you als install npm, 
the node package manager; but that should be the case if you just run the 
installer by just clicking next all the time.

[node.js]: https://nodejs.org/en/

If you installed all the above software, you should be ready to go for the
next Lesson where we talk about Syntax.