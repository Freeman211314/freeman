#链表追击问题
链表追击问题，经常用于 求某个节点

[160. 相交链表](https://leetcode-cn.com/problems/intersection-of-two-linked-lists/)
[142. 环形链表 II](https://leetcode-cn.com/problems/linked-list-cycle-ii/)
[287. 寻找重复数](https://leetcode-cn.com/problems/find-the-duplicate-number/submissions/)

等等，都是求某个节点，当然这部分内容，最通用的方案，就是将节点存于map容器中，通过容器辅助求解。

287. 寻找重复数 这道题很精髓，看起来只是查找重复数，但必须在O(1)空间复杂度，小于O(n^2）时间复杂度情况下进行，所以将其转换为

O(1)的空间复杂度：
### 结题思路
一般追击问题，都是在路程上进行分析，通过两次以上的轮询得到 所需节点的节点。