动态规划总结：

1. 最优递推子结构
2. 基准值

案例分析：

1、 找零问题，最优解，最少的硬币数  [http://www.cnblogs.com/hapjin/p/5578852.html](http://www.cnblogs.com/hapjin/p/5578852.html)

c\[i,j\]表示从coinValues数组中第0......到i个值，对应的找数值i的最少硬币数

持续分析，得出c\[i,j\] = min{c\[i-1,j\] , c\[i, j - coinValues\[i\]\] + 1} （说白了就是面值为coinValues\[i\] 的硬币用 或 不用）

2、 找零问题，多少种找零方案 [https://www.cnblogs.com/hapjin/p/5579737.html](https://www.cnblogs.com/hapjin/p/5579737.html)

最优子结构：c\[i,j\] = c\[i-1,j\]  +  c\[i, j - coinValues\[i\]\] （明显组合原理中加法实现）

3、 打家劫舍问题

---

慢慢的你会发现，动态规划，其实就是用最优子结构，一步步递推出基准值的情况，然后得到最优解。

所以你一开始会很难理解c\[i,j\]情况。为什么需要这样定义，但反过来想，就是为了剔除掉第i +1面值时带来的复杂问题，使用迭代思想，将问题简单化

