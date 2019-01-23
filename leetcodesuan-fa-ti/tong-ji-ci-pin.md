# [统计词频](https://leetcode-cn.com/problems/word-frequency/submissions/)

* 可以参照spark经典思路  
* unix pipes，即unix管道，也就是俗称的shell脚本  

awk命令，常用语文本分析。  

```
awk '{for(i=1;i<=NF;i++){res[$i]+=1}}END{for(k in res){print k" "res[k]} }' words.txt | sort -nr -k2
```

1、 awk对每行文本进行分隔处理(默认空格分隔)，然后对每行进行后面代码处理。  
2、 分隔后的字符，如果是一样的，则会在同一个$i中，所以这个会一直增加。  
3、 利用这个，可以进行累加  


sort 命令，进行对数值进行排序(-nr)，对数值(-k2)
***
其中：
awk 是文本分析工具，经常用于统计、处理  

sed 文本流编辑工具，经常用于打印特定的行等。如：[打印第10行](https://leetcode-cn.com/problems/tenth-line/) ，答案为：sed -n '2p' file.txt  

sort 排序工具  