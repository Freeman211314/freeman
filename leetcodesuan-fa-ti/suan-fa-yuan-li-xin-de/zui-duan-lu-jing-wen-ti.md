##最短路径
    * 加权
        * 松弛图
    * 无权
        * 广度优先遍历，先到end则直接返回。
###经典的 ***有向图加权最短路径问题***
1. Dijkstra算法
    * 初始化图（使用二维数组初始化一个图形，将权重作为数组的值）
    * 松弛 图，因为v1 -> v4 权重为100，但v1 -> v3 -> v4整体权重是50，那直接以50作为最终权重值。
        * 松弛图时，一定得从起点到最小的边开始，然后再找第二个小边。。。
    * 一轮后，起点到每个顶点的边，都是最小的。然后持续n轮。
    
[算法详解](https://blog.csdn.net/qq_35644234/article/details/60870719)
2. SPFA算法 
    

```java
    //计算剩余的顶点的最短路径（剩余this->vexnum-1个顶点）
    while (count != this->vexnum) {
        //temp用于保存当前dis数组中最小的那个下标
        //min记录的当前的最小值
        int temp=0;
        int min = INT_MAX;
        //找出到起点的最小边
        for (i = 0; i < this->vexnum; i++) {
            if (!dis[i].visit && dis[i].value<min) {
                min = dis[i].value;
                temp = i;
            }
        }

        //把temp对应的顶点加入到已经找到的最短路径的集合中
        dis[temp].visit = true;
        ++count;
        
        //因为不可达的，则是无穷。并且 1-3-4这种情况，会在运行4时，4+3的值 会覆盖出来。
        for (i = 0; i < this->vexnum; i++) {
            //注意这里的条件arc[temp][i]!=INT_MAX必须加，不然会出现溢出，从而造成程序异常
            if (!dis[i].visit && arc[temp][i]!=INT_MAX && (dis[temp].value + arc[temp][i]) < dis[i].value) {
                //如果新得到的边可以影响其他为访问的顶点，那就就更新它的最短路径和长度
                dis[i].value = dis[temp].value + arc[temp][i];
                dis[i].path = dis[temp].path + "-->v" + to_string(i + 1);
            }
        }
    }
```
***
###经典的 ***无向图最短路径问题***
[单词接龙](https://leetcode-cn.com/problems/word-ladder/)
其实解题思路，也是Dijkstra思想，只不过实现起来要简单，因为无向图，则构造图时，只需要关注半边，而且它只有存在不存在，则权重可以看为1，则就没必要松弛了。
