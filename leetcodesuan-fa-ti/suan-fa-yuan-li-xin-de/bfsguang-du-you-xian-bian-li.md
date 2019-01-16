##广度优先遍历
详情略，但经典使用场景是
1.[***树的层次遍历***](https://leetcode-cn.com/problems/populating-next-right-pointers-in-each-node-ii)
2.图轮（包含无向图 和 有向图）
***
###树的层次遍历
结题技巧：
1. 队列辅助容器，需要标注层级
    * 可以采用头结点 + 1作为参数传递来得到层级
    
2.双向队列方式
3.