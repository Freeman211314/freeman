# [279. 完全平方数](https://leetcode-cn.com/problems/perfect-squares/)

> 1、给定正整数 n，找到若干个完全平方数（比如 1, 4, 9, 16, ...）
2、 组成和的完全平方数的个数最少

答题：
1、 动态规划分析（最简单，但递推式分析不明显）
首先，个数最少问题，明显最优解问题。那么考量 和为i的个数dp[i]依赖于什么？  
依赖于前一个j*j的个数 + 余数的个数
公式: dp[i] = min(dp[i], dp[j] + dp[i - j]，其中j是一个数的平方，那么究竟是哪个数的平方呢？这个可能是需要遍历的。  
很明显，惯性思路是先去j最大的情况，然后再用余数处理，而通过动态规划分析，利用等式，将最优解转换为dp[j] + dp[i - j]的情况。

2、常规思路，是先取j最大的情况，然后再取第二大的情况，最后得到n=0时，个数最小的值。
这种常规思路，实现方式，采用BFS。

3、数学公式方法。
这个就需要多刷题，见过才能知道了。