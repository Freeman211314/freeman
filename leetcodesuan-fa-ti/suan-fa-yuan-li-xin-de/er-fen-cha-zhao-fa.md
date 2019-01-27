# [278. 第一个错误的版本](https://leetcode-cn.com/problems/first-bad-version/submissions/)

在初次分析中发现就是在有序集中查找一个数。

我常写的二分查找法如下：
```java
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