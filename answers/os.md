# Topic: OPERATING SYSTEM

## What is process, thread? What are the differences between them?

A process is like a program in execution. And a thread is a segment of a process. Each process has its own memory and is isolated. Meanwhile, threads of the same process can easily communicate with other threads, access common variables, memory.

## What data process, thread need to live? Why they said that Thread is a lightweight process?

Thread is a lightweight process because it does not cost much CPU to switch between threads as between processes.

## How CPU switch (context switch) between processes/threads? How data is to ensure safety? (in case single CPU core and multiple CPU cores)

When process context switching happens, the state of the current process will be stored in Process Control Block, so this process can be resumed later. Data in memory of the current process will be switched into virtual memory, then this memory will get flushed to store data of the next process.

When thread context switching happens, the state of the current thread will be stored in processor's cache and translational lookaside bsuffer, so the thread can be resumed later.  There is no memory switching involved.

## What is multi-process and multi-thread? When we should you which one?

Multi-processing is when more than 2 processes are running simultaneously on a computer. This is probable in a multi-processor computer, where each processor handles a process.

Multi-threading is when more than 2 threads created by the same process are running simultaneously.

## Process has how many states? How does it change between each state?

Basically, a process has 5 states: new, ready, running, wait, and terminate. New is the status of the process when it is created. At the ready status, the process waits to be assigned to a processor. When the process is assigned to a processor, its status becomes running and the processor executes the process instructions. If the process need something like I/O, or the CPU is assigned for another process, process status will become waiting. When all the instructions are executed, or the process is terminated by OS, it moves to terminate state where it waits to be removed out of the main memory.

## Scheduling algorithm

There are many types of scheduling algorithms like first come first serve, shortest job first, shortest remaining time first, round-robin, etc.


## What will happen if a process is waiting? Or a thread is sleeping?

When a thread is sleeping, other threads might be running.

When a process is waiting, OS can run another process.

## How CPU detects that a thread is sleeping? Or detect when it wants to run?

OS has an OS scheduler that keeps track of the list of processes and their status. When the thread goes to sleep, it tells the scheduler that it gives up its time slide, and it shouldn't be wake up until a certain time has elapsed. The next time the scheduler looks at this process, if the time has elapsed, it will change this thread status as ready to run.

## What is thread-pool? How to use it? Describe how to create a thread-pool in your programming language

Thread pool is a design pattern that's used to manage concurrent execution. It is also called as worker model. A thread pool has a limited number of threads to allocate for concurrent execution.

## Can 2 different processes access or change data of each other address space? (this question may make you confuse with your knowledge about virtual memory)

Cause memory can be used by a process at this time and later by another process, yes an address space in general does not belongs to any process and can be changed by many processes, but in a certain time, an address space belongs to a process only and can only be modified by this process.

## Can 2 processes use the same library (for eg: libc is required to every process)? How?

It is possible if the library is a shared library, not a static one. Each process has its own virtual memory address that refers to the same physical memory address that stores the shared library.

## How does debugger work? How it can attach to a running process and change data of that process?

To be defined.

## How 2 processes can communicate with each other? (There are a lot of ways but focus on the OS's way)

It can use a shared resource or pass messages to other processes.

## What is child-process? How to create a child-process?

Child process is a process created by another process. Child process inherits most of properties from its parent, such as environment settings, process directory, from its parent. It does not inherit some properties like process id, lock...

## What data a child-process have when we create it?

As above.

## Can it read/write data on it's parent process?

No, it cannot. If it wants to communicate with its parents, it has to use a separate shared memory segment or use a socket.

## What is copy on write (COW), Dirty COW? **(this concept is important to understand OS)**

Copy on write is when multiple callers ask for a copy of a resource, OS can return the pointer to the old resource and only make the private copy for a caller when necessary, like when the caller wants to modify this resource. The advantage is if the caller makes no modification, no private copy needs to be created.

## What will happen when child-process changes a variable of parent process?

Child process cannot change variables of its parent.

## If file descriptor also be inherited by the child process. What if 2 processes can handle a same file descriptor or even a same socket?

