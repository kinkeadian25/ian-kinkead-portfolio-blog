---
title: Crafting Interpreters by Robert Nystrom - The Introduction
description: My journey through the introduction of book "Crafting Interpreters" and the insights I gained on creating a programming language.
topic: Learning How to Create A Programming Language - Reena
date: April 8, 2024
---

I recently decided to embark on a mission of creating a programming language. I not only want to do this just because I have always wanted to do it, but now that I have most of the core principles of full-stack and distributed systems development down. I believe this is a natural next step to becoming a much stronger programmer within these forms of development and others. Also, I just love computers.

I decided to start this journey by reading "Crafting Interpreters". This book is a comprehensive guide on implementing interpreters and compilers for programming languages and also provides insights on designing a language worth implementing. It's the book I wish I had when I first started getting into languages by working on the open-source project Roslyn.

## Chapter 1: Introduction

As I embarked on my journey of creating a programming language with this book, I was struck by the prevalence of "little languages" or "domain-specific languages" that were covered in the introduction. I thought I knew of a lot of them, but they really are somewhat neverending! While it's often more efficient to reuse an existing language, there are instances where crafting a custom parser or tool is necessary, and I want to be capable of that! This process, though intricate, is a testament to a programmer's skill and understanding of data structures and algorithms.

The book opens with a powerful quote from G.K. Chesterton, "Fairy tales are more than true: not because they tell us that dragons exist, but because they tell us that dragons can be beaten." This quote really makes sense for this task, encapsulating the essence of learning - the courage to face challenges and the triumph of overcoming them. Implementing a language is akin to training with weights or at high altitudes as far as programming is concerned in my opinion - it's a rigorous test of endurance and skill that leaves you stronger and more knowledgeable. There are great lessons to learn from the past, but at the end of the day you are creating your own way of talking to the computer, so there will not be documentation to support you the whole way.

I can already tell there are unique techniques and challenges involved, but they're not insurmountable. We learn everyday that something once thought impossible with computers is very much possible. This introduction not only demystified the process of language creation for me but also instilled a newfound confidence in my abilities as I realized how much of it I understood or had familiarity with!

### Scanning and Parsing

The introduction also covered the concepts of scanning and parsing. Scanning, also known as lexing, chunks together a linear stream of characters into a series of "words" or tokens. Parsing, on the other hand, takes these tokens and builds a tree structure that mirrors the nested nature of the grammar. This terminology was familiar to me due to the syntax trees in Roslyn but definitely still took a couple reads. The first 100 pages as a whole took a couple reads, but I enjoyed it every time!

### Static Analysis: Binding, Resolution, and Type Checking

The book soon delves into static analysis, a stage where the individual characteristics of each language start coming into play. At this point, we know the syntactic structure of the code, but we don't know much more than that. For example, in an expression like `a + b`, we know we are adding `a` and `b`, but we don’t know what those names refer to. Are they local variables? Global? Where are they defined?

This is where the process of binding or resolution comes in. For each identifier, we find out where that name is defined and wire the two together. This is where scope comes into play—the region of source code where a certain name can be used to refer to a certain declaration. This process was a bit challenging to grasp at first, but the book does an excellent job of explaining it in a clear and concise manner.

If the language is statically typed, this is when we type check. Once we know where `a` and `b` are declared, we can also figure out their types. Then if those types don’t support being added to each other, we report a type error. The language I am learning to build in this book is dynamically typed, so it will do its type checking later, at runtime.

### Intermediate Representations and Optimization

The book then takes you into the heart of the compiler - the transformation of the tree into a new data structure that more directly expresses the semantics of the code. This is where the magic happens, where the code is organized in a way that makes the next stage simpler to implement.

The book introduces the concept of an intermediate representation (IR), a form of the code that isn't tightly tied to either the source or destination forms. The IR acts as an interface between the source language and the final architecture where the program will run. This concept was not a revelation to me, but I knew nothing about how these things worked before today. It allows for the support of multiple source languages and target platforms with less effort. For example, if you want to implement Pascal, C, and Fortran compilers, and you want to target x86, ARM, and SPARC, you would normally have to write nine full compilers. But with a shared IR, you only need to write one front end for each source language that produces the IR, and one back end for each target architecture.

The book also delves into optimization, the process of transforming the user's program into a more efficient form while preserving the same semantics. A simple example given is constant folding, where an expression that always evaluates to the same value is evaluated at compile time and replaced with its result.

These concepts were not only fascinating but also gave me a deeper understanding of how compilers work. It was like peeling back the layers of an onion, each layer revealing a new level of complexity and elegance.

### Thoughts So Far

I am just so thrilled to be reading this book! Now that I am done with school, I can finally embark on this journey that I decided I needed to accomplish after my first Console.WriteLine("Hello World") when I decided to teach myself C#. Now that I have the intro done, it is time to start creating Lox first as jlox with Java, and then clox with C!

Once I have completed this book, I am going to buy a couple more and use them along the way to help me build my first language without any sort of tutorial, **Reena**!
