---
id: Generics
title: Generics
---

# Generics in C#
```CSharp
TypeName<T>
```
May look similar, but C# generics are *not* C++ templates. Generics are reified types managed by .NET Common Language Runtime (CLR), which empowers it with:

- Type-safe at runtime
- No code bloat (only one machine-code version for reference types)
- Participation in reflection, JIT optimizations, and metadata

like no other can do.

Generics help you avoid casting, reduce code duplication, and improve runtime performance by allowing the .NET runtime to generate optimized type-specific implementations.