can refer [here](https://www.cs.ait.ac.th/~on/O/oreilly/perl/cookbook/ch17_10.htm)

## Concurrency vs Parallels? (in case single CPU core and multiple CPU cores)

To be defined.

## What is critical zone?

Critical zone or critical region is the segment of code where processes access shared resources.

## What is race condition and how to handle this case?

Race condition is when two threads access a variable at the same time. It can lead to data inconsistency if the operations are executed in a certain order. To prevent this we can take advantage of some locking mechanisms.

## What is locking mechanism? mutex? semaphore? spinlock? read lock vs write lock?

Mutex is a mutual exclusive flag to detect if the desired resource is free and claim it for use.

Semaphore is a generalized mutex, to control the number of available resources.

Spinlock is a mechanism in which a process keeps asking for the availability of the resource via polling.

## What is deadlock and how to avoid deadlock?

Deadlock is when there is a circle where some processes lock something and wait for something that other processes have already locked.

Deadlock happens when all of these conditions happen:

- Mutual exclusion: It means processes want to access the same resource.
- Hold and wait: When processes need more than one resource and it already has some, it will hold them and wait for the rest.
- No preemption: A process can not take away resource that is being held by other processes.
- Circular wait.
This can be avoided by making processes release their locked variable when they cannot get the other necessary resource, or granting some preemption permission for some processes.

## How does memory is managed in the OS?

To be defined.

## What is virtual memory? Why do we need it? How does it work?

Virtual memory is a memory management technique where secondary memory (eg disks) can be used as main memory like RAM. Virtual memory allows computers to operate quite normally when memory shortages happen.

When a process is in use, its data is stored in a physical address using RAM. If at any point, RAM space is needed for something more urgent, data can be swapped out of RAM into virtual memory and swapped back again when needed.

## How large virtual memory is?

The size of virtual memory is unlimited. Actually, it is limited by the disk space but the disk space is quite large so we can consider it unlimited.

## What is paging?

Paging is the memory management mechanism that allows OS to get the processes from the secondary memory to the physical memory in form of fixed-size blocks called pages.

## Can 2 processes map to the same physical address? How and in which case?

Yes. Each process has its virtual memory address and can be mapped to the same physical memory address when it is processed by CPU. The condition is they need to take turns to be processed.

## What is heap space and stack space?

Heap space is for dynamic memory allocation. Stack space is for static memory allocation.

## What will happen with memory when you open an application?

The application will be loaded to RAM when we open an application.

## What will happen you call another function (with parameters) or return from a function?

When we call another function, local variables of the new function will be put to stack, and the stack register will be moved to the appropriate position. If the function takes parameters, it will create a duplicate version of those parameters (If the parameter is a pointer, it still creates a new pointer that points to the same address).

When a function returns, local variables will be pop out of stack and the stack pointers will also be moved to the appropriate position.

## What will happen with stack? (why we do not use heap here?)?

As above.

## What will happen with registers?

As above.

## What causes stack overflow?

Stack overflow happens when the stack memory runs out. The most common cause of stack overflow is infinite recursion.

## What is dynamic allocating? How does it work?

Dynamic allocation is the act of asking for a specific segment of memory from the OS.

## How does deallocation work?

Deallocation announces for the OS that this segment of memory is free now and can be used by other processes.

## What happens when your computer is full of memory?

To be defined. (It will throw error?)

## Why you do not need to "deallocate" local variable?

Cause local variable is allocated in stack and will be destroyed automatically after the function returns.

## How does Garbage Collection work? When it will be triggered?

Garbage Collector (GC) will detect which object in heap memory has no reference. It means this object cannot be used anymore and it's safe to sweep this object away. GC will run periodically for languages that have GC. Besides, languages like Java or Python have a mechanism to invoke GC manually.

## What is a pointer? What difference between pass by value and pass by reference?

Pointer is the address of a variable. Pass by value means passing only the value of the variable, while pass by reference means passing the address of this variable in the memory.

## Where global variable will be saved?

Process memory is divided into four sections:

- Text section: when the code is stored.
- Data section: when static and global variables are stored.
- Stack section: where local variables are stored.
- Heap section: where dynamically allocated variables are stored.

## Why in Linux everything is "file"?

It will create a uniform interface for operations on Linux systems. To be more exact, everything in Linux is a stream of bytes that is represented as a file descriptor.

## How does mouse/keyboard/monitor... communicate with your computer?

It streams a stream of bytes into our computer.

## What is file descriptor?

File descriptor is a unique identifier for a file or input/output resources.

## What is buffer? Why do we need buffer?

Buffer is a segment of memory that is reserved to store necessary data being processed. Buffer helps reduce the processing time.

## What will happen if 2 processes read/write to the same file?

If 2 processes read/write to the same file, it means they use the same file descriptor to access this file, also the file offset. So the changes that one process does with the shared file are visible to the other process. ([More](https://walkerlala.github.io/archive/what-if-write-to-the-same-file.html))

## What is system call (syscal)?

A syscall is a programmatic way that allows a computer program to request a service from the kernel of the operating system, on which the program will be executed.

## How to do a syscal?

Some libraries provide functions that allow us to interact with the kernel.

## What happens with CPU when we execute a syscal?

CPU will execute the system call handler, which will perform some action to fulfill the syscall. ([More](https://www.ibm.com/docs/en/aix/7.2?topic=calls-understanding-system-call-execution))

## What is user space and kernel space?

Memory is divided into kernel space and user space:

- Kernel space is where the code of the kernel is stored, and executed.
- User space is where the code of everything other than the kernel is stored and executed.

## What is in-memory cache? (memcached/redis)

In-memory cache is the data storage layer between the application and the database. It stores data in memory which has a much fast data access speed so it is used to speed up the application.

## LRU? implement LRU in your program language! (How about multi-thread?)

Least recently used is a strategy to invalidate cache. As the name already said, it will remove the least recently used data when the cache is full. We can implement LRU using a combination of hashmap and a doubly linked list.

## How to migrate Cache stampede?

Cache stampede happens when a lot of data need to be queried at the same time but most of them haven't been cached yet, so the number of queries that need to be executed on database is huge. We can mitigate cache stampede by warming cache, cache locking, or predicting when the cache is expired so we can update cache.

## Quicksort vs Merge sort. Which is faster? Why? How they use these 2 sorting algorithms real life?

To be defined.
