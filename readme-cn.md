# Webassembly中文版学习笔记

## 是什么

## 为什么

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