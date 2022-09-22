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

1. now we will know how JavaScript Engine Performs Variable Lookups
2. scope -> accessibility or visibility of variables
3. Using scope, we can avoid unintended modifications to the variables from other parts of the program
4. we can use the same variable names in different scopes.
5. block scope -> they can be scoped to the nearest pair of `curly braces.` That means, they `can’t be accessed from outside that pair of curly braces`
6. a scope can be nested inside another scope
7. `lexical scope` -> static scope, scope is determined at lexing time(compilation time) rather than at runtime
8. Using lexical scope we can determine the scope of the variable just by looking at the source code. Whereas in the case of dynamic scoping the scope can’t be determined until the code is executed
9. lang which supports static scope -> javascript, c, c++, java etc
10. when a variable is used engine go up the scope chain until it finds the variable
11. If it’s still could not find the variable, it will either implicitly declare the variable in the global scope (if not in strict mode) or return an error
12. `lexical environemnt` -> A lexical environment is a structure that holds identifier-variable mapping. (here identifier refers to the name of variables/functions, and the variable is the reference to actual object [including function object and array object] or primitive value)
13. lexical environment is a place where variables and references to the objects are stored.
14. lexical environment is a place where variables are stored during the program execution
15. new lexical environment is created for each lexical scope but only when the code in that scope is executed. The lexical environment also has a reference to its outer lexical environment ( i.e outer scope)
16. JavaScript engine uses the lexical environment to determine scope and scope chain
17. A new lexical environment is created only for let and const declarations, not var declarations. var declarations are added to the current lexical environment (global or function lexical environment)
    `read further:` https://blog.bitsrc.io/understanding-scope-and-scope-chain-in-javascript-f6637978cf53

## CLOSURES ->

1. functions in JavaScript form closures, closures are created everytime a func is created at func creation time
2. closure is the combination of a function and the lexical environment within which that function was declared
3. thanks to javascript lexical scoping many closures(func) can share same lexical environment
4. changes to the variable value in one closure don't affect the value in the other closure
5. closures can provides us benefits like data hiding and encapsulation which are normally associated with OOPs
6. each closure references a diff version of lexical environment through its own closure
7. closures is the combination of func bundled together with reference to its lexical env
8. closures has three scopes -> local, enclosed(chain of func scope), global
9. closures have access to all outer function scopes.
10. Closures can capture variables in `block scopes `and `module `scopes as well
11. Closures can close over `imported values` as well, which are regarded as `live bindings`, because when the original value changes, the imported one changes accordingly
12. with let and const, closures binds also the blocked scoped variable
13. each function instance manages its own scope and closure. Therefore, it is unwise to unnecessarily create functions within other functions if closures are not needed for a particular task eg: object/class methods(use prototype inheritance)

## new Keyword ->

1. When a function is called with the new keyword, the function will be used as a constructor
2. when a func is called with new, new creates an object
3. points new object [[prototype]] to constructor function's prototype property
4. this in the constructor function now refer to new object
5. A function can know whether it is invoked with new by checking new.target
6. Array(), Error(), and Function() behave the same when called as a function or a constructor.
7. Boolean(), Number(), and String() coerce their argument to the respective primitive type when called, and return wrapper objects when constructed
8. Symbol() and BigInt() can only be called without new
9. Proxy and Map can only be constructed with new
10. Date() returns a string representing the current date when called, same as new Date().toString()

## **proto** vs [[prototype]] ->

1. **proto** is an internal property of an object, pointing to its prototype
2. All the object constructors (function) have prototype properties
3. All the objects have proto property.
4. proto is used in the lookup chain to resolve methods, constructors, etc.
5. prototype -> It is the property of the class.
6. proto -> It is the property of the instance of that class.
7. Object.getPrototypeOf() method returns the prototype (i.e. the value of the internal [[Prototype]] property) of the specified object , same as proto

## Instance of ->

1. `Instanceof operator` -> tests to see if the prototype property of a constructor appears anywhere in the prototype chain of an object
   eg: auto instanceof Car

## DOUBTS (networking, linux)->

1. company's internal software repository with url accessible from office network ?
2. repo server ?
3. file based name resolution ?
4. DNS PROBE FINISHED NX DOMAIN -> not able to locate ip address of a name
5. part of the network and assigned with ip ?
6. `host A does not care what is the real hostname of system B`
7. ssh, curl, nslookup,dig?
8. `resolv.conf file , entry for public nameserver that knows all the sites on internet.`
9. 8.8.8.8 nameserver available on internet hosted by google ?
10. .net ?
11. subdomains are the services provided by the domains ?
12. dot is the root where everything starts ?
13. `local DNS server -- root DNS server ponts to DNS server serving .com and so on`
14. `www. for external facing website, and subdomains for each purpose`
15. mail.mycompany.com ?
16. someone from the outside wants to access our web server ?
17. `search in resolv.conf , to append the domain name while resolving dns name`
18. CNAME ??
19. `nslookup directly from DNS server`
20. `dig also resolves DNS name directly from DNS server`
21. password to write in a file in another system ??
22. `search domain in resolv.conf`
23. apache server connect, telnet apache 80, not able to... so we ping then we got lack priviledge for raw socket, then we did ssh apache with our password, so we went to apache's system, `so sudo ip link set dev eth0 up` ??
24. `sudo ip route add default via 172.16.238.10`
25. `gateway/routes through router`
26. 0.0.0.0 -> any ip destination
27. 0.0.0.0 -> in gateway means we don't need a gateway(when in own network so don't neet router/gateway)
28. default gateway is the path used to pass information when the device doesn't know where the destination is
29. routing table -> command `route`
30. `ip addr add` -> to set ip addresses on the interface
31. `/etc/network/interfaces` -> to persist changes made with commands like ip addrs add etc
32. connecting to other network's system ?? (we can go to that system with ssh <servername>) if we know its password, we will do this in our network too ??? )
33. `different system connected to a router, and we have made one system as a web server, so we can connect to that system with router as gateway, if its interface is up and many more things`
34. `ip r add default via 172.16.238.10` -> added default route via eth0 gateway on the server
35. to troubleshoot an issue with the route we use `traceroute` command -> show us the no. of hops or devices between source and the repo server in our case
36. `netstat command`, netstat -an | grep 80 | grep -i LISTEN
