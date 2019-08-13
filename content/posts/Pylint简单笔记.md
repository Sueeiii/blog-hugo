---
title: "Pylint简单笔记"
date: 2019-08-14T00:37:19+08:00
draft: false
categories: 
- Python学习
tags: 
- Python
- Pylint
- 笔记
---

## pylint（Python语言规范（google））       

异常:
    　尽量减少try/except快中的代码量。try块的体积越大，期望之外的异常就越容易被触发。
    　永远不要使用except语句来捕获所有异常，也不要捕获Exception或者StanderError。会很容易隐藏真正的bug。
    　当捕获异常时，使用as而不要使用逗号。      
    
<!-- more -->

全局变量：
　　避免全局变量，偶有有用。
　　例外：
　　　　１、脚本的默认选项。
　　　　２、模块极常量：例：PI＝３.14159，常量应该全大写，用下划线链接。
　　　　３、有时候用全局变量来缓存值或者作为函数返回值很有用。
　　　　４、如果需要，全局变量应该仅在模块内部可用，并通过模块级的公共函数访问。

默认参数值：
　　不要在函数或方法中使用可变对象作为默认值。


True/False：
　　尽可能使用隐式False
　　永远不要用==或者!=来比较单件，比如None，使用is或者is not。
　　处理整数时，使用隐式False可能会得不偿失，你可以将一个已知是整型但不是len()的返回结果与０比较。


语法作用域：
　　嵌套的Python函数可以引用外层函数中定义的变量，但是不能够对它们赋值。


行长度：
　　每行不超过８０个字符（圆括号，中括号，花括号中的行隐式的链接起来）。
　　如果一个文本字符串在一行放不下，可使用圆括号来实现隐式行链接。
　　如：x = ('This will build a very long long'
　　　　　　'long long long long long long long string')
　　在注释中，如有必要，将长的URL放在一行上。

括号：
　　除非是用于实现行链接，否则不要在返回语句或条件语句中使用括号，不过在元祖两边使用括号是可以的。
　　


大部分py文件不必以#!作为文件的开始，根程序的main文件应该以#!/usr/bin/python2或者#!/usr/bin/python3开始。

为了提高可读性，注释应该至少离开代码两个空格。
如：
　　if i & (i - 1) == 0:          # true if i is a power of 2.

可将字符串加入列表中，使用.join()将字符串连接起来。


文件与sockets：
　　在文件和sockets结束时。显式的关闭它。
　　推荐使用with语句来管理文件。
　　对于不支持使用“with”语句的类似文件的对象，使用contextlib.closing()。