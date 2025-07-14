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
