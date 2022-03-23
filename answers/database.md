# Topic: DATABASE

## Compare Relational DB (SQL) vs NoSQL. It's also really nice to know about newSQL (a kind of auto sharding DB which support SQL stuff but scale like NoSQL)

Relational DB is organized by schema, table. All records in a table must be in the same structure, follow some constraints. Relational DB guarantees ACID characteristics so it is safe and stable.

NoSQL is something that is not relational DB. Currently, it contains 4 main kinds:

- The first kind is Document. In this kind, each piece of data is a JSON document.
- The second is Key-Value DB. Simply, it is like a hash map that maps one key to one value.
- The third is Wide Column DB. Records in a table can have a different number of columns.
- The last one is Graph which is suitable for some graph-like data, for example, connections of people on a social network.

## How these 2 things can scale up?

Usually, people scale up Relational DB vertically. Add more CPU, more RAM, more storage. An additional thing we can do is sharding, that device data into different clusters, different nodes. Due to ACID characteristics, relational DB needs to do more work when writing and reading data to ensure those characteristics.
Cause NoSQL sacrifices one or some ACID characteristics, it can be easily scaled horizontally just by simply adding nodes.

## 3 normal forms in DBMS

The first normal form is about making everything atomic. It means a column stores a single value, not multiple values.

The second normal form is about removing partial dependencies. It means no column depends only on a subset of the candidate key of the relation.

The third normal form is about removing transitive dependencies. It means there is no relationship that column A depends on column B, and column B depends on column C.

## ACID of SQL and BASE of NoSQL? Why NoSQL is eventual consistency?

BASE:

- Basically Availability
- Soft state
- Eventually consistency

## CAP theorem in this case. [This is a so nice graph](http://blog.nahurst.com/visual-guide-to-nosql-systems)

In CAP theorem:

- C stands for Consistency
- A stands for Availability
- P stands for Network Partition

It's kinda confused when people say we can only choose 2 out of three things because network partition is not something we can choose in a distributed system.
In the good condition, when there is no network partition, a system can guarantee both consistency and availability. But when the network fault comes, we have to choose one thing between Consistency and Availability to sacrifice.

## What is parameterized statement (in Java it's prepared statement)? How does it work **internally**?

A parameterized statement is a statement that we can customize, like changing filter conditions.

## What is SQL injection? how to avoid it?

SQL injection is when the attacker sends a parameter that contains SQL queries and hopes this query will be executed in the system's database.
SQL injection can be avoided by escaping special characters in the params that users submit to the system.

## How many "requests" you have to send to Database in a single prepared statement query? // one for compile and one for execute

It includes 2 steps, compile and execute.

First, the database management system will compile the statement template then store the result without executing it.

Next, the necessary values will be bound into the compiled statement template, then the statement will be executed.

## Can you reuse the compiled query multiple times? (does it help to speed up your application?)

Yes, we can reuse the compiled query multiple times with different bound values. And yes it speeds up the application.

## How indexing works internally?

To be defined.

## What algorithm and data structure indexing used? And why?

Index can use a hash table or B-Tree.

## How composite indexing works?

It's like a single index but the key is a compound key, which is the combined values of these columns that are indexed.

## How to know your query is using index?

By adding "explain" in front of the query, we will get how the query ran and if it uses index or not.

The query optimizer will use index automatically if possible and chose the index that it thinks is the best. And we can force our query to use an index by specifying it in the query.

## How index work in this case: `WHERE age = 5` and `Where age > 5`? The complexity to go to the next record?

It depends on the index type is hashing or B-Tree. If the index type is B-Tree, there is no difference between these two cases. The complexity to go to the next record is O(1) because all the leaves are linked together as a doubly linked list.

## Indexing with char?

To be defined.

## The complexity of SQL query? How to measure it? How SQL optimize a query?

To be defined.

## Compare `WHERE id = 'a' AND id = 'b' AND id = 'c'` vs `WHERE id in (a, b, c)`?

In MySQL, the values in the IN list will be sorted and MySQL will use binary search to check if the current value is in the list. So the check operator will cost O(log N) complexity, with N being the number of elements that need to be compared.

Some links to read more:

- https://www.postgresql.org/message-id/12553.1135634231@sss.pgh.pa.us

- https://www.cybertec-postgresql.com/en/postgresql-indexing-index-scan-vs-bitmap-scan-vs-sequential-scan-basics/

- https://subscription.packtpub.com/book/big_data_and_business_intelligence/9781785284335/11/ch11lvl1sec104/running-bitmap-heap-and-index-scan

