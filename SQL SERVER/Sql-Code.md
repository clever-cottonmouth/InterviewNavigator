--==================================DUPLICATE EMAILS

```sql
SELECT MIN(id) AS id,
TRIM(LOWER(email)) AS cleaned_email
FROM users
GROUP BY cleaned_email
ORDER BY id
```

--=================================Highest salary each departments

```sql
select
d.name as department_name
, e.id as employee_id
, first_name
, last_name
, salary
from employees e
join departments d on e.department_id = d.id
where (department_id , salary) in
(select
department_id
,  max(salary) as highest_salary
from employees
group by 1)
order by d.name
```

## How do you handle duplicate rows in a SQL query?

```sql
SELECT FirstName, LastName, DepartmentID, COUNT(*) as EmployeeCount
FROM Employees
GROUP BY FirstName, LastName, DepartmentID
HAVING COUNT(*) > 1;
```

## Write a SQL query to find the top 3 departments with the highest average salary.

```sql
SELECT TOP 3
    d.DepartmentName,
    ROUND(AVG(e.Salary), 2) AS AverageSalary
FROM Employees e
INNER JOIN Departments d
    ON e.DepartmentID = d.DepartmentID
GROUP BY d.DepartmentName
ORDER BY AverageSalary DESC;
```

## Write a SQL query to find the employees who have worked for more than 5 years.

```sql
SELECT 
    e.EmployeeID,
    e.FirstName,
    e.LastName,
    e.HireDate,
    DATEDIFF(YEAR, e.HireDate, GETDATE()) AS YearsOfService
FROM Employees e
WHERE DATEDIFF(YEAR, e.HireDate, GETDATE()) > 5;
```

## A database cursor is an object that enables traversal over the rows of a result set. It allows you to process individual row returned by a query.

```sql

DECLARE 
    @product_name VARCHAR(MAX), 
    @list_price   DECIMAL;

DECLARE cursor_product CURSOR
FOR SELECT 
        product_name, 
        list_price
    FROM 
        production.products;

OPEN cursor_product;

FETCH NEXT FROM cursor_product INTO 
    @product_name, 
    @list_price;

WHILE @@FETCH_STATUS = 0
    BEGIN
        PRINT @product_name + CAST(@list_price AS varchar);
        FETCH NEXT FROM cursor_product INTO 
            @product_name, 
            @list_price;
    END;

CLOSE cursor_product;

DEALLOCATE cursor_product;
```
