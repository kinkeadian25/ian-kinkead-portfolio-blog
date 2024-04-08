---
title: dotnet/roslyn - Issue 69700
description: A deep dive into a specific contribution to the Roslyn .NET Compiler Platform to fix incorrect error formatting for missing generic attributes.
date: Aug. 29, 2023
topic: Open Source
---

#### [Link to the PR](https://github.com/dotnet/roslyn/pull/69735)

In my recent work on the [dotnet/roslyn](https://github.com/dotnet/roslyn) repository, I encountered an interesting issue related to the diagnostic message for missing attribute types. The Roslyn repository is the home of the .NET Compiler Platform, which provides open-source C# and Visual Basic compilers with rich code analysis APIs.

## The Issue

The problem was with the diagnostic message for missing attribute types. When an attribute type was missing, the error message was not clear enough. It would say:

- The type or namespace name 'SomeAttribute<>Attribute' could not be found (are you missing a using directive or an assembly reference?)

The expected behavior was for the error message to be more specific and helpful:

- The type or namespace name 'SomeAttributeAttribute<>' could not be found (are you missing a using directive or an assembly reference?)

## The Solution

To solve this issue, I added a check on arity in the construction of the message. Here's the code change I made:

### Before:

```csharp
if (options.IsAttributeTypeLookup() && !options.IsVerbatimNameAttributeTypeLookup())
{
    // just recurse one level, so cheat and OR verbatim name option :)
    NotFound(where, simpleName, arity, whereText + "Attribute", diagnostics, aliasOpt, qualifierOpt, options | LookupOptions.VerbatimNameAttributeTypeOnly);
}

```

### After:

```csharp
if (options.IsAttributeTypeLookup() && !options.IsVerbatimNameAttributeTypeLookup())
{
    string attributeName = arity > 0 ? $"{simpleName}Attribute<>" : $"{simpleName}Attribute";

    NotFound(where, simpleName, arity, attributeName, diagnostics, aliasOpt, qualifierOpt, options | LookupOptions.VerbatimNameAttributeTypeOnly);
}

```

This change ensures that the diagnostic message is more specific and helpful, improving the developer experience when working with attributes in C#.
