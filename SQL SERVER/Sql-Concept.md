# Candidate Vs Primary

`Candidate Key` – A Candidate Key can be any column or a combination of columns that can  **qualify as unique key in database** . There can be multiple Candidate Keys in one table. Each Candidate Key can qualify as Primary Key.

`Primary Key` – A Primary Key is a column or a combination of columns that  **uniquely identify a record** . Only one Candidate Key can be Primary Key.

# Temporary Table

A temporary table in SQL is a table that exists temporarily and is typically used to store intermediate results that you need to access multiple times within a session.

CREATE TABLE #TempTable (
    ID INT PRIMARY KEY,
    Name NVARCHAR(50),
    Age INT
);


## **Cascading Referential Integrity Constraints**

The Cascading Referential Integrity Constraints in SQL Server are the foreign key constraints that tell SQL Server to perform certain actions whenever a user attempts to delete or update a primary key to which an existing foreign keys point

###### SET NULL:

If a user tries to delete or update statement(s) that will affect rows in the foreign key table, then those values will be set to NULL when the primary key record is deleted or updated in the Primary key table. The important thing that we need to keep in mind that the foreign key columns affected must allow NULL values.

###### CASCADE:

If a user tries to delete the statement(s) which will affect the rows in the foreign key table, then those rows will be deleted when the primary key record is deleted. Similarly, if an update statement affects rows in the foreign key table, then those rows will be updated with the value from the primary key record after it has been updated.

###### SET DEFAULT:

If a delete or update statement affects rows in a foreign key table, then all rows containing those foreign keys are set to the default value. All foreign key columns in the related table must have default constraints defined on them.

###### NO ACTION:

This is the default action that SQL Server performs. This specifies that if an update or deletes statement affects rows in foreign key tables, then the action will be denied and rolled back. An error message will be raised.

## **Sequence Object**

A sequence is an object in SQL Server that is used to generate a number sequence. This can be useful when we need to create a unique number to act as a primary key.

The Sequence Object is one of the new features introduced in SQL Server 2012. A sequence is a user-defined object and as its name suggests it generates a sequence of numeric values according to the properties with which it is created. It is similar to the Identity column, but there are many differences between them that we will discuss in our next article. But the most important point to keep in mind is that the Sequence Object in SQL Server is not limited to a column or table but is scoped to an entire database.
