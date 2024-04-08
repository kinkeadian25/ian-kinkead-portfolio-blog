---
title: dotnet/roslyn - Issue 65931
description: A detailed look at a contribution to the Roslyn .NET Compiler Platform to improve AsPublicInterfaceImplementation.
date: Dec. 14, 2022
topic: Open Source
---

#### [Link to the PR](https://github.com/dotnet/roslyn/pull/65984)

In my recent work on the [dotnet/roslyn](https://github.com/dotnet/roslyn) repository, I addressed an issue related to the handling of expression-bodied methods in public interface implementations. The Roslyn repository is the home of the .NET Compiler Platform, which provides open-source C# and Visual Basic compilers with rich code analysis APIs.

## The Issue

The problem was identified in issue [#65984](https://github.com/dotnet/roslyn/issues/65984), titled "AsPublicInterfaceImplementation doesn't handle expression-bodied correctly".

The existing code resulted in this:

```csharp
public interface IGeneral
{
    object DoSomething();
}

public class C : IGeneral
{
    object IGeneral.DoSomething() => new();
}
```

The issue was that AsPublicInterfaceImplementation did not correctly handle the expression-bodied method in the explicit implementation above.

## The Solution

The solution involves modifying the `WithBodies` method to correctly handle expression-bodied methods and properties. The `WithBodies` method is responsible for ensuring that a method, property, or accessor has a body. If it doesn't, a new body is created and added.

In the original code, the `WithBodies` method only checked if the `Body` property was `null`. However, this approach didn't account for expression-bodied methods and properties, which use the `ExpressionBody` property instead of `Body`.

Here's the updated `WithBodies` method for `MethodDeclaration`:

### Before:

```csharp
private static SyntaxNode WithInterfaceSpecifier(SyntaxNode declaration, ExplicitInterfaceSpecifierSyntax? specifier)
            => declaration.Kind() switch
{
    SyntaxKind.MethodDeclaration => ((MethodDeclarationSyntax)declaration).WithExplicitInterfaceSpecifier(specifier),
    SyntaxKind.PropertyDeclaration => ((PropertyDeclarationSyntax)declaration).WithExplicitInterfaceSpecifier(specifier),
    SyntaxKind.IndexerDeclaration => ((IndexerDeclarationSyntax)declaration).WithExplicitInterfaceSpecifier(specifier),
    SyntaxKind.EventDeclaration => ((EventDeclarationSyntax)declaration).WithExplicitInterfaceSpecifier(specifier),
    _ => declaration,
};
  private SyntaxNode AsImplementation(SyntaxNode declaration, Accessibility requiredAccess)
  {
      declaration = this.WithAccessibility(declaration, requiredAccess);
      declaration = this.WithModifiers(declaration, this.GetModifiers(declaration) - DeclarationModifiers.Abstract);
      declaration = WithBodies(declaration);
      return declaration;
  }
  private static SyntaxNode WithBodies(SyntaxNode declaration)
  {
      switch (declaration.Kind())
      {
          case SyntaxKind.MethodDeclaration:
              var method = (MethodDeclarationSyntax)declaration;
              return (method.Body == null) ? method.WithSemicolonToken(default).WithBody(CreateBlock()) : metho
          case SyntaxKind.OperatorDeclaration:
              var op = (OperatorDeclarationSyntax)declaration;
              return (op.Body == null) ? op.WithSemicolonToken(default).WithBody(CreateBlock()) : o
          case SyntaxKind.ConversionOperatorDeclaration:
              var cop = (ConversionOperatorDeclarationSyntax)declaration;
              return (cop.Body == null) ? cop.WithSemicolonToken(default).WithBody(CreateBlock()) : cop;
          case SyntaxKind.OperatorDeclaration:
              var method = (BaseMethodDeclarationSyntax)declaration;
              return (method.Body == null && method.ExpressionBody == null) ? method.WithSemicolonToken(default).WithBody(CreateBlock()) : metho
          case SyntaxKind.PropertyDeclaration:
              var prop = (PropertyDeclarationSyntax)declaration;
              return (prop.AccessorList != null) ? prop.WithAccessorList(WithBodies(prop.AccessorList)) : prop;
          case SyntaxKind.IndexerDeclaration:
              var ind = (IndexerDeclarationSyntax)declaration;
              return (ind.AccessorList != null) ? ind.WithAccessorList(WithBodies(ind.AccessorList)) : ind;
          case SyntaxKind.EventDeclaration:
              var ev = (EventDeclarationSyntax)declaration;
              return (ev.AccessorList != null) ? ev.WithAccessorList(WithBodies(ev.AccessorList)) : ev;
      }
      return declaration;
  }
  private static AccessorListSyntax WithBodies(AccessorListSyntax accessorList)
      => accessorList.WithAccessors(SyntaxFactory.List(accessorList.Accessors.Select(x => WithBody(x)))
  private static AccessorDeclarationSyntax WithBody(AccessorDeclarationSyntax accessor)
  {
      if (accessor.Body == null)
      if (accessor.Body == null && accessor.ExpressionBody == null)
      {
          return accessor.WithSemicolonToken(default).WithBody(CreateBlock(null));
      }
      else
      {
          return accessor;
      }
  }
```

### After:

```csharp
private static SyntaxNode WithInterfaceSpecifier(SyntaxNode declaration, ExplicitInterfaceSpecifierSyntax? specifier)
            => declaration.Kind() switch
 {
    SyntaxKind.MethodDeclaration => ((MethodDeclarationSyntax)declaration).WithExplicitInterfaceSpecifier(specifier),
    SyntaxKind.PropertyDeclaration => ((PropertyDeclarationSyntax)declaration).WithExplicitInterfaceSpecifier(specifier),
    SyntaxKind.OperatorDeclaration => ((OperatorDeclarationSyntax)declaration).WithExplicitInterfaceSpecifier(specifier),
    SyntaxKind.ConversionOperatorDeclaration => ((ConversionOperatorDeclarationSyntax)declaration).WithExplicitInterfaceSpecifier(specifier),
    SyntaxKind.IndexerDeclaration => ((IndexerDeclarationSyntax)declaration).WithExplicitInterfaceSpecifier(specifier),
    SyntaxKind.EventDeclaration => ((EventDeclarationSyntax)declaration).WithExplicitInterfaceSpecifier(specifier),
    _ => declaration,
};
private SyntaxNode AsImplementation(SyntaxNode declaration, Accessibility requiredAccess)
{
    declaration = this.WithAccessibility(declaration, requiredAccess);
    declaration = this.WithModifiers(declaration, this.GetModifiers(declaration) - DeclarationModifiers.Abstract);
    declaration = WithBodies(declaration);
    return declaration;
}
private static SyntaxNode WithBodies(SyntaxNode declaration)
{
    switch (declaration.Kind())
    {
        case SyntaxKind.MethodDeclarati
        case SyntaxKind.ConversionOperatorDeclarati
        case SyntaxKind.OperatorDeclaration:
            var method = (BaseMethodDeclarationSyntax)declaration;
            return (method.Body == null && method.ExpressionBody == null) ? method.WithSemicolonToken(default).WithBody(CreateBlock()) : meth
        case SyntaxKind.PropertyDeclaration:
            var prop = (PropertyDeclarationSyntax)declaration;
            return (prop.AccessorList != null) ? prop.WithAccessorList(WithBodies(prop.AccessorList)) : prop;
        case SyntaxKind.IndexerDeclaration:
            var ind = (IndexerDeclarationSyntax)declaration;
            return (ind.AccessorList != null) ? ind.WithAccessorList(WithBodies(ind.AccessorList)) : ind;
        case SyntaxKind.EventDeclaration:
            var ev = (EventDeclarationSyntax)declaration;
            return (ev.AccessorList != null) ? ev.WithAccessorList(WithBodies(ev.AccessorList)) : ev;
    }
    return declaration;
}
private static AccessorListSyntax WithBodies(AccessorListSyntax accessorList)
    => accessorList.WithAccessors(SyntaxFactory.List(accessorList.Accessors.Select(x => WithBody(x))
private static AccessorDeclarationSyntax WithBody(AccessorDeclarationSyntax accessor)
{
    if (accessor.Body == null && accessor.ExpressionBody == null)
    {
        return accessor.WithSemicolonToken(default).WithBody(CreateBlock(null));
    }
    else
    {
        return accessor;
    }
}
```

This change ensures that the expression-bodied methods are correctly handled in public interface implementations, improving the accuracy of the code generation.
