##最短路径
###经典的 ***有向图加权最短路径问题***
1. Dijkstra算法
    * 初始化图（使用二维数组初始化一个图形，将权重作为数组的值）
    * 松弛 图，因为v1 -> v4 权重为100，但v1 -> v3 -> v4整体权重是50，那直接以50作为最终权重值。
        * 松弛图时，一定得从起点到最小的边开始，然后再找第二个小边。。。
    * 一轮后，起点到每个顶点的边，都是最小的。然后持续n轮。
2. SPFA算法
    
[算法详解](https://blog.csdn.net/qq_35644234/article/details/60870719)




```python
void Graph_DG::Dijkstra(int begin){
    //首先初始化我们的dis数组
    int i;
    for (i = 0; i < this->vexnum; i++) {
        //设置当前的路径
        dis[i].path = "v" + to_string(begin) + "-->v" + to_string(i + 1);
        dis[i].value = arc[begin - 1][i];
    }
    //设置起点的到起点的路径为0
    dis[begin - 1].value = 0;
    dis[begin - 1].visit = true;

    int count = 1;
    //计算剩余的顶点的最短路径（剩余this->vexnum-1个顶点）
    while (count != this->vexnum) {
        //temp用于保存当前dis数组中最小的那个下标
        //min记录的当前的最小值
        int temp=0;
        int min = INT_MAX;
        for (i = 0; i < this->vexnum; i++) {
            if (!dis[i].visit && dis[i].value<min) {
                min = dis[i].value;
                temp = i;
            }
        }
        //cout << temp + 1 << "  "<<min << endl;
        //把temp对应的顶点加入到已经找到的最短路径的集合中
        dis[temp].visit = true;
        ++count;
        for (i = 0; i < this->vexnum; i++) {
            //注意这里的条件arc[temp][i]!=INT_MAX必须加，不然会出现溢出，从而造成程序异常
            if (!dis[i].visit && arc[temp][i]!=INT_MAX && (dis[temp].value + arc[temp][i]) < dis[i].value) {
                //如果新得到的边可以影响其他为访问的顶点，那就就更新它的最短路径和长度
                dis[i].value = dis[temp].value + arc[temp][i];
                dis[i].path = dis[temp].path + "-->v" + to_string(i + 1);
            }
        }
    }

}
--------------------- 
作者：Ouyang_Lianjun 
来源：CSDN 
原文：https://blog.csdn.net/qq_35644234/article/details/60870719 
版权声明：本文为博主原创文章，转载请附上博文链接！
```
***
###经典的 ***无向图最短路径问题***
[单词接龙](https://leetcode-cn.com/problems/word-ladder/)
其实解题思路，也是Dijkstra思想，只不过实现起来要简单，因为无向图，则构造图时，只需要关注半边，而且它只有存在不存在，则权重可以看为1，则就没必要松弛了。
