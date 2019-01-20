# [统计词频](https://leetcode-cn.com/problems/word-frequency/submissions/)

* 可以参照spark经典思路
* unix pipes，即unix管道，也就是俗称的shell脚本

awk命令，常用语文本分析。

```
awk '{for(i=1;i<=NF;i++){res[$i]+=1}}END{for(k in res){print k" "res[k]} }' words.txt | sort -nr -k2
```
1、 awk对每行文本进行分隔处理(默认空格分隔)，然后对每行进行后面代码处理。
2、 分隔后的字符，如果