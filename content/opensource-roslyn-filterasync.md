---
title: dotnet/roslyn - Issue 66173
description: A deep dive into a specific contribution to the Roslyn .NET Compiler to fix the handling of the async modifier for methods without a body.
date: Jan. 3, 2023
topic: Open Source
---

#### [Link to the PR](https://github.com/dotnet/roslyn/pull/66201)

In my recent work on the [dotnet/roslyn](https://github.com/dotnet/roslyn) repository, I encountered an interesting issue related to the handling of the `async` modifier for methods without a body. The Roslyn repository is the home of the .NET Compiler Platform, which provides open-source C# and Visual Basic compilers with rich code analysis APIs.

### The Issue

The problem was identified in issue [#66173](https://github.com/dotnet/roslyn/issues/66173), titled "SyntaxGenerator: Consider filtering async modifier for methods without a body". The existing code was:

```csharp
var hasBody = !modifiers.IsAbstract && (!modifiers.IsPartial || statements != null);

modifiers: AsModifierList(accessibility, modifiers, SyntaxKind.MethodDeclaration),
```

The question was whether we should drop the async modifier if hasBody is false.

### The Solution

To solve this issue, I added a check to remove the async modifier if hasBody is false. Here's the code change I made:

```csharp
var hasBody = !modifiers.IsAbstract && (!modifiers.IsPartial || statements != null);

if (!hasBody)
    modifiers -= DeclarationModifiers.Async;

return SyntaxFactory.MethodDeclaration(
    attributeLists: default,
    modifiers: AsModifierList(accessibility, modifiers, SyntaxKind.MethodDeclaration),
```

This change ensures that the async modifier is correctly handled, improving the accuracy of the code generation.
