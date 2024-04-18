185
SELECT d.Name AS Department, e1.Name AS Employee, e1.Salary
FROM Employee e1 
JOIN Department d ON e1.departmentId = d.Id
WHERE 3 > (SELECT COUNT(DISTINCT e2.Salary)
        FROM Employee e2
        WHERE e2.Salary > e1.Salary AND e1.DepartmentId = e2.DepartmentId
        )


193:
select b.id
from Weather a
cross join Weather b
where b.recordDate - a.recordDate = 1
and b.temperature - a.temperature > 0




570:
SELECT name 
FROM Employee 
WHERE id 
IN 
(
    SELECT managerId 
    FROM Employee 
    GROUP BY managerId 
    HAVING count(*)>=5
)




1193:
SELECT 
    TO_CHAR(trans_date, 'YYYY-MM') AS month,
    country,
    COUNT(*) AS trans_count,
    COUNT(CASE WHEN state = 'approved' THEN 1 END) AS approved_count,
    SUM(amount) AS trans_total_amount,
    SUM(CASE WHEN state = 'approved' THEN amount ELSE 0 END) AS approved_total_amount
FROM 
    Transactions
GROUP BY 
    TO_CHAR(trans_date, 'YYYY-MM'),
    country;




1070:
SELECT product_id, year AS first_year, quantity, price
FROM Sales
WHERE 
  (product_id, year) 
  IN (SELECT product_id, MIN(year) 
  FROM Sales GROUP BY 1)
