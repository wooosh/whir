# Whir Specification

## Typing
Whir has the following types:
- integer: i64, i32, i16, i8
- unsigned integer: u64, u32, u16, u8
- float: f64, f32
- pointer: ptr (represents an unsigned int with your architectures pointer size)
- void: void
- type (only used as a parameter)

Types can also be used as values that represent their size in bytes, except for `void`:
```
(add i64 i8) // == 9
```
### Symbols
Symbols allow you to name local variables. Symbols preserve the type the were set with when loaded:
```
(alloc $mynumber i64) // subtype i64
(load $mynumber) // returns a i64 value
```

- Symbols can only be used after they have been instantiated using `alloc`
- Symbols downcast to pointers automatically
## Operations
### Memory
```
// alloc will instantiate a symbol that corresponds to a variable
(alloc symbol type) // Returns a symbol of the given type
(alloc symbol size) // Returns a void typed symbol
(alloc symbol size align) // Returns a void typed symbol and aligns the local variable

// store will set a memory address
(store symbol value) // Value must be of the same type as symbol
(store ptr value)

// load returns the value in the given symbol at the pointer
(load symbol) // Does not work for void type symbols
(load ptr type)

// copy copies a block of memory from src to dest. src and dest must be pointers or symbols of type void.
(copy src dest size)
```
# TODO
- Compile time math
- Memory addressing
- Type casting
- Type annotations
- Operations
- Syntax
- Hardware registers
- Functions
- Goto
- Control flow
- Non-text sections
- Immediates
