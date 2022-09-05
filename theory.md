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
