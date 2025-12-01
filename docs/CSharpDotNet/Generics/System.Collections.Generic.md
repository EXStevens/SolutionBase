---
title: System.Collections.Generic
sidebar_position: 2
---

# `System.Collections.Generic`
Core Generic Collections

## `List<T>`
Resizable dynamic array.  
Fast random access (O(1)), append is amortized O(1).

## `Dictionary<TKey, TValue>`
Hash map (hash table).  
Fast lookup/insert/delete average O(1).

## `HashSet<T>`
Unique-value collection (mathematical set).  
Insert & lookup average O(1).

## `Queue<T>`
FIFO (First-In-First-Out) collection.

## `Stack<T>`
LIFO (Last-In-First-Out) collection.

## `LinkedList<T>`
Doubly linked list.  
Efficient insertion/removal in the middle of the list.

## `SortedList<TKey, TValue>`
Sorted Key–Value pairs backed by *array*.  
Good for smaller datasets.

## `SortedDictionary<TKey, TValue>`
Sorted Key–Value pairs backed by *red-black tree*.  
Good for larger datasets.

## `SortedSet<T>`
Sorted unique elements.  
Uses balanced tree (RB-tree).

## `KeyValuePair<TKey, TValue>`
Struct used when iterating `Dictionary<K, V>`.