- https://www.oreilly.com/library/view/high-performance-mysql/9780596101718/ch04.html"

## Complexity of this query `SELECT * FROM abc ORDER BY name LIMIT 10 OFFSET 1000000` // SELECT 10 record from offset 10^6 after sort by name (which is a char)? How to optimize it?

O(N log N) with N being the total number of records.

We can optimize the query by indexing the column name.

## What is the complexity of COUNT(*) query?

In MySQL, it depends on the storage engine that the table uses. For MyISAM, the total number of rows is stored with each table so the complexity is O(1), but for InnoDB, it is O(N).

## How to write query to avoid full table scan?

We need to write a query that takes advantage of index if any.

## Complexity of JOIN, INNER JOIN, OUTER JOIN?

To be defined.

## What is Database Replicating? When we need it?

Database replicating is the act of making one or many copies of a database to increase the availability of data.

## What is bin log? How Master DB sync with Slave DB?

When data is written into DB, first it will be stored in Write Ahead Logs. Master DB send these log to Slave DB so Slave DB can also have those changes.

## Can a Slave DB be a slave of another Slave DB (we do not need to sync from Master DB directly)?

Yes it can.

## What is Database Sharding? When we need it?

Sharding happens when a database is too big so the query time increases. We shard database to improve query time and also increase the availability of the system. If one shard is down, there is only a portion failure.

## Which rule we can apply to DB Sharding?

- Ensure unique key for the whole system.

- Distribute load.

## How to ensure primary key is globally unique when sharding?

We can have a key generating system that generates keys for all servers. But this server can be a central point of failure. To improve that, we can have multiple servers to generate keys, each server is in charge of some range of keys.

## How we can shard a table to multiple tables (same server) and multiple DB (multiple servers)?

To be defined.

## How query can work when we sharding? for example query but the data is in different tables/dbs?

For a query that we might know exactly where data is using its key, we can detect which shard is holding necessary data and query on this shard.

For a query that data might be on a lot of shards, we can execute the query on all possible shards then aggregate data later.

## What is database transaction?

Relational DB ensures Atomicity by Transaction. A transaction is a collection of operations. Either all of those operations are executed, or non of them is executed. It ensures there is no time when something is failed in the middle and we have no idea when or how to roll back.

## How rollback works internally?

To be defined.

## What is dirty read, dirty write, read skew, phantom read, write skew, lost update?

Dirty read is when transaction A is allowed to read a value that has been modified by transaction B but has yet been committed. This may cause a problem when transaction B fails and rollback happens, so the value that A reads is not the value in database.

Dirty write is when transaction A is allowed to write a value that has been modified by transaction B but has yet been committed.

Read skew is when someone needs to read one value multiple times in a transaction. But the result each time is different.

Phantom read is when a transaction needs to get a collection of records multiple times in a transaction. But the number of records each time is different.

Write skew is when someone needs to read some object then update some object based on the result of the read value.

Lost update is a special case of write skew when read and update happen with the same object.

Read committed is a weak isolation level that is used to guarantee no dirty read and no dirty write. It assures that all object that can be read is already committed and no write can happen to an uncommitted object.

2 stronger isolation levels are snapshot isolation and serializable snapshot isolation. For snapshot isolation, a transaction can read the old version of a value while other transactions are writing. For serializable snapshot isolation, a transaction cannot read while other transactions are writing. It is called 2PL - two-phase locking.

## How transaction work when there are many concurrent requests?

To be defined.

## How to avoid race condition in DB? Read/Write lock?

To be defined.

## Distributed transaction? How to make a transaction when a query needs to access multiple DB?

A distributed transaction is needed when data that suppose to be in a transaction is stored in different databases. There is a technique called 2 phase commit (2PC) that helps to resolve this situation.

There will be a coordinator which orchestrates the whole transaction. When the transaction begins, the coordinator generates a global transaction ID for all participants of this transaction. Each participant will execute their own transaction that attaches to the global transaction. When all local transactions are done, the coordinator sends the prepare request for all participants. This is the first phase - the prepare phase in 2PC. Participants can respond yes or no, indicate if they can commit this transaction or not. And the "yes" answer is the promise that it will be able to commit this transaction no matter what. If all participants respond "yes", the coordinator can decide to commit this transaction and send the commit request to all participants. This is the second phase of 2PC, the commit phase. Once the commit decision is made by the coordinator, it is irreversible. It will keep resending commit requests to participants no matter what. If the coordinator fails, the participant must keep the status of being able to commit this global transaction no matter what.

## What is Try-Confirm Cancel?

To be defined.
