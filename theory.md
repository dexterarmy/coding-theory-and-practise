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
4. DNS PROBE FINISHED NX DOMAIN error-> not able to locate ip address of a name
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
35. to troubleshoot an issue with the route we use `traceroute` command -> show us the no. of hops or devices between source and the repo server in our case, shows us devices like routers, sytem in our route between source and destination
36. `netstat command`, netstat -an | grep 80 | grep -i LISTEN, check if http process is running on port 80
37. connection timeout error -> issue with interface, route, ip resolve, DNS server issue, server itself has connectivity issues, software that hosts the service is not functioning (network troubleshooting)
38. ping to check if the response is coming from remote server
39. screen sharing session ??
40. assuming the folder in which the web server started it gave all the files in that folder

## Security and file permissions ->

1. group users on the same system
2. system accounts created during OS installation, for software and services that are not super user
3. sshd -> provides encrypted communications between two untrusted hosts over an insecure network, listens at port 22
4. system accounts vs service accounts ???
5. `sudo su -`, `su -l username`, `sudo su -c "whoami"`
6. in Ubuntu, by default, root has no password. Without arguments, su means "switch user to root" and to do that you have to enter root's password, not your own. Unless you give root a password, it doesn't have one, so you can't literally log in as root. That is why use of `su` is not recommended and `sudo` is recommended because it requires your own passwd
7. sudo to give users administrative access
8. chsh -> to change user's shell
9. how it is secure if anyone can edit sudoers file ??
10. sudoers file, prevents other users from running commands as root user ???
11. admin can give granular level access with sudo
12. `access control files`

## this ->

1. runtime binding, it can't be set by assignment during execution
2. All non-static methods within the class are added to the prototype of this
3. Derived classes must not return before calling super(), unless they return an Object or have no constructor at all.
4. in non–strict mode, with call and apply, if the value passed as this is not an object, an attempt will be made to convert it to an object
5. Object.prototype.toString.call(34) `????`
6. Calling f.bind(someObject) creates a new function with the same body and scope as f. `bind only works once`
7. arrow func -> this as first arg in call,apply,bind will be ignored, so put first arg as null
8. arro func -> this remains that of the enclosing lexical context.
9. this binding is only affected by the most immediate member reference
10. method is on object's prototype chain, this refers to object the method was called on, as if the method were on the object
11. `Object.create()` creates a new object, using an existing object as the prototype of the newly created object.
12. A function used as getter or setter has its this bound to the object from which the property is being set or gotten.
13. if returned object from constructor, then `this object` is dead
14. in DOM event handlers, `outer code` has this set to element event is attached to not `inner code(if in function)`
15. `can also bind the class methods in the constructor`, so that in other constructor also this will point to previous class instance.

## OOPs ->

1. `abstraction` -> Objects in an OOP language provide an abstraction that hides the internal implementation details
2. `encapsulation` -> refers to the bundling of data with the methods that operate on that data, or the restricting of direct access to some of an object's components
3. `inheritance` -> child class will inherit all the public and protected properties and methods from the parent class
4. `polymorphism` -> representing one form in multiple forms

## Luhn's Algorithm ->

1. use to validate credit card numbers, IMEI numbers
2. Starting from the rightmost digit, double the value of every second digit
3. if doubling results in two digits number, add the digits
4. now take sum of all the digits
5. if the sum is divisible by 10 then it is a valid number

## MongoDB aggregation pipeline ->

1. with this we can find users who have their birthdays on specific dates with :`$expr, $eq, $and, $dayOfMonth, $month`
2. return birthdays of current month : `$match stage, $expr, $eq, $month`
3. return birthdays of current week : first we will convert all the birthdates to current year with project stage and using `$dateFromParts with $year, $month and $dayOfMonth`. Then we will have match stage to match for current week with : `$expr, $eq, $week`
4. `read more` -> https://medium.com/@luansantos_4481/how-to-return-birthdays-of-the-current-day-week-and-month-with-mongodb-aggregation-f4104fe82e3c
    
