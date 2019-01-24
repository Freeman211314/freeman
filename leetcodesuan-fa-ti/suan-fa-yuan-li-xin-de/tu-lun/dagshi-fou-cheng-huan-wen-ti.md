# DAG
有向无环图

# 是否存在环
> 分析
解决这道题，我们首先要补充一下关于拓扑排序的知识。
将有向图中的顶点以线性方式进行排序。即对于任何连接自顶点u到顶点v的有向边uv，在最后的排序结果中，顶点u总是在顶点v的前面。
当有向图中存在环时，因为其中有互相依赖，导致无法决定谁前谁后，这时候这个有向图是无法被拓扑排序的。通过这种思想，我们只需要判断这个有向图是否可以被拓扑排序即可知道能否选取所有课程学习。

那么接下来看看拓扑排序的经典算法：

* 选择入度为0的节点输出
* 从有向图中删除此节点以及出边
* 循环上述过程，直到有向图中无节点或无入度为0的节点，循环结束
* 若循环结束后，如果有向图中无节点，那么说明可以拓扑排序；如果有向图中仍存在节点，那么说明存在环，即不可被拓扑排序。

这道题就采取上述思路，通过删除（同时记录）入度为0的节点，判断最后入度为0的节点的个数是否和总节点个数相同即可。
    
* [207. 课程表](https://leetcode-cn.com/problems/course-schedule/)
* [210. 课程表 II](https://leetcode-cn.com/problems/course-schedule-ii/)
```java
class Solution {
    //分析，图论
    //拓扑排序，入度为0的，优先被选择。
    public int[] findOrder(int numCourses, int[][] prerequisites) {
        //构造图,因为需要优化时间复杂度，所以将入度也表示出来
        int[] degree = new int[numCourses];
        Map<Integer,List<Integer>> graph = new HashMap();
        for(int i = 0;i< prerequisites.length;i++){
            int ru = prerequisites[i][0];//课程0
            int chu = prerequisites[i][1];//被需要的课程
            degree[ru]++;//入度数量,便于优化有序时间复杂度
            if(graph.containsKey(chu)){
               List<Integer> container = graph.get(chu); 
               container.add(ru);
            } else {
                List<Integer> container = new ArrayList();
                container.add(ru);
                graph.put(chu,container);
            }
        }
        //分析
        int[] result = new int[numCourses];
        int h = 0;
        for(int i = 0;i< degree.length;i++){
            for(int j = 0;j<degree.length;j++){
                if(degree[j] == 0){
                    if(graph.containsKey(j)){
                        List<Integer> ruList = graph.get(j);
                        for(int k =0 ;k< ruList.size();k++){
                            degree[ruList.get(k)] --;
                        }
                    }
                    result[h++] = j;
                    degree[j] --;
                }                
            }            
        }
        if(result.length > 1 && result[result.length - 1] == 0 && result[result.length - 2] == 0){
            return new int[]{};
        }
        return result;
        
    }
}
```


