# 1. Intruduction
>This document serves as the complete definition of Google's coding standards for source code in the Java™ Programming Language. 
A Java source file is described as being in Google Style if and only if it adheres to the rules herein.

此文档作为谷歌编码规范的完整定义，用于JAVA语言编写的源代码。当且仅当一个JAVA源文件遵从此处的规则才能被称为谷歌风格。

>Like other programming style guides, the issues covered span not only aesthetic issues of formatting, but other types of conventions 
or coding standards as well. However, this document focuses primarily on the hard-and-fast rules that we follow universally, 
and avoids giving advice that isn't clearly enforceable (whether by human or tool).  

像其他的编程风格指导，议题包含的范围不仅仅是格式化的美观问题，还包含其他类型的惯例和编码标准。无论如何，此文档主要关注于我们普遍遵循的硬性规则，避免给出
一些不能被明确执行（无论是人还是工具）的建议

## 1.1 Terminology notes(术语说明)
>In this document, unless otherwise clarified:  
1.The term class is used inclusively to mean an "ordinary" class, enum class, interface or annotation type (@interface).  
2.The term member (of a class) is used inclusively to mean a nested class, field, method, or constructor; 
that is, all top-level contents of a class except initializers and comments.  
3.The term comment always refers to implementation comments. We do not use the phrase "documentation comments", 
instead using the common term "Javadoc."  
Other "terminology notes" will appear occasionally throughout the document.  

此文档中，除非除了明确说明的：
1. 类class用于表示一个普通的类、枚举类、接口或者注解类型（@interface）。
2. (类的)成员用于表示一个内嵌类、成员变量、成员方法或者构造函数；也就是，一个类除了初始化块和注释的所有顶级内容。
3. 注释一直都是指的执行注释，我们不使用短语“文档注释”，用Javadoc代替  
  
其他术语说明再后面的整个文档中都可能会出现

## 1.2 Guide notes
>Example code in this document is non-normative. That is, while the examples are in Google Style, they may not illustrate 
the only stylish way to represent the code. Optional formatting choices made in examples should not be enforced as rules.

此文档中的中的示例代码不是正式的。也就是说，那些使用谷歌风格的示例，并不表示他们是实现代码的唯一优雅方式。示例中使用可选的格式化选择不应该被强加为规则。

# 2. Source file basics
## 2.1 File Name
>The source file name consists of the case-sensitive name of the top-level class it contains (of which there is exactly one), 
plus the .java extension.

源文件的名字由它包含的（只有一个）大小写敏感的顶级类名加上.java扩展名构成。

## 2.2 File encode: UTF-8
>Source files are encoded in UTF-8. 源文件全部用utf-8编码

## 2.3 Special characters
### 2.3.1 Whitespace characters
>Aside from the line terminator sequence, the ASCII horizontal space character (0x20) is the only whitespace character that appears anywhere in a source file. This implies that:  
1.All other whitespace characters in string and character literals are escaped.  
2.Tab characters are not used for indentation.
