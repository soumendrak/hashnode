---
title: "How to Use Structs in GoLang: A Comprehensive Tutorial"
seoTitle: "GoLang Structs Tutorial: How to Use"
seoDescription: "Learn GoLang structs: group data, model real-world entities, create methods and interfaces. Comprehensive tutorial"
datePublished: Thu Mar 23 2023 13:44:39 GMT+0000 (Coordinated Universal Time)
cuid: clfl60nya00vmkqnvb9zyc4ql
slug: how-to-use-structs-in-golang-a-comprehensive-tutorial
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1679204308931/bfa1cf78-361c-48a0-b451-372e72d4231e.png
tags: go, golang, struct, programming-tips, golang-developer

---

> This blog post discussed structs in GoLang, which are user-defined types used to group data and model real-world entities. It showed how to declare and create named and anonymous structs, access and modify structs fields, and use nested structs to create more complex data structures. Structs are the basis for creating methods and interfaces in GoLang.

## Introduction

A struct is a user-defined type that represents a collection of fields. It can be used where it makes sense to group the data into a single unit rather than having each as separate values.  
For instance, an employee has a firstName, lastName, and age. Grouping these three properties into a single struct named Employee makes sense. A struct can also contain fields of different types, such as string, int, float64, etc. This concept is generally compared with the classes in object-oriented programming, but structs are simpler and do not support inheritance or methods.  
A struct can be declared using the type keyword and the struct keyword, followed by a list of fields inside curly braces. An example of a real-world entity represented as a struct is an address with fields such as name, street, city, state, and Pincode.

Sure, here is a code snippet that shows how to declare and use a struct type Address:

```go
package main

import (
	"fmt"
)

func main() {
	fmt.Println(addr1.name)
	fmt.Println(addr1.street)
	fmt.Println(addr1.city)
	fmt.Println(addr1.state)
	fmt.Println(addr1.pincode)
	fmt.Println(addr2.name)
}

// Declaring a struct type Address
type Address struct {
	name    string
	street  string
	city    string
	state   string
	pincode int
}

// Creating an Address struct using a struct literal
var addr1 = Address{
	name:    "Soumendra",
	street:  "BTM Layout",
	city:    "Bengaluru",
	state:   "Karnataka",
	pincode: 560076,
}

var addr2 = Address{
	name:    "Rahul",
	street:  "Indiranagar",
	city:    "Bengaluru",
	state:   "Karnataka",
	pincode: 560038,
}
```

## Syntax

* To declare a named struct type, we use the `type` keyword followed by the name of the type and the `struct` keyword. Inside the curly braces, we list the fields of the struct, each with a name and a type.
    
* The name of the type and the fields should start with a capital letter if we want them to be exported (visible outside the package).
    
* The name of the type should be descriptive and usually singular. The names of the fields should be concise and clear.
    
* The type of the fields can be any valid Go type, such as built-in types (string, int, bool, etc.), user-defined types (other structs, interfaces, etc.), or composite types (arrays, slices, maps, etc.).
    
* For example, to declare a struct type Employee with fields firstName, lastName, age, and salary, we can write:
    

```go
// Declaring a named struct type Employee
type Employee struct {
  FirstName string
  LastName string
  Age int
  Salary int
}
```

## Named struct

* To create structs of a named type, we can use two different syntaxes:
    
    * one with specifying field names and
        
    * one without specifying field names.
        
* The first syntax uses a struct literal, a list of field names and values inside curly braces.
    
* *The order of the fields does not matter in this syntax*, and we can omit some fields if we want them to have zero values.
    
* The advantage of this syntax is that it makes the code more readable and clear. The disadvantage is that it can be verbose and repetitive if we have many fields or many structs to create.
    
* For example, to create an Employee struct using this syntax, we can write:
    

```go
// Creating an Employee struct using a struct literal
employee1 := Employee{
  FirstName: "Soumendra",
  LastName: "Sahoo",
  Age: 31,
  Salary: 50000,
}
```

* The second syntax lists values inside curly braces without specifying the field names.
    
* *The order of the values must match the order of the fields* in the struct declaration in this syntax, and *we cannot omit any field*.
    
* The advantage of this syntax is that it is concise and compact.
    
