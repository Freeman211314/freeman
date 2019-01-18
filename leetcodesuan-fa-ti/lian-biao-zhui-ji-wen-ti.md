#链表追击问题
链表追击问题，经常用于 求某个节点

[160. 相交链表](https://leetcode-cn.com/problems/intersection-of-two-linked-lists/)
[142. 环形链表 II](https://leetcode-cn.com/problems/linked-list-cycle-ii/)

等等，都是求某个节点，当然这部分内容，最通用的方案，就是将节点存于map容器中，通过容器辅助求解。

O(1)的空间复杂度：
### 结题思路
一般追击问题，都是在路程上进行分析，通过两次以上的轮询得到 所需节点的节点。