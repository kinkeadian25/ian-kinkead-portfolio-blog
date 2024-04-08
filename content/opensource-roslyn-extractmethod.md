---
title: dotnet/roslyn - Issue 38127 & 65456
description: A detailed look at a contribution to the Roslyn .NET Compiler Platform to fix nullability issues in the Extract Method refactoring.
date: Dec. 29, 2022
topic: Open Source
---

#### [Link to the PR](https://github.com/dotnet/roslyn/pull/65925)

In my recent work on the [dotnet/roslyn](https://github.com/dotnet/roslyn) repository, I addressed two issues related to the handling of nullability in the Extract Method refactoring. The Roslyn repository is the home of the .NET Compiler Platform, which provides open-source C# and Visual Basic compilers with rich code analysis APIs.

## The Issues

The problems were identified in issues [#38127](https://github.com/dotnet/roslyn/issues/38127) and [#65456](https://github.com/dotnet/roslyn/issues/65456). Both issues were related to the Extract Method refactoring not correctly handling nullability in certain scenarios.

Here's an example that illustrates the problem:

```csharp
public class Test
{
    public int M(Dictionary<string, string?> v)
    {
        return v.Count;
    }
}
```

When running the Extract Method refactoring on the return statement line, the expected behavior was that the new method's parameter type should be Dictionary<string, string?>. However, the actual behavior was that the new method's parameter type was Dictionary<string, string>, missing the nullability annotation on the second generic parameter. This resulted in an immediate nullability error.

## The Solution

The solution involved modifying the Extract Method refactoring to correctly handle nullability in these scenarios. This was a complex task that required changes in several parts of the codebase. The changes ensured that nullability annotations were correctly preserved when extracting methods, and that nullability errors were correctly reported.

## The changes included:

- Modifying the method that determines the type of the extracted method's parameters to correctly handle nullability.
- Updating the method that generates the new method to correctly apply nullability annotations.
- Adjusting the method that checks for nullability errors to correctly handle the new scenarios.
- Due to the complexity of the changes, I encourage you to view the full details of the contribution in the pull request.
