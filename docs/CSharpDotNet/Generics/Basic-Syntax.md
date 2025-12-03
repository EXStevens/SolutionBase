---
title: Basic Syntax
sidebar_position: 1
---

# Basic Syntax
## Declaration
### Generic Class
```CSharp
public class Box<T>
{
    public T Value { get; set; }
}
```
### Generic Method
```CSharp
public T Method<T>(T value)
{
    return value;
}
```
### Generic Interface
```CSharp
public interface IRepository<T>
{
    T Get(int id);
}
```
### Generic Constraints
```CSharp
public class Factory<T> where T : new()
{
    public T Create() => new T();
}
```

:::tip
- T is a type parameter (a placeholder)
- `where T : new()` is a constraint, which restricts what kinds of types can be used
:::

## Constraint
Generic constraints specify the requirements that a type parameter must satisfy. They allow the compiler to ensure that `T` supports certain operations, such as having a parameterless constructor, inheriting from a specific base class, or implementing an interface.

Without constraints, the compiler cannot assume anything about `T`.

### Basic Syntax

```CSharp
class MyClass<T> where T : ConstraintType
{
}
```

Multiple constraints can be combined:

```CSharp
class MyClass<T> where T : BaseClass, IInterface, new()
{
}
```

Constraint order must follow this pattern:

1. class or struct  
2. Base class  
3. Interfaces  
4. new()

### Common Constraint Types

#### Reference type constraint

```CSharp
where T : class
```

#### Value type constraint

```CSharp
where T : struct
```

#### Parameterless constructor

```CSharp
where T : new()
```

#### Inherit from a base class

```CSharp
where T : BaseClass
```

#### Implement an interface

```CSharp
where T : IDisposable
```

### Why Constraints Are Needed

#### Calling members that may not exist

```CSharp
void CloseItem<T>(T item)
{
    item.Dispose(); // Cannot compile
}
```

```CSharp
void CloseItem<T>(T item) where T : IDisposable
{
    item.Dispose(); // ✔ Safe
}
```

#### Creating instances of T

```CSharp
class Factory<T>
{
    T Create() => new T(); // Not allowed
}
```

```CSharp
class Factory<T> where T : new()
{
    T Create() => new T(); // ✔ Allowed
}
```

### Method-Level Constraints

Constraints can also be applied to individual methods:

```CSharp
public void Save<T>(T item) where T : IEntity
{
    item.Store();
}
```