## ReactJS -> 
    
    1. JSX -> html with javascript , syntax extension in javascript, convert JSX to javascript object with babel for browser to understand
    2. Components -> reusable with their own logic and control, stateless, stateful, dereive data as props, return jsx onscreen
    3. virtual DOM -> represent real DOM in memory, changes only changed object state, compares previous state, performance
    4. one way data flow -> child in parent, modular and fast, easy debug react app(chrome extension by facebook)
    5. react only updates those componets that have changed
    6. react has more functionality , with JS code becomes more complex
    7. ES5 -> var app = React.createClass({render: function()}), require(), ES6 -> class app extends Component{render()}
    8. camel case react events in JSX, pass function name as event handler not string 
    9. synthetic events -> combine response of different browser native envents in common APIm so that events are uniform in diff browsers(e.preventDefault). App runs regardless of browsers
    10. list -> key, which item changed then update that only, updated components are re-rendered 
    11. form -> interact with app, alert the user when the submit button is pressed, pass event to parent 
    12. regular func as event handler -> this.handle.bind(this), arrow -> (e) => this.handle(e)
    13. no html, css in react native 
    14. angular -> complete MVC,real DOM, bi-directional, react -> view layer of MVC 
    15. render() -> return html displayed in component, each component shoul have render()
    16. state -> react object, data about component, component re-renders, behaviour of component
    17. props -> react object, stores value of attribute of tags, passed from one component to another, like data is passed in functions, this.props or props object
    18. container ->higher order component, multiple components using same logic, makes components simple and reusable
    19. embed components in another -> props.children
    20. class -> lifecycle hooks, mounting updating and unmounting, componentDidMount(),  componentWillUnmount()
    21. func -> no lifecycle hooks, easy to understand, not complex, now can be resused
    22. redux -> predictable state container, store, action -> source info for store, reducer -> how state will change in response to actions sent to store, state is immutable, so when redux state changes new copy of state creates and values are set, single store, concept of reducer
    23. flux -> action - dispatcher - store - view, triggering certain actions is the only way to update data(one way data). When dispatch triggered and store updates it emits change event that views can re-render, state is mutable, multiple store, concept of dispatcher
    24. ReactRouter -> react-router-dom package, create routes inr react app, for single page web apps, maintains consistent structures, enable multiple views in single app by defining multiple routes in react app, single html page, user navigates multiple views in same file, page will not referesh since it is a single file, improved performance, <BrowserRouter/>, <Routes/>, <Route/> (these three comping from react-router-dom)
    25. inline style with style: {{}}, or object in style: {}, css file to be imported in modules
    26. createRoot() -> create a react root for supplied container and return the root, root renders a react element to the DOM . root can also be unmounted with root.unmount(). Controles the content of container node you passed in. ANy existing DOM elements inside are replaced when render is called.  Later calls use React’s DOM diffing algorithm for efficient updates.Does not modify the container node, modifies the children of container. It may be possible to insert a component to an existing DOM node without overwriting the existing children. Using createRoot() to hydrate a server-rendered container is not supported. Use hydrateRoot() instead
    
    
## Nodejs -> 
    1. cross-platform javascript runtime env, async, event driven, non-blocking I/O, scalable, concurrency
    2. app we can make like -> video streaming app, network app, realtime app, Iot, microservice architecture
    3. req to server - event loop - simple req(event loop) and return response - thread pool(complex request) accesses external resource - event loop send response to client 
    4. nodejs is single threaded for async processsing, can handle more concurrent client req, event loop is processing model's heart in nodejs
    5. control flow of async logic is bettr with promises than callbacks
    6. I/O -> data transfer is output from one medium and input to another, medium can be network, files system etc
    7. NPM -> online repository package/module for nodejs, command line client(npm) for nodejs packages and manages nodejs versions and dependencies
    8. moduels like -> http server, stream, util, url, fs, so modules can be used in nodejs applications
    9. mongoDB -> cross platform, express- > framework fro restful apis with nodejs, mongoose -> oops based library that creates connection between nodejs and mongoDB 
    10. pros: streaming data, intensive I/O operation, fast processing, CONS -> no heavy computation, single threaded so no cpu intensive, relational database not good for nodejs
    11. event based -> event triggers various functions
    12. event loop -> handles async callbacks, 
    13. nodejs process starts, then callbacks and handlers are added to their respective queues like timer callback in timer queue, promises and next tick in microtask queue, i/o operation in I/O poll queue, setImmediate in check phase immediate queue etc. Then event loop starts checking. Starts with microtask queue. THen event loop moves to timers phase, if no more timers then loop moves to I/O and if no pending I/O then loop moves to setImmediate. 
    14. event loop blocks and wait in poll phase when appropriate, if no other callback is there then event loop will wait in I/O phase and wait for callbacks to be added to the queue and execute them.
    15. event loop explains the async process and non blocking I/O nature of nodejs.
    16. Nodejs starts - intitialises event loop - processes input script(or REPL) which perform async APIcall timer process.nextTIck() - starts processing event loop
    17. event loop performs operations relevant to that phase before executing callbacks in the phase queue, timers - pending(I/o callbacks delayed until next loop iteration) - idle, prepare - poll(I/O events, all except close timer setImmediate, node blocks here when required) - check(immediate) - close(like socket.on('close'), process.on('exit'))
   18. As Node.js starts executing your index.js file, or some other application entry point, the `Event Loop begins`    
   19. 6 phase -> tick or cycle or loop, when no pending work in event loop nodejs process exits. Program only runs as long as task are queued in event loop or call stack 
   20. poll phase ->non-blocking I/O request callbacks are executed,  run our JS code we wrote, top to bottom, can execute immediately or pass to queue for future tick of event loop
   21. When event loop is in poll phase of iteration it will execute whole code, poll phase figures our how long it should block and poll for I/O then process events in poll queue
   22. so if no timers scheduled when event loop reaches poll phase it will wait there, so if poll queue is empty it blocks and waits for any inflight I/O operations to finish before executing their callback
   23. microtasks are executed immediately if they are scheduled during poll phase rather than waiting for poll phase to complete. Microtask run after main line and at the end of each phase of event loop
    24. poll phase becomes idle when queue of poll phase is empty, poll phase waits for any pending I/O requests to finish
    25. without protocols like webSocket and server-side events, long-polling is an efficient way to handle connection with server. Nodejs uses long polling. LOng polling works on top of client-server model. Server only sends client response when data is available till that time link remains open. Long polling(study more) ????
    26. regulr polling(periodic polling) -> when data unavailable whole process fails but every request is sent to server and recieves null responses
    27. long polling in nodejs can be configured on client side, during downtime or when making new request to server the client generates event loop
    28. in long polling server only sends data when available after sending browser can submit new request almost immediately
    

    
    
    
    
    
    
    
    
    
    
    
    
