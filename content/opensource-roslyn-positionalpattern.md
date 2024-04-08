---
title: dotnet/roslyn - Issue 65612 & 65748
description: A detailed look at a contribution to the Roslyn .NET Compiler Platform to add more support for positional patterns.
date: Dec. 6, 2022
topic: Open Source
---

#### [Link to the PR](https://github.com/dotnet/roslyn/pull/65748)

In my first ever PR for the [dotnet/roslyn](https://github.com/dotnet/roslyn) repository, I addressed an issue related to the GenerateDeconstructMethodCodeFixProvider not supporting positional patterns. The Roslyn repository is the home of the .NET Compiler Platform, which provides open-source C# and Visual Basic compilers with rich code analysis APIs.

## The Issue

The problem was identified in issue [#65612](https://github.com/dotnet/roslyn/issues/65612). The issue was that the GenerateDeconstructMethodCodeFixProvider did not offer a codefix for the following code:

```csharp
public class C
{
    public void M(object o)
    {
        if (o is C("")) { }
    }
}
```

The expected result would be:

```csharp
public class C
{
    public void M(object o)
    {
        if (o is C("")) { }
    }

    private void Deconstruct(out string x)
    {
        throw new NotImplementedException();
    }
}
```

## The Code Changes

- This was not just a simple IDE fix. The changes involved modifications to several files, including GenerateDeconstructMethodFixProvider.cs, GenerateDeconstructMethodTests.cs, and CSharpGenerateDeconstructMethodService.cs. The changes added support for positional patterns in the GenerateDeconstructMethodCodeFixProvider, and included new unit tests to verify the functionality.

- Moreover, the changes also touched the compiler side of Roslyn, demonstrating the complexity and depth of this contribution. This was a great learning experience and a significant step in my journey as an open-source contributor.

- After many years of clicking the lightbulb for help with C#, I provided the solution. What an amazing feeling!
