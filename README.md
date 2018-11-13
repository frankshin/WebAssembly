# Webassembly中文版学习笔记

## 是什么

WebAssembly是一种小体积，高加载速度的二进制编码格式

WebAssembly不是用来取代JavaScript的。它被设计为和JavaScript一起协同工作，从而使得网络开发者能够利用两种语言的优势
WebAssembly设计的目的不是为了手写汇编级别代码，而是为诸如C、C++等低级源语言提供一个高效的编译目标，使得以各种语言编写的代码都可以以接近原生的速度在web中运行

AssemblyScript compiles a strictly-typed subset of TypeScript (a typed superset of JavaScript) to WebAssembly ahead of time (see: Limitations). It's not really a language on its own, though it provides several new WebAssembly-specific types and built-ins, but rather a compiler-variant for the same thing that integrates with Binaryen, Emscripten's WebAssembly backend, instead.

It's both possible to write close-to-the-metal WebAssembly as well as portable code that compiles to WebAssembly using asc and JavaScript using tsc. As the syntax is just TypeScript, existing tooling can be used in development as well (e.g. for syntax highlighting and refactoring) and common code can easily be shared between the two compilers.

Integrating with Binaryen provides rich validation, optimization (for size and/or speed) and output (WebAssembly text and binary format, asm.js, source maps) capabilities on top of that.

## 为什么

## 发展过程

## some concepts

Module: 一个“代码单元”。包含编译好的二进制代码。可以高效的缓存、共享, 未来可以像一个ES2015模块一样导入/导出
Memory: 连续的，可变大小的字节数组缓冲区。可以理解为一个“堆”
Table: 连续的，可变大小的类型数组缓冲区, 现在table只支持函数引用类型，可以类比为一个“栈”
Instance: 在Module基础上，包含所有运行时所需状态的实例, 如果把Module类比为一个cpp文件，那么Instance就是链接了dll的exe文件

wat文件：？
wasm文件：？

## 优势

- 高效，跨平台

WebAssembly是二进制的，可以直接在WebAssembly虚拟机上的机器代码（可以类比于jvm 字节码）
类比于汇编，如果机器的指令集和架构相同，则机器码可以直接执行，不关心上层os环境。Webassembly也一样能在不同平台上获得高效执行

- 沙箱化执行环境

WebAssembly被限制运行在一个虚拟的的沙箱执行环境中，运行时产生的变化可以随后删除，不会对系统产生永久性影响。并且它严格遵循浏览器的同源策略和授权策略，进一步确保了安全性

- 有文本格式，可读可调试

类比于汇编。每一条指令有对应的二进制值

- 无版本，标准化

WebAssembly是无版本，向后兼容的。这一点很有意义，相信大家在开发中也很经常碰到版本带来的一些很坑爹的问题。由于系统体积很大，依赖繁杂，且高级依赖往往不兼容低版本，造成升级时的巨大困难 
其次，WebAssembly无论是在PC端还是移动端，都支持各种浏览器平台

## 编译

目前能编译成 WebAssembly 字节码的高级语言有：

> AssemblyScript: 语法和typescript一致，为前端编写webassembly最佳选择

detail：
AssemblyScript compiles a strictly-typed subset of TypeScript (a typed superset of JavaScript) to WebAssembly ahead of time (see: Limitations). It's not really a language on its own, though it provides several new WebAssembly-specific types and built-ins, but rather a compiler-variant for the same thing that integrates with Binaryen, Emscripten's WebAssembly backend, instead.

> c/c++, 官方推荐的语言

c++从代码到浏览器中运营的执行过程如下：
![执行流程](https://smallpang.oss-cn-shanghai.aliyuncs.com/WebAssembly/005NrfBdly1fgn4gtsn7tj316o0d20td.jpg)

> Rust，语法复杂，对前端来说学习成本高

> kotlin，语法和java、js相似，语言学习成本低

> Golang，语法简单，学习成本低，但对于webassembly的支持还处在未正式发布阶段

## 一个完整的code demo

## WebAssembly应用案例分析

1、[teavm](https://github.com/konsoletyper/teavm)
> what: java bytecode to javascript compiler

2、[Figma](https://www.figma.com)
> Browser based multiplayer collaboration UI design tool

3、[Google Earth](https://www.google.com/earth/)

4、[Egret engine](https://www.egret.com/en/)

5、[Walt](https://github.com/ballercat/walt)
> 这个工具可以让开发者不用熟悉c/c++或rust，使用js就可以写出接近机器码效率的网页应用，有点意思

## 参考文档

[webassembly入门](https://blog.csdn.net/m549393829/article/details/81839822)
[8个WebAssembly应用案例](https://blog.csdn.net/fRF0lw4/article/details/79267457)
[让c代码在浏览器中运行-webassembly入门介绍](https://blog.csdn.net/sinat_32582203/article/details/73355211)