* The disadvantage is that it can be confusing and error-prone if we have many fields or change the order of the fields in the struct declaration. For example, to create an Employee struct using this syntax, we can write:
    

```go
// Creating an Employee struct using a list of values
employee2 := Employee{"Rahul", "Dravid", 50, 80000}
```

## Anon structs

* We can use an anonymous struct to create structs without declaring a new data type. An anonymous struct is a struct literal without a type name. It can be helpful when we need a temporary data structure not used elsewhere in the code.
    
* For example, we can use an anonymous struct to store configuration data or pass some arguments to a function.
    
* The disadvantage of using an anonymous struct is that we cannot reuse or refer to it by name. For example, to create an anonymous struct with fields firstName, lastName, age, and salary, we can write:
    

```go
// Creating an anonymous struct
employee3 := struct {
  firstName string
  lastName string
  age int
  salary int
}{
  firstName: "Dipanwit",
  lastName: "DasMohapatra",
  age: 26,
  salary: 30000,
}
```

It also can be written without specifying the field name

```go
	employee4 := struct {
		FirstName string
		LastName  string
		Age       int
		Salary    int
	}{"Pranjal", "Kamra", 30, 70000}
```

## Assigning fields of a struct

* To access individual fields of a struct, we use the dot (.) operator followed by the field name.
    
* We can use this operator on both struct variables and struct pointers. We can also modify or assign values to fields using the same operator and the assignment (=) operator.
    
* For example, to access and modify fields of Employee structs, we can write:
    

```go
	// Accessing fields of a struct
	fmt.Println(employee1.FirstName) // prints Soumendra
	fmt.Println(employee2.Age)       // prints 50
	fmt.Println(employee3.Salary)    // prints 30000
	fmt.Println(employee4.Salary)    // prints 70000

	// Modifying or assigning values to fields
	employee1.Salary = 60000      // modifying field value
	employee2.LastName = "Gandhi" // assigning new value to field

	fmt.Println(employee1.Salary)   // prints 60000
	fmt.Println(employee2.LastName) // prints Gandhi
```

[Run in Playground](https://play.golang.com/p/dW36gH5ypOR)

## Nested struct

* Nested structs are structs that have fields that are themselves structs. This allows us to create more complex data structures representing hierarchical or nested relationships.
    
* For example, we can create a nested struct to represent a person with an address with fields such as street, city, and state. To declare a nested struct, we can either define each struct type separately and use them as field types, or we can define anonymous structs inside others.
    
* To create a nested struct, we can use either syntax for creating named or anonymous structs, but we have to specify the values for each nested field using curly braces. To access or modify fields of a nested struct, we have to use the dot (.) operator multiple times to reach the desired field. For example, to declare and use a nested struct Employee with an Address field, we can write:
    
    ```go
    package main
    
    import "fmt"
    
    type Address struct {
    	street  string
    	city    string
    	state   string
    	pincode int
    }
    
    type Employee struct {
    	firstName string
    	lastName  string
    	age       int
    	salary    int
    	address   Address
    }
    
    func main() {
    	employee1 := Employee{
    		firstName: "Abhijit",
    		lastName:  "Chavda",
    		age:       45,
    		address: Address{
    			city:  "Bengaluru",
    			state: "Karnataka",
    		},
    	}
    
    	fmt.Println("First Name:", employee1.firstName)
    	fmt.Println("Age:", employee1.age)
    	fmt.Println("City:", employee1.address.city)
    	fmt.Println("State:", employee1.address.state)
    }
    ```
    

[Run in Playground](https://go.dev/play/p/PU27baHYrKt)

## Conclusion

In this blog post, we have learned about structs in GoLang, which are user-defined types that represent collections of fields. We have seen how to declare and create named, and anonymous structs using different syntaxes, access and modify structs fields using the dot (.) operator, and use nested structs to create more complex data structures. Structs are helpful for grouping data into a single unit and modeling real-world entities. They are also the basis for creating methods and interfaces in GoLang. For further reading on structs in GoLang, you can check out these links:

* [https://golangbot.com/structs/](https://golangbot.com/structs/)
    
* [https://www.geeksforgeeks.org/structures-in-golang/](https://www.geeksforgeeks.org/structures-in-golang/)