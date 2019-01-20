# [统计词频](https://leetcode-cn.com/problems/word-frequency/submissions/)

* 可以参照spark经典思路
* unix pipes，即unix管道，也就是俗称的shell脚本

awk命令，常用语文本分析。

```python 
awk '{for(i=1;i<=NF;i++){res[$i]+=1}}END{for(k in res){print k" "res[k]} }' words.txt | sort -nr -k2