# [打家劫舍](https://leetcode-cn.com/problems/house-robber/comments/)
经典算法题
> 你是一个专业的小偷，计划偷窃沿街的房屋。每间房内都藏有一定的现金，影响你偷窃的唯一制约因素就是相邻的房屋装有相互连通的防盗系统，如果两间相邻的房屋在同一晚上被小偷闯入，系统会自动报警。
给定一个代表每个房屋存放金额的非负整数数组，计算你在不触动警报装置的情况下，能够偷窃到的最高金额。

数组中，隔开取值，求最大值？
* 分析一：与之前组合问题很想，首先引入思维的是回溯法
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