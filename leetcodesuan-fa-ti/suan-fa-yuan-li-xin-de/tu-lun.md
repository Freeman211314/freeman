# 有向图

# 无向图
***

常见算法：
1、 求[最短路径问题](zui-duan-lu-jing-wen-ti.md)  
2、 DAG（有向无环图）求证是否无环问题 [207. 课程表](https://leetcode-cn.com/problems/course-schedule/)

验证是否有环:  
分为3步：
    * 构建图
    * 缩减出度为0的节点，直到最后
    * 所有的出度是否都为0，如果是则无环，否则则有环。
    
    
附:
[图的几种表示法](https://blog.csdn.net/woaidapaopao/article/details/51732947)
