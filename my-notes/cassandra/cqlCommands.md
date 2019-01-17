Show all keyspaces

cqlsh> DESCRIBE keyspaces;

#####Use a keyspcase
cqlsh> use jot;

#####Drop  a keyspcase
```
cqlsh:jot> DROP KEYSPACE jot;
```

#####Show all tables
```
cqlsh:jot> describe tables
```
#####Delete all records in a table
```
cqlsh:jot> TRUNCATE contextus.auditlogs;
```

#####Delete a record in a table
```
cqlsh:jot> delete from  contextus.auditlogs where id=1626h3h18;
```
#####Drop a table
```
cqlsh:jot> drop table notes;
```
##### Describe a column

```
cqlsh:jot> DESCRIBE COLUMNFAMILY notes ;
```
##### Add a column
```
cqlsh:jot> ALTER TABLE usersbyemail ADD lastLoggedIn timestamp;
```

#####Change a column type
```
cqlsh:jot> ALTER TABLE users ALTER bio TYPE text;
```

#####Simple select
```
cqlsh:jot>  select * from tasks where assignee ='e69907a8-f487-48bf-ba0c-3b16acf29db2';
```
#####Put  resul in a file
```
cqlsh -e "select * from contextus.userwidgets where user = 5842dad3-500d-41f2-b73e-87df08e43dcb" >> out.txt
```
