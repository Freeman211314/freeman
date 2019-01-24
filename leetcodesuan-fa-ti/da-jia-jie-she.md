# [打家劫舍](https://leetcode-cn.com/problems/house-robber/comments/)
***
[213. 打家劫舍 II](https://leetcode-cn.com/problems/house-robber-ii/comments/)
这道有环的问题，我理解错意思：并不是它可以回到原点又重新开始偷，所以只需要money[n] = Math.max(rob(nums, 0, n-2), rob(nums, 1, n-1),而单独money[n-2]和money[n-1]还是按照原先的*** 动态规划***求解。

经典算法题
> 你是一个专业的小偷，计划偷窃沿街的房屋。每间房内都藏有一定的现金，影响你偷窃的唯一制约因素就是相邻的房屋装有相互连通的防盗系统，如果两间相邻的房屋在同一晚上被小偷闯入，系统会自动报警。
给定一个代表每个房屋存放金额的非负整数数组，计算你在不触动警报装置的情况下，能够偷窃到的最高金额。

数组中，隔开取值，求最大值？
* 分析一：与之前组合问题很想，首先引入思维的是*** 回溯法***
最大值，毫无疑问，是第i个数，存不存在？如果存在，则是第i+2后数组再重新组合的再结果。
```java
private void helper(int[] nums,int begin,int sum){
        if(begin >= nums.length){
            if(result.compareTo(sum) < 0){
                result = sum;
            }
            return ;
        }
        if(begin >= nums.length-1){
            if(result.compareTo(sum + nums[begin]) < 0 ){
                result = sum + nums[begin];
            }
            return ;
        }
        
        for(int i = begin; i < nums.length; i++){
            helper(nums,i + 2, sum + nums[i]);
        }
    }
```
最后发现超出时间限制。
回溯法的弊端，每次递归内部都做了大量重复计算。

* 分析二：*** 记忆化搜索***
因为回溯法造成大量重复取用计算num[i]的值，那我可以将
```java
/**
     * memo[i] 表示考虑抢劫 nums[i...n] 所能获得的最大收益
     */
    private int[] memo;

    /**
     * 方式一：记忆化搜索
     * ① 状态：考虑抢劫 nums[index...num.length） 这个范围内的所有房子
     * ② 状态转移：tryRob(n) = Max{rob(0) + tryRob(2), rob(1) + tryRob(3)... rob(n-3) + tryRob(n-1), rob(n-2), rob(n-1)}
     *
     * @param nums
     * @return
     */
    public int rob1(int[] nums) {
        memo = new int[nums.length];
        Arrays.fill(memo, -1);
        return tryRob(nums, 0);
    }

    private int tryRob(int[] nums, int index) {
        if (index >= nums.length) {
            return 0;
        }
        // 记忆化搜索可以避免重叠子问题的重复运算
        if (memo[index] != -1) {
            return memo[index];
        }
        // 下面是对状态转移方程的描述
        int res = 0;
        for (int i = index; i < nums.length; i++) {
            res = Math.max(res, nums[i] + tryRob(nums, i + 2));
        }
        memo[index] = res;
        return res;
    }
```
* *** 动态规划***，每次取用都会影响后续的结果，那么就不能采用贪心算法。这种问题就必须采用动态规划。
动态规划：找递推式
 memo[i] 表示考虑抢劫 nums[i...n-1] 所能获得最大收益（不是说一定从 i 开始抢劫）
memo[i] = Max(nums[i]+ memo[i+2],nums[i+1] + memo[i+3)
这种递推式出来了。
```java
//money[i] = Max(num[i-2] + money[i], money[i-1]);
    public int rob(int[] nums){
        int[] money = new int[nums.length];
        for(int i = 0;i< money.length ;i++){
            if(i == 0){
                money[i] = nums[i];
                continue;
            }
            if(i == 1){
                money[i] = Math.max(nums[i-1],nums[i]);
                continue;
            } 
            money[i] = Math.max(money[i-2] + nums[i],money[i-1]);
        }
        return nums.length > 0 ? money[nums.length - 1] : 0;
    }
```