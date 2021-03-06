---
layout: page
title: "有关副作用的思考"
description: ""
---
{% include JB/setup %}


软件开发自诞生以来一直以其复杂性困扰者一代有一代的程序员。对于绝大部分的程序而言，其复杂性在于各种业务逻辑交织缠绕在一起使人难以理解，当程序规模越来越大之后，程序的复杂性更是成指数级别上涨，这对想要理解这些程序的开发人员而言构成了巨大的挑战。程序复杂性的根源何在呢，我想可能与副作用相关。

### 副作用
函数副作用的定义如下：

    计算机领域，函数的副作用指当调用函数时，除了返回函数值之外，还对主调用函数产生附加的影响。


试想一下，如果一段程序的每个函数都有副作用，甚至没有函数，那么副作用贯穿整个程序的任何角落，那么要理解这段程序时，我们需要看完程序的每一个函数，每一行代码，记住每个对中对程序状态的点，才能完全理解这段程序，这极大增大了程序员理解和记忆的负担。相反对于一个完全没有副作用的程序，我们可以只了解其中每个函数的大概的功能，即可理解程序的作用。
<br/>

### 三种设计思想
下面我们看看三种程序设计思想(面向过程，面向对象，函数式)是如何面对这一问题的

#### 面向过程
面向过程主要是要求将代码分割成函数，在分割的过程中，一些无需贯穿始终程序状态被分散在各个函数中，变成了函数中得局部状态，减少了代码中全局状态的数量，使得代码的复杂性大大降低。

#### 面向对象
面向对象提出了封装的概念，明确地要求将副作用封装的一个较小的范围(类)中，以此减少副作用的影响

#### 函数式编程
函数式编程要求每个函数中尽量避免副作用，每个函数的结果都通过返回值给出。
<br/>
然而我们却无法完全禁止副作用的产生，因为没有副作用我们的程序恐怕无法实现任何功能，例如，开打一个文件的操作势必会改变操作系统中该文件的状态，并间接对其他代码或者程序产生影响

### 对我们的意义
1. 编写代码时尽量避免副作用
2. review代码时，对有副作用的模块要重点review
3. 最好能有对代码的副作用进行评价的工具，作用代码质量的一个指标
