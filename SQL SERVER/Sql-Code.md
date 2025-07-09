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
