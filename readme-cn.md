# Webassembly中文版学习笔记

## 是什么

WebAssembly是一种小体积，高加载速度的二进制编码格式

WebAssembly不是用来取代JavaScript的。它被设计为和JavaScript一起协同工作，从而使得网络开发者能够利用两种语言的优势 
WebAssembly设计的目的不是为了手写汇编级别代码，而是为诸如C、C++等低级源语言提供一个高效的编译目标，使得以各种语言编写的代码都可以以接近原生的速度在web中运行

## 为什么

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

## Webassembly优缺点

## 当前转译现状

目前能编译成 WebAssembly 字节码的高级语言有：

- AssemblyScript: 语法和typescript一致，为前端编写webassembly最佳选择

detail：
AssemblyScript compiles a strictly-typed subset of TypeScript (a typed superset of JavaScript) to WebAssembly ahead of time (see: Limitations). It's not really a language on its own, though it provides several new WebAssembly-specific types and built-ins, but rather a compiler-variant for the same thing that integrates with Binaryen, Emscripten's WebAssembly backend, instead.

- c/c++, 官方推荐的语言

- Rust，语法复杂，对前端来说学习成本高

- kotlin，语法和java、js相似，语言学习成本低

- Golang，语法简单，学习成本低，但对于webassembly的支持还处在未正式发布阶段

## What exactly is AssemblyScript

AssemblyScript compiles a strictly-typed subset of TypeScript (a typed superset of JavaScript) to WebAssembly ahead of time (see: Limitations). It's not really a language on its own, though it provides several new WebAssembly-specific types and built-ins, but rather a compiler-variant for the same thing that integrates with Binaryen, Emscripten's WebAssembly backend, instead.

It's both possible to write close-to-the-metal WebAssembly as well as portable code that compiles to WebAssembly using asc and JavaScript using tsc. As the syntax is just TypeScript, existing tooling can be used in development as well (e.g. for syntax highlighting and refactoring) and common code can easily be shared between the two compilers.

Integrating with Binaryen provides rich validation, optimization (for size and/or speed) and output (WebAssembly text and binary format, asm.js, source maps) capabilities on top of that.

## 参考文档

[webassembly入门](https://blog.csdn.net/m549393829/article/details/81839822)