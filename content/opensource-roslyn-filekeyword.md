---
title: dotnet/roslyn - Issue 66319
description: A detailed look at a contribution to improve Intellisense suggestions in regards to the file keyword in the Roslyn .NET Compiler Platform.
date: Jan. 20, 2023
topic: Open Source
---

#### [Link to the PR](https://github.com/dotnet/roslyn/pull/66357)

# Enhancing Intellisense for the 'file' Keyword in dotnet/roslyn Repository

In my recent work on the [dotnet/roslyn](https://github.com/dotnet/roslyn) repository, I tackled an issue related to the Intellisense suggestions for the 'file' keyword. The Roslyn repository is the home of the .NET Compiler Platform, which provides open-source C# and Visual Basic compilers with rich code analysis APIs.

## The Issue

The problem was with the Intellisense suggestions when using the 'file' keyword. When typing code using the 'file' keyword, no suggestions were being provided. For example:

```csharp
//      ↓ here
file sealed class A { }
//   ~~~~~~
```

The expected behavior was for Intellisense to suggest other keywords that could be used for declaration on types after the 'file' keyword, such as 'class', 'struct', 'sealed', 'abstract', 'readonly', etc.

To solve this issue, I worked on enhancing the Intellisense suggestions. While implementing this, I was provided an opportunity to practice creating a lot of fairly complex unit tests, which is a crucial skill in software development.

Here is one example:

```csharp
[Fact, WorkItem(66319, "https://github.com/dotnet/roslyn/issues/66319")]
public async Task TestFileKeywordInsideNamespace()
{
    await VerifyKeywordAsync(
@"namespace N {
file $$
}");
}

[Fact, WorkItem(66319, "https://github.com/dotnet/roslyn/issues/66319")]
public async Task TestFileKeywordInsideNamespaceBeforeClass()
{
    await VerifyKeywordAsync(
@"namespace N {
file $$
class C {}
}");
}
```
