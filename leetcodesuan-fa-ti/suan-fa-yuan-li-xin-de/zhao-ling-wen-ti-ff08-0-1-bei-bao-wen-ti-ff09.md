# 0-1背包问题
[解答](https://www.cnblogs.com/xym4869/p/8513801.html)


# [找零问题](https://leetcode-cn.com/problems/coin-change/submissions/)
> 给定不同面额的硬币 coins 和一个总金额 amount。编写一个函数来计算可以凑成总金额所需的最少的硬币个数。如果没有任何一种硬币组合能组成总金额，返回 -1。

头条面试的时候被问到过，也是我痛定思痛，开始注意算法的起因。
***  
1、 最值问题-> 动态规划
***转移方程式？***
> 分析: 金额i从硬币coins找零问题，每次金额coins找零有几种情况？金额j（0 ~ coins.length）找 1 与 不找 0，0与1问题。

考虑该问题的最优子结构：设 c[i,j]表示 可用第 0，1，.... i 枚硬币 对 金额为 j 的钱 进行找钱 所需要的最少硬币数。
i 表示可用的硬币种类数， j 表示 需要找回的零钱

第 i 枚硬币有两种选择：用它来找零 和 不用它找零。因此，c[i,j]的最优解如下：
***c[i,j]= min{c[i-1,j] , c[i, j-coinsValues[i]] + 1}***   其中，
* c[i-1,j] 表示 不使用第 i 枚硬币找零时，对金额为 j 进行找钱所需要的最少硬币数
* c[i, j-coinsValues[i]] + 1 表示 使用 第 i 枚硬币找零时，对金额为 j 进行找钱所需要的最少硬币数。由于用了第 i 枚硬币，故使用的硬币数量要增1
c[i,j] 取二者的较小值的那一个。
```
public static int charge(int[] coinsValues, int n){
 8         int[][] c = new int[coinsValues.length + 1][n + 1];
 9         
10         //特殊情况1
11         for(int i = 0; i <= coinsValues.length; i++)
12             c[i][0] = 0;
13         for(int i = 0; i <= n; i++)
14             c[0][i] = Integer.MAX_VALUE;
15         
16         for(int j_money = 1; j_money <=n; j_money++)
17         {
18             
19             for(int i_coinKinds = 1; i_coinKinds <= coinsValues.length; i_coinKinds++)
20             {
21                 if(j_money < coinsValues[i_coinKinds-1])//特殊情况2，coinsValues数组下标是从0开始的,  c[][]数组下标是从1开始计算的
22                 {
23                     c[i_coinKinds][j_money] = c[i_coinKinds - 1][j_money];//只能使用 第 1...(i-1)枚中的硬币
24                     continue;
25                 }
26                 
27                 //每个问题的选择数目---选其中较小的
28                 if(c[i_coinKinds - 1][j_money] < (c[i_coinKinds][j_money - coinsValues[i_coinKinds-1]] +1))
29                     c[i_coinKinds][j_money] = c[i_coinKinds - 1][j_money];
30                 else
31                     c[i_coinKinds][j_money] = c[i_coinKinds][j_money - coinsValues[i_coinKinds-1]] +1;
32             }
33         }
34         return c[coinsValues.length][n];
35     }
```
参考：https://www.cnblogs.com/hapjin/p/5578852.html

2、组合出所有情况 -> 回溯法实现组合问题




