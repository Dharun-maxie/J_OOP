*`Heaps` are `data structures` used for efficient access to the maximum or minimum element in a `collection`. They're commonly used in `priority queues` for tasks like scheduling events or implementing `algorithms` like `Dijkstra's`. Additionally, `heapsort` leverages `heaps` for sorting. They're also utilized in memory allocation and `graph algorithms` like `Prim's` and `Kruskal's`.*

Min & Max Heap
1. **Time Complexity**:
   - Insertion (adding a new element): O(log n)
   - Deletion (removing the root element): O(log n)
   - Finding the minimum/maximum element: O(1)

2. **Space Complexity**:
   - O(n) for both min-heap and max-heap, where n is the number of elements in the heap.

*Let's Code Heap class.*

```java
package Tree.Heaps;  
  
import java.util.ArrayList;  
  
  
class Heap<T extends Comparable<T>> {  
    ArrayList<T> root;  
    Heap()  
    {  
        root=new ArrayList<>();  
    }  
    // up-heap  
    public int parent(int index){  
        return (index-1)/2;  
    }  
    // down-heap  
    public int left(int index){  
        return index * 2 + 1;  
    }  
    public int right(int index){  
        return index * 2 + 2 ;  
    }  
  
    public void Insert(T V)  
    {  
        root.add(V);  
        upheap(root.size() - 1);  
    }  
  
    public void Insert(T[] V)  
    {  
        for(T i : V) {  
            root.add(i);  
            upheap(root.size() - 1);  
        }  
    }  
    private void upheap(int index)  
    {  
        if(index == 0)  
            return;  
        int parent=parent(index);  
        if(root.get(index).compareTo(root.get(parent)) < 0){  
            swap(index,parent);  
            upheap(parent);  
        }  
    }  
    public T Min()  
    {  
        return root.getFirst();  
    }  
    private T remove() throws Exception {  
        if (root.isEmpty())  
            throw new Exception(" : List Empty Can't remove");  
  
        T minElement = root.get(0);  
  
        T lastElement = root.remove(root.size()-1);  
        if (!root.isEmpty()){  
            root.set(0,lastElement);  
            downheap(0);  
        }  
        return minElement;  
    }  
    private void downheap(int index)  
    {  
        int min=index;  
        int left = left(index);  
        int right = right(index);  
  
        if(left < root.size() && root.get(min).compareTo(root.get(left)) > 0)  
            min=left;  
        if(right < root.size() && root.get(min).compareTo(root.get(right)) > 0)  
            min=right;  
        if(min != index) {  
            swap(min, index);  
            downheap(min);  
        }  
    }  
  
    public ArrayList<T> HeapSort()throws Exception  
    {  
        ArrayList<T> list=new ArrayList<>();  
  
        while(!root.isEmpty()) {  
            list.add(this.remove());  
        }  
        return list;  
    }  
  
    private void swap(int x,int y)  
    {  
        T temp=root.get(x);  
        root.set(x,root.get(y));  
        root.set(y,temp);  
    }  
}
```

*Let's Code Main class.*

```java
package Tree.Heaps;  
  
import java.util.ArrayList;  
  
public class Main {  
    public static void main(String[] args) throws Exception {  
        Integer[] arr = {9, 8, 3, 6, 5, 12, 14, 7, 2, 1, 10, 11, 15, 4, 13};  
          
//  String[] arr = {"b","d","m","v","f","z","u","h","o","r","a"};  

        Heap<Integer> obj =new Heap<>();  
        
        obj.Insert(arr);  
        
        ArrayList list = obj.HeapSort();  
        
        System.out.println(list);  
    }  
}
```

That's it.