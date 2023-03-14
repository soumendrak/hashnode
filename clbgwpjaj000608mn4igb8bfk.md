---
title: "Go: Arrays vs Slices"
datePublished: Fri Dec 09 2022 19:34:09 GMT+0000 (Coordinated Universal Time)
cuid: clbgwpjaj000608mn4igb8bfk
slug: go-arrays-vs-slices
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1670614388004/B2fB89dKb.png
tags: go, golang, array, slice, golang-developer

---

Array and slice are two important data structures in Go that are used to store and manipulate sequences of values. Although they may appear similar at first glance, some key differences between the two are worth understanding.

An array is a fixed-size data structure that stores a sequence of values of the same type. It is allocated with a specific size that cannot be changed after its creation. For example, the following code creates an array of 5 integers:

```go
var myArray [5]int
```

An array is accessed using its index, a zero-based integer value that specifies the element's position in the array. For example, to access the first element in the array, we can use the following code:

```go
myArray[0]
```

An array is a value type, which means that a copy of the array is created when it is passed to a function or assigned to a variable. This can have significant performance implications if the array is substantial, as copying the entire array can take time and memory.

On the other hand, a slice is a variable-size data structure that references a portion of an array. A slice is declared using the \[\]type syntax and is dynamically resized according to the program's needs. For example, the following code creates a slice of 5 integers:

```go
mySlice := []int{1, 2, 3, 4, 5}
```

A slice is accessed using a range, which is a pair of values that specify the start and end indices of the slice. For example, to access the first three elements in the slice, we can use the following code:

```go
mySlice[0:3]
```

Unlike an array, a slice is a reference type, meaning that only a reference to the slice is created when it is passed to a function or assigned to a variable. This can have some performance benefits if the slice is significant, as copying only a reference is much faster and requires less memory.

Another critical difference between an array and a slice is how they are passed to a function. An array is passed by value, meaning a copy of the array is created and passed to the function. This can have significant performance implications if the array is substantial, as copying the entire array can take time and memory. On the other hand, a slice is passed by reference, which means that only a reference to the slice is passed to the function. Again, this can have some performance benefits if the slice is significant, as copying only a reference is much faster and requires less memory.

## Differences

These are the differences between arrays and slices in the Go programming language.

* An array is a fixed-size data structure that stores a sequence of values of the same type. On the other hand, a slice is a variable-size data structure that references a portion of an array.
    
* An array is allocated with a specific size, which cannot be changed after creation. A slice, on the other hand, can be dynamically resized.
    
* An array is accessed using its index, while a slice is accessed using a range.
    
* An array is a value type, while a slice is a reference type.
    
* An array is passed by value to a function, while a slice is passed by reference.
    
* An array is declared using the \[size\]type syntax, while a slice is displayed using the \[\]type syntax.
    

```go
// Declare and initialize an array of 5 integers
arr := [5]int{1, 2, 3, 4, 5}
```

```go
// Declare and initialize a slice of integers
slice := []int{1, 2, 3, 4, 5}
```

## Usage

* Arrays are used when the size of the data is known in advance and is not expected to change. This allows for efficient memory allocation and access. Examples include storing a list of student names or a deck of cards.
    
* Slices are used when the data size is not known in advance or is expected to change. This allows for more flexible and dynamic data manipulation. Examples include working with a subset of data from an array, such as the first ten elements, or dynamically adding and removing elements from a list.
    

## Conclusion

Array and slice are two important data structures in Go that are used to store and manipulate sequences of values. While both provide similar functionality, some critical differences are worth understanding. First, an array is a fixed-size data structure that stores a series of values of the same type, while a slice is a variable-size data structure that references a portion of an array. An array is a value type, while a slice is a reference type. Finally, an array is passed by value to a function, while a slice is passed by reference. Understanding these differences can help you choose the proper data structure for your needs and write more efficient and effective Go code.