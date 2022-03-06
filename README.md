# Backend SWE interview questions

This repo contains technical questions (and answers) on several topics you might want to prepare for an interview for BE position.

Most of the questions comes from [vietnakid](HTTPS://github.com/vietnakid/learning-material/blob/master/computer-science/cs_questions.md). I wrote down the brief answers and add some new questions/topics.

The answers to those questions bases on my humble knowledge. If you find some things want to improve or fix, please fire a PR, I would be more than happy.

## TOPICS

- [NETWORKING](#networking)
- [OPERATING SYSTEM](#operating-system)
- [DATABASE](#database)
- [SECURITY](#security)

## NETWORKING

[Answers here](/answers/networking.md#topic-networking)

1. Read the concept of TCP in [this wiki page](HTTPS://en.wikipedia.org/wiki/Transmission_Control_Protocol) and try to understand all the concepts of it (deeply):
    - How TCP open a connection? What does it need to open a connection?
        - Why there are 3 way handshakes but not 2 way?
        - What is syn, ack mean?
        - Why they have to send 2 "random" sequence numbers? The purpose of this sequence number?
        - What if the 3rd handshake fail? How the server can detect it and what does it do in this case?
    - How TCP handles the connection?
        - What happens if some bits are wrong due to connection errors? How to detect them and fix them?
        - How the timeout is handled? what if the timeout is expired?
        - What will happen if some "packet" is missing on the way?
        - How to detect the appropriate number of packets to send (speed of sending packet)?
    - How TCP close the connection?
        - What if the internet is dropped in the middle of the connection? Or in case one peer is crash?
    - How long you can keep a TCP connection alive?
2. What are the differences between TCP and UDP? And in which case we use which?

3. How Ping command works? What is TTL? How does TTL will be changed?

4. How HTTP works?
    - Why did people say that HTTP is stateless? The reason they make it stateless?
    - Can we make a persistent HTTP connection? pros and cons of this way?
    - Why HTTP require cookie each time we send the request?
    - Can someone use your cookie and log in your Facebook account? How to migrate this?
    - What is HTTP session? How does authentication work in HTTP? What is JWT?
    - Which type of "data" HTTP can help us to get or push? (binary file? image? text file? video file? music file?)
    - REST/RESTful?
    - AJAX technique?
    - How HTTPS work?
    - Learn about some useful headers

5. When you type "google.com" into your browser, that will happen when you type enter till everything is displayed on your screen?
    - DNS lookup (in case you already access google.com before and also in case you do not know the IP of google.com)
        - Which protocol DNS use and why?
        - The other of place to look up DNS.
    - TCP or UDP will be used in this case? why?
    - How to know "google.com" require HTTP or HTTPS? how browser can know and redirect from HTTP to HTTPS?
    - After you get the HTML content for "google.com" how to get the *.js and image files?
    - When getting *.js or image files do why use another TCP connection or use the same one as in the get HTML content? How DNS lookup work in this case?
    - After your browser display "google.com" fully, is there any connection open?
    - Caching can apply to which steps? How caching applied?

6. What is the connection pool? It's advantages and disadvantages? How to implement connection pool in your programing language?

7. What is socket?
    - Why do we need socket? Why socket is a "file" in linux?
    - What is src port when you create a connection to a "server"?
    - How one server can handle multiple connections to the same port? [Good answers here but read all answers](https://stackoverflow.com/questions/3329641/how-do-multiple-clients-connect-simultaneously-to-one-port-say-80-on-a-server)
    - What is the maximum number of connections a server can handle? (if it has unlimited resource) (in case of the same client and in case of multiple clients)
    - When you open multiple tabs on your chrome, how OS knows which packet (both sending and receiving) correspond to which tab? (how about in case you open many tabs to the same page "for eg: google.com")
    - What are the maximum numbers of connection your machine can connect to "google.com" (if you have unlimited resource)
    - Can two processes listen to the same port on your machine? Why? How?
    - What is buffer? why we always need buffer when working with "file"?
    - What is unix socket? When to use it?

8. What is TCP proxy? reverse proxy? and VPN?
    - How your router at your home works?
        - Inside LAN network, it uses IP or MAC address? Why?
        - How does it know which packet comes from (or arrive at) which machine?
        - What is the difference between Hub and Switch inside LAN?
        - How src IP/PORT and dst IP/PORT change on the way to the server?
    - How load-balancer works?
        - When we send a packet to a load-balancer how does it forward to the desired server? (Does it keep any data on its memory?)
        - When the server wants to send data back to the client, does the connection need to go through the load-balancer?
        - What is different between reverse proxy and load-balancer?
        - Can load-balancer be a bottleneck? (Because it is the end-point of too many requests) (bottleneck about RAM or CPU or Network?)
        - Try to understand everything in [this page](https://softwareengineering.stackexchange.com/questions/312956/what-does-a-load-balancer-return) (all the answers)

## OPERATING SYSTEM

[Answers here](/answers/os.md#topic-operating-system)

1. What is process, thread? What are the differences between them?
    - What data process, thread need to live? Why they said that Thread is a lightweight process?
    - How CPU switch (context switch) between processes/threads? How data is to ensure safety? (in case single CPU core and multiple CPU cores)
    - What is multi-process and multi-thread? When we should you which one?
        - Process has how many states? How does it change between each state?
        - Scheduling algorithm
        - What will happen if a process is waiting? Or a thread is sleeping?
        - How CPU detects that a thread is sleeping? Or detect when it wants to run?
    - What is thread-pool? How to use it? Describe how to create a thread-pool in your programming language
    - Can 2 different processes access or change data of each other address space? (this question may make you confuse with your knowledge about virtual memory)
        - Can 2 processes use the same library (for eg: libc is required to every process)? How?
        - How does debugger work? How it can attach to a running process and change data of that process?
    - How 2 processes can communicate with each other? (There are a lot of ways but focus on the OS's way)
    - What is child-process? How to create a child-process?
        - What data a child-process have when we create it?
        - Can it read/write data on it's parent process?
        - What is copy on write (COW), Dirty COW? **(this concept is important to understand OS)**
        - What will happen when child-process changes a variable of parent process?
        - If file descriptor also be inherited by the child process. What if 2 processes can handle a same file descriptor or even a same socket?

2. Concurrency vs Parallels? (in case single CPU core and multiple CPU cores)
    - What is critical zone?
    - What is race condition and how to handle this case?
    - What is locking mechanism? mutex? semaphore? spinlock? read lock vs write lock?
    - What is deadlock and how to avoid deadlock?

3. How does memory is managed in the OS?
    - What is virtual memory? Why do we need it? How does it work?
        - How large virtual memory is?
        - What is paging?
        - Can 2 processes map to the same physical address? How and in which case?
    - What is heap space and stack space?
    - What will happen with memory when you open an application?
    - What will happen you call another function (with parameters) or return from a function?
        - What will happen with stack? (why we do not use heap here?)?
        - What will happen with registers?
    - What causes stack overflow?
    - What is dynamic allocating? How does it work?
        - How does deallocation work?
        - What happens when your computer is full of memory?
    - Why you do not need to "deallocate" local variable?
    - How does Garbage Collection work? When it will be triggered?
    - What is a pointer? What difference between pass by value and pass by reference?
    - Where global variable will be saved?

4. Why in Linux everything is "file"?
    - How does mouse/keyboard/monitor... communicate with your computer?
    - What is file descriptor?
    - What is buffer? Why do we need buffer?
    - What will happen if 2 processes read/write to the same file?

5. What is system call (syscal)?
    - How to do a syscal?
    - What happens with CPU when we execute a syscal?
    - What is user space and kernel space?

6. Caching:
    - What is in-memory cache? (memcached/redis)
    - LRU? implement LRU in your program language! (How about multi-thread?)
    - How to migrate Cache stampede?
    - Quicksort vs Merge sort. Which is faster? Why? How they use these 2 sorting algorithms in real life?

- Good resources: [Overview of OS syntax, try do dive deeper to each concept](https://medium.com/cracking-the-data-science-interview/the-10-operating-system-concepts-software-developers-need-to-remember-480d0734d710)

## DATABASE

1. Compare Relational DB (SQL) vs NoSQL. It's also really nice to know about newSQL (a kind of auto sharding DB which support SQL stuff but scale like NoSQL)
    - How these 2 things can scale up?
    - 3 normal forms in DBMS
    - ACID of SQL and BASE of NoSQL? Why NoSQL is eventual consistency?
    - CAP theorem in this case. [This is a so nice graph](http://blog.nahurst.com/visual-guide-to-nosql-systems)

2. What is parameterized statement (in Java it's prepared statement)? How does it work **internally**?
    - What is SQL injection? how to avoid it?
    - How many "requests" you have to send to Database in a single prepared statement query? // one for compile and one for execute
    - Can you reuse the compiled query multiple times? (does it help to speed up your application?)

3. How indexing works internally?
    - What algorithm and data structure indexing used? And why?
    - How composite indexing works?
    - How to know your query is using index?
    - How index work in this case: `WHERE age = 5` and `Where age > 5`? The complexity to go to the next record?
    - Indexing with char?

4. The complexity of SQL query? How to measure it? How SQL optimize a query?
    - Compare `WHERE id = 'a' AND id = 'b' AND id = 'c'` vs `WHERE id in (a, b, c)`?
    - Complexity of this query `SELECT * FROM abc ORDER BY name LIMIT 10 OFFSET 1000000` // SELECT 10 record from offset 10^6 after sort by name (which is a char)? How to optimize it?
    - What is the complexity of COUNT(*) query?
    - How to write query to avoid full table scan?
    - Complexity of JOIN, INNER JOIN, OUTER JOIN?

5. What is Database Replicating? When we need it?
    - What is bin log? How Master DB sync with Slave DB?
    - Can a Slave DB be a slave of another Slave DB (we do not need to sync from Master DB directly)?

6. What is Database Sharding? When we need it?
    - Which rule we can apply to DB Sharding?
    - How to ensure primary key is globally unique when sharding?
    - How we can shard a table to multiple tables (same server) and multiple DB (multiple servers)?
    - How query can work when we sharding? for example query but the data is in different tables/dbs?

7. What is database transaction?
    - How rollback works internally?
    - What is dirty read, dirty write, read skew, phantom read, write skew, lost update?
    - How transaction work when there are many concurrent requests?
    - How to avoid race condition in DB? Read/Write lock?
    - Distributed transaction? How to make a transaction when a query needs to access multiple DB?
    - What is Try-Confirm Cancel?

8. Compare:
    - PostgreSQL vs MySQL

## SECURITY

1. Hash vs Encrypt vs Encode
    - Are there any way we can crack Hash
    - Symmetric vs asymmetric encryption? AES vs RSA?
    - Fast Hash vs Slow Hash?
    - When we use Encode??
    - What is the perfect hash function?
    - What is the load factor of hashing?

2. SSL/TLS
    - How to verify a certificate? How many kinds of certificates are there?
    - What is CA? how to verify certificate of a CA?
    - What is digital signature? What is HMAC?

3. How to store credential information efficiency? (user password, config key, database credential, user information, secret key,.... )

4. Describe a way to defense DDOS? (actually, there are many kinds of DDOS not just network or memory, so this question is pretty complicated)
