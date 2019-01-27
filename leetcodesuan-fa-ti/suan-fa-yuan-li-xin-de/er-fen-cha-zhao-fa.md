# [278. 第一个错误的版本](https://leetcode-cn.com/problems/first-bad-version/submissions/)

在初次分析中发现就是在有序集中查找一个数。

我常写的二分查找法如下：

```
public int firstBadVersion(int n) {
        //查找  -->二分查找法
        int begin = 1;
        int end = n;        
        while(begin < end){
            int middle = (begin + end) >> 1;
            if(isBadVersion(middle)){
                end = middle - 1;
            } else {
                begin = middle +1;
            }
        }
        return begin;
}

```
发现会统计错误，因为比如123中2是第一个错误版本，end = middle - 1后直接等于1了，造成在1，1中继续查找，最后返回结果1.
那么可能会陷入(***不进肯定是错误的，因为如果不进的话，会造成最后相临的两个数最后永远等于前者，死循环了。***

```
            if(isBadVersion(middle)){
                end = middle;
            } else {
                begin = middle;
            }
```
但是这道题目当middle是true时，那么前者可能是true，也可能正好是false(那么当前middle即为所求），所以在此处不-1.
所以综合分析得出:（）


```
    if(isBadVersion(middle)){
                end = middle ;
            } else {
                begin = middle +1;
    }

```



