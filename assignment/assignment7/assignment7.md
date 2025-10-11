# CS106L Assignment 7: Implementing Unique Pointer

This assignment requires implementing a custom version of unique pointer in C++. Here, we need to understand three key concepts:
- RAII (Resource Acquisition Is Initilization)
- Smart pointers and the memory management
- Move semantics in C++

## RAII (Resource Acquisition Is Initialization)

First of all, we need to understand the definition of RAII.
RAII is a C++ programming technique where resource management is tied to its lifetime.
Resources are acquired during object construction and released during object destruction.

As for benefits, compared to the manual `new` and `delete` keywords in C++, first of all, this achieves automatic memory management.
So, there is no need for us to manually call `delete`.

Besides, this method achieves exception safety. The resources are released when an exception occurs.

Most importantly, this could prevent memory leaks, which ensures every `new` has a corresponding `delete`.

```cpp
// Here is the reference code
// RAII in action - automatic cleanup
{
    autoptr = cs106l::unique_ptr<int>(new int (42));
}
// Memory automatically freed when the pointer goes out of scope

```

## Implementing Unique Pointer

Let us first figure out what smart pointers are.

Smart pointers are objects that manage dynamically allocated memory, automatically freeing the memory when the smart pointer goes out of scope.
They implement RAII principles.
There are so many benefits by using smart pointers, such as preventing memory leaks, automatic cleanup, exception safety and clear ownership semantics.

In C++, there are three types of smart pointers as follows:
1. `unique_ptr`
2. `shard_ptr`
3. `weak_ptr` 



## Move Semantics

We need to review the definition of move semantics.

Move semantics allow the resources of an object to be transferred to another object, rather than copied.
This is especially useful for objects that own memory or other resources.

```cpp
//Here is the reference code
unique_ptr<int> ptr1 = make_unique<int>(42);
unique_ptr<int> ptr2 = std::move(ptr1);
// Note: The behavior above moves the ownership from ptr1 to ptr2. Now the ptr1 is a null pointer, and the ptr2 owns the memory, just like ptr1 brfore.
```

In the case above, we use move instead of copy.
This prevents double deletion, making efficient transfers.



