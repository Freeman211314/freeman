# [184. 部门工资最高的员工](https://leetcode-cn.com/problems/department-highest-salary/)

> select d.Name as Department,e.name as Employee,e.Salary as Salary 
from Employee e
left join Department d
on e.DepartmentId = d.Id
group by e.DepartmentId
having e.Salary = MAX(Salary)

坑点：having中***MAX函数是返回是分组前每组的最大值,此类聚合函数都是在group by中返回每组***。
select Min(id)
from Person
group by Email

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

原先一直以为，先order by,然后再 group by就能成功？？***现在看group by只关注于物理表中数据,而不是子表(视图）中的数据***
因为order by是返回第一条记录。