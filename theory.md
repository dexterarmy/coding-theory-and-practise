## Stack and heap ->

-- memory management units, memory space in stack < heap
-- value type -> stack, reference type -> heap
-- no memory leak on stack, once func finishes its work stack is removed, When you have a variable with automatic storage duration`(stack)`it is cleaned up by the program automatically
-- Every function at the program you run gets its own stack
-- heap is part of the memory, that is related to the process and not to a specific function
-- there can be many stacks because there are many functions but there is only 1 heap
-- heap is a big memory place where you throw all your objects
-- garbage collectors to clean the heap
-- with garbage collectors also there might be leaks at heap so we have to take care of that, so check out how the garbage collector works in your preferred language
-- heap is a memory space that is global to all the function, therefore if function X changes something there, it means the change will be reflected to function Y as well
`there is a stack for each function and there is 1 heap for the whole program, that means if there is something in the heap, every change will be reflected by all the program, while changing something at the stack it doesn’t affect the whole program, it affects just the function`

## Event loop ->

- `web api` -> built into browser, expose data from browser and surrounding computer env and do complex things. Web API on top of core javascript code like geolocation API(in background browser uses c++ code to communicate with device GPS hardware and return data to browser environment to use in our code)

* func that finished Web API execution(setTimeout web api) are moved to callback queue.
* macro task queue(task queue) -> setTimeout, setInterval, setImmediate
* micro task -> process.nextTick, Promise callback
* event loop order -> call stack --- micro task queue --- macro task queue

## Funciton Scope and Block scope ->

--`scope` means which variable is accessible and upto which point it is accessible
-- whole document is `global scope` and all the other functions and variables are contained in this global scope
-- `local scope` -> variables declared inside the functions
`Function Scope`: variable is declared inside a function, only accessible within that function and cannot be used outside that function
`Block scope` -> variable declared in if,switch,for,while in other words in `curly braces`, are accessible within that particular condition or loop or curly braces
`var` -> func scope, `let, const` -> block scope

## Primitive and non primitive type ->

`mutable` -> object, array
`immutable` -> primitive types
`reference type` -> array, obj, func, date, regex
`non primitive / value type` -> number, boolean, string, null , undefined, symbol
`value type` -> new element gets into the top of the stack and stores the data of that variable with new memory location each time
`var name = "Maya", var newName = name` -> both variable in new memory location
`heap` -> stores the data randomly, where each of the data has its own address,slower to access but has much more space since it handles more complex variables. Adds variable(element) to the stack but its value points to the address of object stored in heap
`var Person = {name: "Maya", age: "29"} ,var newPerson = Person` -> adds Personpointer and newPersonpointer to the stack
but both of them points to the same address in heap so to the same object
-- Mutability in JavaScript is not related to the variable keyword but to the value's type
-- The difference between let and const is about reassignability, not mutability

## Scope chain -.

-- now we will know how JavaScript Engine Performs Variable Lookups
