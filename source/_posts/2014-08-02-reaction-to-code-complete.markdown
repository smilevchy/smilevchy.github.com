---
layout: post
title: "Reaction to &lt;Code Complete&gt;"
date: 2014-08-02 15:25:54 +0800
comments: true
categories: Reaction
---

终于把 \<Code Complete\>.2nd 读完了，1000多页的量。由于是电子版的，因此没有那种一看到很厚的一本书就被吓倒的感觉，但也少了那种消灭完一本大书的成就感。

以下是自己对一些有趣的章节的简短的笔记流记录......

<!-- more -->


*Guidelines about ADT*

1. 把常见的底层数据类型创建为 ADT 并使用这些 ADT, 而不再使用底层数据类型
2. 把像文件这样的常用对象当作 ADT
3. 简单的事物也可当作 ADT
4. 不要让 ADT 依赖于其存储介质


*Thinking about Class*

Class is based on definition of ADT


*Defensive Programming*

1. 检查所有非法输入数据
2. 使用 Assertions
3. Error-Handling Techniques
    * 返回中立值
	* 换用下一个正确的数据
	* 返回与前次相同的数据
	* 换用最接近的合法值
	* 把警告信息记录到日志文件中
	* 返回一个错误码
	* 调用错误处理子程序或对象
	* 当错误发生时显示出错误消息
	* 用最妥当的方式在局部处理错误
	* 关闭程序
4. Compromise between Robustness and Correctness
5. 隔离程序，使之包容由错误造成的损害
    > 选择某些接口作为安全区域的边界，对穿越安全区域边界的数据进行合法性校验
	> 当数据非法时做出相应的反映；
	> 输入数据时将其转换为恰当的类型
6. 使用调试助手（辅助调试的代码）
7. 使用进攻式编程
8. 避免过度防御式编程


以下是一部分整理的此书所推荐的书籍简短记录......


*Fault Tolerance*

1. IEEE Software 2001.07
2. Agile Database Techniques (Ambler 2003)
3. On the design and development of program families (Parnas 1976)


*Software Design, General*

1. The Object-Oriented Thought Process
2. Object-Oriented Design Heuristics
3. __Programming on Purpose: Essays on Software Design (Plauger)__
4. The Art of UNIX Programming


*Software Design Theory*

1. A Rational Design Process: How and Why to Fake it (Parnas)
2. On the Criteria to Be Used in Decomposing Systems into Modules
3. Designing Software for Ease of Extension and Contraction (Parnas 1979)
4. The Modular Structure of Complex Systems


*Design Patterns*

1. Design Patterns Explained


*Design in General*

1. Conceptual Blockbusting: A Guide to Better Ideas (Adams 2001)
2. How to Solve It: A New Aspect of Mathematical Method
3. How to Solve It: Modern Heuristics
4. The Sciences of the Artificial
5. Software Creativity


*Assorted*

1. Pragmatic Programmer
2. Applied UML and Patterns
3. Fundamentals of Object-Oriented Design in UML
4. High Output Management
5. Test-Driven Development: By Example (Beck)
6. Software Engineering Metrics and Models
7. C Programming Guidelines (Plum)
8. The Elements of Java Style
9. Professional Software Development
10. Principles of software Engineering
11. Design and Code Inspections to Reduce Errors in Program Development
12. The Psychology of Computer Programming
13. Managing the Software Process
14. Refactoring: Improving the Design of Existing Code
15. Rapid Development 
16. Code Reading: The Open Source Perspective
17. Programmers at Work


*Classes in General*

1. __Object-Oriented Software Construction__
2. Effective Java Programming Language Guide


*Defensive Programming*

1. Assertions
    * Writing Solid Code(Maguire)
2. Secure
    * Writing Secure Code
	
	
*Data Structure*

1. Introduction to Algorithms (Cormen,H.Thomas, Charles E.Leiseron, Ronald L.Rivest)
2. Algorithms in C++ (Sedgewick, Robert), Parts 1-4, Parts 5
3. Algorithms in Java, Parts 1-4
4. Algorithms in Java, Parts 5


*Software Complexity*

1. A Complexity Measure (Tom McCabe)
2. Software Engineering Metrics and Models 


*Software Testing*

1. Testing Computer Software
2. Lessons Learned in Software Testing
3. Introducing Software Testing
4. How to Break Software : A Practical Guide to Testing
5. What is Software Testing? And Why Is It So Hard?
6. The Art of Software Testing
7. Test-Driven Development: By Example
8. Bug Patterns in Java


*Performance Tuning*

1. Performance Solutions: A Practical Guide to Creating Responsive, Scalable Software
2. "Optimization: Your Worst Enemy" (http://www.flounder.com/optimization.htm)
3. __Writing Efficient Programs__
4. Web Performance Tuning
5. Java Performance Tuning
6. Java Platform Performance: Strategies and Tactics


*Programming Tools*

1. www.sdmagazine.com/jolts <Software Development Magazine>


*Program Style*

1. The Practice of Programming
2. The Elements of Java Style
3. __The Elements of Programming Style__
4. __Literate Programming__


*Personal Characteristics*

1. The Humble Programmer
2. The Psychology of Computer Programming: Silver Anniversary Edition
3. Tutorial: Human Factors in Software Development


*Software Engineering*

1. Facts and Fallacies of Software Engineering
2. Professional Software Development
3. The Mythical Man-Month
4. PeopleWare
5. __Software Creativity__
6. Software Engineering: A Practitioner's Approach
7. Software Engineering (Ian Sommerville)
	


