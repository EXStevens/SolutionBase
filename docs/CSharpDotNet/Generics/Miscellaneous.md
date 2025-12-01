# Miscellaneous

## System
### `Nullable<T>` : (struct) enables value types to be null → `int?`, `bool?`

## System.Threading.Tasks
### `Task<T>` : (class) async operation returning `T`
### `ValueTask<T>` : (struct) lightweight async return → reduces allocation
### `TaskCompletionSource<T>` : (class) manually completes `Task<T>`

## System.Lazy
### `Lazy<T>` : (class) lazy-initialized value container

## System.Tuple
### `Tuple<T1, T2...>` : (class) legacy tuple type
### `ValueTuple<T1, T2...>` : (struct) modern tuple type behind `(a, b, c)`

## System.Memory
### `Memory<T>` : (struct) sliceable, safe memory buffer
### `ReadOnlyMemory<T>` : (struct) read-only memory slice
### `Span<T>` : (ref struct) high-performance stack-only span
### `ReadOnlySpan<T>` : (ref struct) read-only span

## System.Buffers
### `ArrayPool<T>` : (class) shared array pool → high-performance allocations
### `MemoryPool<T>` : (class) pooled `Memory<T>` blocks
### `IMemoryOwner<T>` : (interface) owner of pooled `Memory<T>`

## System.IO / Array utilities
### `ArraySegment<T>` : (struct) slice of an array without copying
