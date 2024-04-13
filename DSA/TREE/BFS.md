
*`BFS` Stands for Breadth First Search. This Search Method Goes by the Breadth of the tree.*


*Let's Implement `BFS` as a `Code`.*

```java
public static List<List<Integer>> BFS(Node node) {  
    List<List<Integer>> list=new ArrayList<>();  
    
    Queue<Node> queue = new LinkedList<>();  
    queue.offer(node);  
    while(!queue.isEmpty())  
    {  
        List<Integer> CurrentList=new ArrayList<>();  
        int size=queue.size();  
        for (int i = 0; i < size; i++) {  
            Node CurrenNode=queue.poll();  
            if(CurrenNode != null) {  
                CurrentList.add(CurrenNode.data);  
                if (node.left != null) {  
                    queue.add(CurrenNode.left);  
                }  
                if (node.right != null) {  
                    queue.add(CurrenNode.right);  
                }  
            }  
        }  
        if (!CurrentList.isEmpty())  
            list.add(CurrentList);  
    }  
    return list;  
}
```

