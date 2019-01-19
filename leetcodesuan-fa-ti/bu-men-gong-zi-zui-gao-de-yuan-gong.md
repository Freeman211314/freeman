# [184. 部门工资最高的员工](https://leetcode-cn.com/problems/department-highest-salary/)

> select d.Name as Department,e.name as Employee,e.Salary as Salary 
from Employee e
left join Department d
on e.DepartmentId = d.Id
group by e.DepartmentId
having e.Salary = MAX(Salary)

坑点：having中***MAX函数是返回group by后记录中最大值，而不是分组前每组的最大值***。

这种求每组中最大值问题，应该先排序，因为***group by后返回的是第一条记录***
> select dName as Department,e.name as Employee,e.Salary as Salary 
from (
    select a.Id,a.Name,Salary,a.DepartmentId, d.name as dName
from Employee a
left join Department d
on a.DepartmentId = d.Id
order by a.Salary desc
    ) as e
group by e.DepartmentId