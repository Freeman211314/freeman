# 空间换时间
经常出现算法优化：时间复杂度较为长，怎么优化呢？
一是方法上优化
二是空间换时间
[205. 同构字符串](https://leetcode-cn.com/problems/isomorphic-strings/)
```java
for(int i =0;i<first.length;i++){
            for(int j = i + 1;j<first.length;j++){
                if(first[i] == first[j]){
                    if(second[i] != second[j]){
                        return false;
                    }
                } else {
                    if(second[i] == second[j]){
                        return false;
                    }
                }
            }
        }
        ```

