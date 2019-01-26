[231. 2的幂](https://leetcode-cn.com/problems/power-of-two/)

>  分析:
如果是2的幂，那么必须为正数。他们共性是010000……这种类型的，符号位为0，其他位置只有一个1。

```java
class Solution {
    public boolean isPowerOfTwo(int n) {
        // 暴力破解，递归
        // 与运算符
        if(n < 0){
            return false;
        }
        int num = 0;
        for(int i=0;i<32;i++){
            // 正数的补码是其本身，负数的补码 符号位 + 补码表示
            if(num > 1 || n == 0){
                break;
            }
            if((n & 0x00000001) == 1){
                num ++;
            }
            n >>>= 1;
        }
        return num == 1 ? true : false;
    }
}
```
我上面，判断一个int型非符号位只有一个1判断方法：
1、 我是每个位置都拎出来，然后判断。
