# Chap1. Clean Code
>*I like my code to be elegant and efficient. The
logic should be straightforward(简单的、率直的) to make it hard
for bugs to hide, the dependencies minimal to
ease maintenance, error handling complete
according to an articulated(明确表达的) strategy, and performance close to optimal(最优的) so as not to tempt(引诱，鼓动)
people to make the code messy(凌乱的) with unprincipled(不道德的) optimizations(最优选择). Clean code does one thing
well.*&nbsp;&nbsp;&nbsp;&nbsp;             --Bjarne Stroustrup(Author of C++)  

>*Clean code is simple and direct. Clean code
reads like well-written prose(散文). Clean code never
obscures(使隐晦，使费解) the designer’s intent but rather is full
of crisp(洁净的) abstractions(抽象) and straightforward lines
of control.* &nbsp;&nbsp;&nbsp;&nbsp;     --Grady Booch(Author of Object Oriented Analysis and Design with Applications)  

>*Clean code can be read, and enhanced by a developer other than its original author. It has
unit and acceptance tests. It has meaningful names. It provides one way rather than many
ways for doing one thing. It has minimal dependencies, which are explicitly(明确的) defined, and provides a clear and minimal API. Code should be literate(文学的) since depending on the language, not all
necessary information can be expressed clearly
in code alone* &nbsp;&nbsp;&nbsp;&nbsp; --“Big” Dave Thomas(founder of OTI,godfather of the Eclipse strategy )  

>*I could list all of the qualities(高标准) that I notice in
clean code, but there is one overarching(首要的) quality
that leads to all of them. Clean code always
looks like it was written by someone who cares.
There is nothing obvious(明显的) that you can do to
make it better. All of those things were thought
about by the code’s author, and if you try to
imagine improvements, you’re led back to
where you are, sitting in appreciation of the
code someone left for you—code left by someone who cares deeply about the craft.* 
&nbsp;&nbsp;&nbsp;&nbsp; --Michael Feathers(author of Working Effectively with Legacy Code)  

>*In recent years I begin, and nearly end, with Beck’s rules of simple code. In priority order, simple code:  
1 Runs all the tests;  
2 Contains no duplication;  
3 Expresses all the design ideas that are in the system;  
4 Minimizes the number of entities such as classes, methods, functions, and the like.  
&nbsp;&nbsp Of these, I focus mostly on duplication. When the same thing is done over and over,
it’s a sign that there is an idea in our mind that is not well represented(代表) in the code. I try to
figure out what it is. Then I try to express that idea more clearly.  
&nbsp;&nbsp;Expressiveness(表达力) to me includes meaningful names, and I am likely to change the
names of things several times before I settle in. With modern coding tools such as Eclipse,
renaming is quite inexpensive(不昂贵的), so it doesn’t trouble me to change. Expressiveness goes 
beyond names, however. I also look at whether an object or method is doing more than one
thing. If it’s an object, it probably needs to be broken into two or more objects. If it’s a
method, I will always use the Extract Method refactoring(重构) on it, resulting in one method
that says more clearly what it does, and some submethods saying how it is done.  
&nbsp;&nbsp;Duplication and expressiveness take me a very long way into what I consider clean
code, and improving dirty code with just these two things in mind can make a huge difference. There is, however, one other thing that I’m aware of doing, which is a bit harder to explain.  
&nbsp;&nbsp;After years of doing this work, it seems to me that all programs are made up of very
similar elements. One example is “find things in a collection.” Whether we have a database of employee records, or a hash map of keys and values, or an array of items of some
kind, we often find ourselves wanting a particular item from that collection. When I find
that happening, I will often wrap the particular implementation in a more abstract method
or class. That gives me a couple of interesting advantages.  
&nbsp;&nbsp;I can implement the functionality(功能) now with something simple, say a hash map, but
since now all the references to that search are covered by my little abstraction, I can
change the implementation any time I want. I can go forward quickly while preserving(保留，维持) my
ability to change later.  
&nbsp;&nbsp;In addition, the collection abstraction often calls my attention to what’s “really”
going on, and keeps me from running down the path of implementing arbitrary(任意的，随心所欲的) collection
behavior when all I really need is a few fairly simple ways of finding what I want.  
&nbsp;&nbsp;**Reduced duplication, high expressiveness, and early building of simple abstractions.**
That’s what makes clean code for me.*  
&nbsp;&nbsp;&nbsp;&nbsp; --Ron Jeffries(author of Extreme Programming Installed and Extreme ProgrammingAdventures in C#)
  
>*You know you are working on clean code when each
routine(例程) you read turns out to be pretty much what
you expected. You can call it beautiful code when
the code also makes it look like the language was
made for the problem.*  
&nbsp;&nbsp;&nbsp;&nbsp;--Ward Cunningham(inventor of Wiki, inventor of Fit, coinventor of eXtreme Programming)
  
  
# Chap2. Meaningful Names

