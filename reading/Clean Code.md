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
## Use Intenton-Revealing Names
命名要表达你的意图
## Avoid Disinformation
避免虚假信息，命名要与它的含义一致
## Make Meaningful Distinctions
命名要有区分度，比如数字后缀就是个反例
## Use Pronounceable Names
使用可以发音的命名，便于沟通交流
## Use Searchable Names
使用可搜索的命名，长名字比短名字好，可搜索的名字比常量好
## Avoid Encodings
1. Hungarian Notation(匈牙利命名，主要用于C语言场景，像JAVA类的高级语言不适用)
2. Member Prefixes(不要使用成员前缀，比如m_)
3. Interfaces and Implementations(接口不用加I前缀，实现可以加Imp后缀)
## Avoid Mental Mapping
避免心理上的映射，比如r代表url的路径部分
## Class Names
类名使用名词或名称短语，避免使用Manager，Processor，Data和Info，不清晰没有意义。不要使用动词
## Mehtod Names
方法名使用动词或动词短语，名词的话需要加上get、set或is前缀  
当构造函数重载时，使用描述参数的静态的工厂方法更佳  
## Don't Be Cute
不要命名得太聪明，带一些你自己或少部分人知道的梗，这会给其他人带来困惑。
## Pick One Word per Concept
使用同一个词表示一个抽象概念。fetch、retrieve和get，实际上是代表同样的含义，所以选一个用在所有的地方。
## Don't Pun
不要使用同一个词表示两个不同的目的。
## Use Solution Domain Names
使用解决方案领域内的术语，这样大家都懂的
## Use Problem Domain Names
使用问题领域的术语
## Add Meaningful Context
添加一些有意义的上下文，比如包名、类名、函数名或者前缀。
## Don't Add Gratuitous Context
不叫加无用的上下文。比如一个Gas station Deluxe的项目，所有类都加GSD的前缀，毫无意义。  
有时候一个简洁有力的名字更好。
## Final Words
选择一个好的名字最难的地方是它需要很好的表达能力和共有的文化背景。

# Chap3 Functions
## Small
First rule small, second rule be smaller than that.  
函数的大小不要超过一屏，越小越好

## Blocks and Indenting
在if、else、while等语句中的代码块应该只有一行，最好抽象成一个函数

## Do One Thing
FUNCTIONS SHOULD DO ONE THING.THEY SHOULD DO IT WELL.THEY SHOULD DO IT ONLY.  
只干一件事的函数是不能被合理的分成多个部分的

## One Level of Abstraction per Function
每个函数要使用同一水平的抽象  

## Reading Code from Top to Bottom: The Stepdown Rule
自顶向下，由粗到细的拆解

## Switch Statements
避免switch语句的重复。可以使用多态来隐藏实现逻辑，将实现逻辑都封装到各个子类中。

## Use Descriptive Names
使用可描述性的名字。函数越小越专注，那么它就越容易去起一个描述性的名字。不要害怕起长名字。长名字好于长注释。  
不要害怕花时间在起名字上。起名字时使用同样的短语、名字和动词。

## Function Arguments
理想的参数数量是0个，然后依次是1个，2个。如果可能的话三个参数的情况要避免。超过3个参数的情况就要严格的审视。  
参数会增加使用者的难度，也会增加测试者的难度。  
输出参数比输入参数更难理解，我们一般习惯于通过返回值来输出。  

## Common Monadic(单值) Forms
单参数函数有两种常见的理由:  
1. 询问一个关于参数的问题：boolean fileExists("MyFile")
2. 对这个参数进行操作，转换成别的什么，然后返回它: InputStream fileOpen("MyFile")  

你要选择能清晰区别这两种的名字  
还有一种不通用但是很有用的单参数函数：事件。有一个参数但是没有返回值: void passwordAttemptFailedNtimes(int attempts)  
一定要遵循上面这几种函数形式，不要混用  

## Flag Arguments
flag参数很丑陋。它意味着函数肯定做了至少两件事。建议把它拆分成2个函数。

## Dyadic(双值) Functions
双值函数不可避免，但是你应该尽可能把他们转换为单值函数。  
比如writeField(output-Stream, name)就有两种方式变成单值函数:  
1. 把writeField(name)方法作为output-Stream的成员方法
2. 创建一个新类，把output-Stream作为成员变量，writeField(name)作为成员方法

## Triads(三值)
三参数函数十分难懂。在创建三值函数时一定要三思而后行。  
例如：可以考虑重载assertEquals(message, expected, actual)函数

## Argument Objects
可以通过创建对象来减少参数，合理得对象创建可以让你更好理解

## Argument Lists
有时我们需要传一个数量可变得参数到函数。
如果那些可变得参数时等同的，我们可以考虑如下方式：
```
    public String format(String format, Object... args)
```

## Verbs and Keywords
选择一个好的函数名字十分有利于解释函数的意图和参数的顺序与意义。  
单参数函数可以使用动词/名词对：writeField(name)  
在函数名中使用关键词有时候也是一个好主意  
比如把参数名放到函数名中：assertExpectedEqualsAcutal(expected, actual)  
这样就解决了参数顺序混淆的问题

## Have No Side Effects
副作用是谎言，函数承诺做一件事，但是它还做了别的隐藏的事情。有时候它还会带来非期望的变化。

## Output Arguments
除非必要，一般而言输出参数要避免
```java
appendFooter(s)    //bad
report.addpendFooter()   //good
```

## Command Query Separation
函数要么做什么事情，要么回答什么问题，而不是两者都有。要么你的函数改变了对象的状态，要么返回了对象的什么信息。  

## Prfer Exceptions to Returning Error Codes


