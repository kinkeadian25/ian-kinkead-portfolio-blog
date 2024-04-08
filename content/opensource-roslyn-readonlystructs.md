---
title: dotnet/roslyn - Issue 66170, 65834
description: A detailed look at a contribution to the Roslyn .NET Compiler Platform to fix the handling of the readonly keyword for structs
date: Jan. 3, 2023
topic: Open Source
---

#### [Link to the PR](https://github.com/dotnet/roslyn/pull/66169)

In my recent work on the [dotnet/roslyn](https://github.com/dotnet/roslyn) repository, I addressed an issue related to the handling of the `readonly` keyword for structs. The Roslyn repository is the home of the .NET Compiler Platform, which provides open-source C# and Visual Basic compilers with rich code analysis APIs.

## The Issue

The problem was identified in issue [#65834](https://github.com/dotnet/roslyn/issues/65834), titled "The DeclarationModifiers class does not properly handle readonly keyword for struct". The existing code was:

```csharp
var field = symbol as IFieldSymbol;
var property = symbol as IPropertySymbol;
var method = symbol as IMethodSymbol;
var type = symbol as INamedTypeSymbol;

return new DeclarationModifiers(
    isStatic: symbol.IsStatic,
    isAbstract: symbol.IsAbstract,
    isReadOnly: field?.IsReadOnly == true || property?.IsReadOnly == true,
```

The issue was that DeclarationModifiers.From(...) was used not just for fields and properties but also for SymbolKind.NamedType with TypeKind.Class and TypeKind.Struct.

## The Solution

To solve this issue, I extended the initialization of isReadOnly in DeclarationModifiers.From to handle the case when ISymbol is a type declaration. Here's the code change I made:

### Before:

```csharp
var field = symbol as IFieldSymbol;
var property = symbol as IPropertySymbol;
var method = symbol as IMethodSymbol;
var type = symbol as INamedTypeSy
return new DeclarationModifiers(
      isStatic: symbol.IsStatic,
      isAbstract: symbol.IsAbstract,
      isReadOnly: field?.IsReadOnly == true || property?.IsReadOnly == true,
      isVirtual: symbol.IsVirtual,
      isOverride: symbol.IsOverride,
      isSealed: symbol.IsSealed,
      isConst: field?.IsConst == true,
      isUnsafe: symbol.RequiresUnsafeModifier(),
      isVolatile: field?.IsVolatile == true,
      isExtern: symbol.IsExtern,
      isAsync: method?.IsAsync == true,
      isRequired: symbol.IsRequired(),
      isFile: (symbol as INamedTypeSymbol)?.IsFileLocal == true
    );
}
```

### After:

```csharp
var field = symbol as IFieldSymbol;
var property = symbol as IPropertySymbol;
var method = symbol as IMethodSymbol;
var type = symbol as INamedType
return new DeclarationModifiers(
      isStatic: symbol.IsStatic,
      isAbstract: symbol.IsAbstract,
      isReadOnly: field?.IsReadOnly == true || property?.IsReadOnly == true || type?.IsReadOnly == true || method?.IsReadOnly == true,
      isVirtual: symbol.IsVirtual,
      isOverride: symbol.IsOverride,
      isSealed: symbol.IsSealed,
      isConst: field?.IsConst == true,
      isUnsafe: symbol.RequiresUnsafeModifier(),
      isVolatile: field?.IsVolatile == true,
      isExtern: symbol.IsExtern,
      isAsync: method?.IsAsync == true,
      isRequired: symbol.IsRequired(),
      isFile: (symbol as INamedTypeSymbol)?.IsFileLocal == true
    );
}
```

This change ensures that the readonly keyword is correctly handled for structs, improving the accuracy of the code generation.
