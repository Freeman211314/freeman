KaraTsuba乘法。普通乘法复杂度一般都是O(n^2)，而这个算法，仅有O(nlog3)。下面，我就来介绍一下这个算法。
        首先来看看这个算法是怎么进行计算的，见下图：
        ![avatar](http://baidu.com/pic/doge.png)
![avatar](https://img-blog.csdn.net/20160910133150980?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

接下来，就来证明一下这个算法的正确性。

我们假设要相乘的两个数是x * y。我们可以把x，y写成:
x * y = (a * 10^(n/2) + b) * (c * 10^(n/2) + d)

这里的n是数字的位数。如果是偶数，则a和b都是n / 2位的。如果n是奇数，则你可以让a是n / 2 + 1位，b是n / 2位。（例如a = 12，b = 34；a = 123，b = 45）

进一步计算，

x * y = a*c*10^n + (a + b + c + d)* 10^n/2 + bd

对比之前的计算过程。结果已经呼之欲出了这里唯一需要注意的两点就是
1. (a * d + b * c)的计算为了防止两次乘法，应该使用之前的计算
2. 这些乘法在算法里应该是***递归实现的***，数字很大时，先拆分，然后拆分出来的数字还是很大的话，就继续拆分，直到a * b已经是一个非常简单的小问题为之。这也是分治的思想。

摘抄引用：
[KaraTsuba乘法——高效的大数乘法](https://blog.csdn.net/sunnylinner/article/details/52592496)