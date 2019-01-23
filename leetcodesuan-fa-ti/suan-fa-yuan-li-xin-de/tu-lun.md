# 有向图

# 无向图
***

常见算法：
1、 求[最短路径问题](leetcodesuan-fa-ti/suan-fa-yuan-li-xin-de/zui-duan-lu-jing-wen-ti.md)  
2、 DAG（有向无环图）求证是否无环问题 [https://leetcode-cn.com/problems/course-schedule/](https://leetcode-cn.com/problems/course-schedule/)

验证是否有环:  
分为3步：
    * 构建图
    * 缩减出度为0的节点，直到最后
    * 所有的出度是否都为0，如果是则无环，否则则有环。
