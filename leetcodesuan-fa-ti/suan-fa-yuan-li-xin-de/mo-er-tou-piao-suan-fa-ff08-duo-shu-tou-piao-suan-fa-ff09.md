# [229. 求众数 II](https://leetcode-cn.com/problems/majority-element-ii/comments/)

> 要求算法的时间复杂度为 O(n)，空间复杂度为 O(1)。

解题思路：
1、 暴力破解
2、 运用空间容器，将时间复杂度降低
但上述两种常用思维，并不能保证时间复杂度 和 空间复杂度最低。 

分析：因为超过n/3的众数，所以毫无疑问众数最多2组。且这两组数，个数一定比其他的总个数多（绝对优势多），那么自然联想到多数投票算法（类似于zk选择算法，都先投自己，如果支持你的人到0个了，那么就换人支持（因为众数，支持的人是最多的））。但是不是支持的人是超过n/3的，还需要一遍循环验证下。  

```java
def majorityElement(self, nums):
        """
        :type nums: List[int]
        :rtype: List[int]
        """
        res1,res2=0,0
        num1,num2=0,0
        for num in nums:
            //如果相等，则候选人获得一票支持
            if num==res1:
                num1+=1
                continue
            if res2==num:
                num2+=1
                continue
            //如果没候选人，则投自己    
            if num1==0:
                res1=num
                num1+=1
                continue
            if num2==0:
                res2=num
                num2+=1
                continue
                
            num2-=1
            num1-=1
        res=[]
        num1,num2=0,0
        for num in nums:
            if num==res1:
                num1+=1
            elif num==res2:
                num2+=1
        threshold=len(nums)//3
        if num1>threshold:
            res.append(res1)
        if num2>threshold and res1!=res2:
            res.append(res2)
        return res
```