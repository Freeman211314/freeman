# 0-1背包问题


# [找零问题](https://leetcode-cn.com/problems/coin-change/submissions/)
> 给定不同面额的硬币 coins 和一个总金额 amount。编写一个函数来计算可以凑成总金额所需的最少的硬币个数。如果没有任何一种硬币组合能组成总金额，返回 -1。

头条面试的时候被问到过，也是我痛定思痛，开始注意算法的起因。
***  
1、 最值问题-> 动态规划
***转移方程式？***
> 分析: 金额i从硬币coins找零问题，每次金额coins找零有几种情况？金额j（0 ~ coins.length）找 1 与 不找 0，0与1问题。

dp[i] = dp[i] (不找金额coins[j]）
dp[i] = dp[i - coins[j]] + 1，找了金额coins[j]，那么总硬币数dp[i]，等于金额i-coins[j]时的总硬币数 + 1

