\#股票买卖问题

\#\#\[只能有一次交易过程\]\([Best Time to Buy and Sell Stock](https://leetcode-cn.com/problems/best-time-to-buy-and-sell-stock)\)

\#\#\[不限制交易次数\]\([Best Time to Buy and Sell Stock II](https://leetcode-cn.com/problems/best-time-to-buy-and-sell-stock-ii)\)

\#\#心得

\#\#\#动态规划

只有一次交易过程，那么分析过程：只有一次交易，那么第i天交易的最大利润则为之前最大利润 或者 当天交易减历史最小值，取最小值，递推式如下：

P\[i\] = max\(P\[i-1, a\[i\] - min\(a\[i-1\]\) 

P\[i\]表示第i天买卖的最大利润

a\[i\]表示第i天的买卖价格

从这里可以得出，当只有一次交易时，考虑**整体最优解**

\#\#\#贪心算法

不限制交易次数，则为典型的贪心算法，因为整体次数不受限制，每次交易都不会影响整体的因素，则求最大利润的话，每次都最大利润，那么整体肯定最大

所以这种贪心算法，就是每次都求得最大的利润 **局部最优解** ，就是求上升空间



