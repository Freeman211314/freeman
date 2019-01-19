# [184. 部门工资最高的员工](https://leetcode-cn.com/problems/department-highest-salary/)

```java
select d.Name as Department,e.name as Employee,e.Salary as Salary 
from Employee e
left join Department d
on e.DepartmentId = d.Id
group by e.DepartmentId
having e.Salary = MAX(Salary)

坑点：having中MAX函数是返回group by后记录中最大值，而不是分组前每组的最大值。