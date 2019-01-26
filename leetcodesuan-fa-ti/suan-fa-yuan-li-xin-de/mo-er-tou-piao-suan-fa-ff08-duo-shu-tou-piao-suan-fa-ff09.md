# [229. 求众数 II](https://leetcode-cn.com/problems/majority-element-ii/comments/)

> 要求算法的时间复杂度为 O(n)，空间复杂度为 O(1)。

解题思路：
1、 暴力破解
2、 运用空间容器，将时间复杂度降低
但上述两种常用思维，并不能保证时间复杂度 和 空间复杂度最低。
分析：因为超过n/3的众数，所以毫无疑问众数最多2组。