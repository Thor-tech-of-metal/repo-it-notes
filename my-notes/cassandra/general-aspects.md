Cassandra general
==========

* Cassandra is a Big TableDB which is very good for insertion data and searching by unique ids ( a combination of partition keys).

*  Cassandra tables should be design based on how they  are going to be read.

*  Cassandra does not perform search it gets the row or rows based on a get operation by keys.

*  Each table can have a primary key and a combinations of partition keys.  The combinations of partitions keys said how to the record is going to be persisted in a node and the compose combination of partitions keys made the unique key.

*  It is good for reading key-value pairs

*  It iis good for writing pre-organized data.

*  It is not very good for search with where clause for not indexed columns even primary keys.  If the column in the search clause is not indexed it can return an error.  The select should be performed using the partitions keys in the where clause as unique id.  Rule  where clause should always include a combination of partitions keys and other columns.

Architecture
==========

*)Peer to peer distributed database management system. All nodes are the same in cassandra. No master/slave. It can  Read and write anywhere any node.

*)It use a gossip protocol which keep searching for changes.

*)Automatically partition the data across all nodes.

*)No single point of failure-> this is because all nodes are the same can be replaced easy.

*)You decive how many copies fo the data you want in the system.


Colum famliy schema
====================
* more flexible than the clasic table colum system. Maps in cells.
* primary and secondary indexes.

Write
=====
1) it writes in to a commit log  2) Mem table  3) Disk

Keyspace
========
A keyspace (or key space) in a NoSQL data store is an object that holds together all column families. It is the outermost grouping of the data in the data store. It is a similar concept of date base schema.
A keyspace can have a number of column families.We can have column families and super column families.

Keys
====
The Partition Key is responsible for data distribution across your nodes.
The Primary Key is equivalent to the Partition Key in a single-field-key table.

Primary key
============
PRIMARY KEY( (partitionKeys) , (primaryKey) )
*) COMPOSITE the primary key can also be COMPOSITE (aka COMPOUND), generated from more columns.

create table stackoverflow (
  key_part_one text,
  key_part_two int,
  data text,
  PRIMARY KEY((key_part_one, kp3), key_part_two)
  );

In  a situation of COMPOSITE primary key, the "first part" of the key is  called PARTITION KEY (in this example key_part_one is the partition key)  and the second part of the key is the CLUSTERING KEY (key_part_two)
For example:
     PRIMARY KEY ((id, ds), caseid) where (id, ds) are partition keys. caseid is primary key.
     PRIMARY KEY (caseid, id, ds) where caseid is partition key.  id, ds are primary keys.


It is always good to sort all information by partition keys
a ) AuditLogByUser  el PartitionKey es
object user extends UUIDColumn(this) with PartitionKey[UUID]

b)  AuditLogBySubject   donde el PartitionKey
object subjectId extends UUIDColumn(this) with PartitionKey[UUID]

Transaction

Cassandra is a sequential access DB which guaranty data integrity. Cassandra does not use RDBMS ACID transactions with rollback or locking mechanisms, but instead offers atomic, isolated, and durable transactions with eventual/tunable consistency
* Atomic
Everything in a transaction succeeds or the entire transaction is rolled back.
* Consistent
A transaction cannot leave the database in an inconsistent state.
* Isolated
Transactions cannot interfere with each other.
* Durable
Completed transactions persist in the event of crashes or server failure.
