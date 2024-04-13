*`AVL trees`, a type of `self-balancing binary search tree`, find applications in various scenarios due to their ability to maintain balance automatically. Here are some key use cases of `AVL trees`. `AVL` stands for `Adelson - Velskii - Landis`*
- **Efficient Indexing**
- **In-Memory Collections**
- **Optimized Search**
- **Database Application**

**ALGORITHM**

*The algorithmic implementation of `AVL Tree`.*
![[AVL1.jpg]]

*There are four possible movement can be happen in the Tree, they are*
- Left- Left case
- Left - Right case
- Right - Right case
- Right - Left case

**The Condition to match any of these cases**

![[AVL2.jpg]]

**There are only two type of Rotation. they are,**

![[AVL3.jpg]]

*Let's Implement this as Code.*

path  -> [D:\Study\1.programming material\NO.1 Priority\Java + DSA\codeOOP\src\Tree]

```java
package Tree;  
  
import java.util.Collections;  
  
class Node  
{  
    int data;  
    Node left;  
    Node right;  
    int height;  
    
    public Node(int data) {  
        this.data = data;  
        height=1;  
    }  
}  
public class AVL {  
    private Node root;  
    
    private void Insert(int data)  
    {  
        root=insert(root,data);  
    }  
    
    private Node insert(Node node, int data) {  
        if (node == null) {  
            node=new Node(data);  
            return node;  
        }  
        if (node.data < data)  
            node.right=insert(node.right,data);  
        if (node.data > data)  
            node.left=insert(node.left,data);  
        node.height=1+Math.max(Height(node.left), Height(node.right));  
        return Rotate(node);  
    }  
    private Node Rotate(Node node) {  
        //left heavy  
        if(Height(node.left) - Height(node.right) > 1)  
        {  
            //left - left case  
            // in this case the child node left tree's height higher than it's right tree's height.          
            if(Height(node.left.left) - Height(node.left.right) > 0)  
                return RightRotate(node);  
            //left - right case  
            if(Height(node.left.left) - Height(node.left.right) < 0)  
            {  
                node.left=LeftRotate(node.left);  
                return RightRotate(node);  
            }  
        }  
        // right heavy  
        if(Height(node.left) - Height(node.right) < -1)  
        {  
            //right - right case  
            if(Height(node.right.left) - Height(node.right.right) < 0)  
                return LeftRotate(node);  
            //right - left case  
            if(Height(node.right.left) - Height(node.right.right) > 0)  
            {  
                node.right=RightRotate(node.right);  
                return LeftRotate(node);  
            }  
        }  
        return node;  
    }  
    
    private Node RightRotate(Node p) {  
        Node c = p.left;  
        Node t = c.right;  
        
        c.right=p;  
        p.left=t;  
        
        p.height=Math.max(Height(p.left),Height(p.right)+1);  
        c.height=Math.max(Height(c.left),Height(c.right)+1);  
        
        return c;  
    }  
    
    private Node LeftRotate(Node c) {  
        Node p= c.right;  
        Node t= p.left;  
        
        p.left=c;  
        c.right=t;  
        
        p.height=Math.max(Height(p.left),Height(p.right)+1);  
        c.height=Math.max(Height(c.left),Height(c.right)+1);  
        
        return p;  
    }  
    
    public void Populate(int[] x)  
    {  
        for (int j : x) {  
            Insert(j);  
        }  
    }  
    
    public void Display()  
    {  
        display(root,0);  
    }  
    
    private void display(Node node, int level) {  
        if (node == null)  
            return;  
            
        System.out.println(String.join(" ", Collections.nCopies(level*3," "))+node.data);  
        
        display(node.left,level+1);  
        
        display(node.right,level+1);  
    }  
    
    public int height() {  
        return Height(root);  
    }  
    private int Height(Node node)  
    {  
        if(node == null)  
            return -1;  
        return node.height;  
    }  
    
    public Boolean Balanced()  
    {  
        return balanced(root);  
    }  
    
    private boolean balanced(Node node) {  
        if(node == null)  
            return true;  
            
        return Math.abs(Height(node.left) - Height(node.right)) <=1 && balanced(node.left) && balanced(node.right);  
    }  
}
```

```java
package Tree;

import Tree.AVL.AVL;

public class Main {
    public static void main(String[] args) {
        AVL obj = new AVL();

        int[] Array = new int[500];
        for (int i = 0; i < 500; i++) {
            Array[i] = i + 1;
        }
        obj.Populate(Array);
        obj.Display();

        System.out.println(obj.height());
        System.out.println(obj.Balanced());
    }
}
```

**That it, this Custom `AVL Tree`**

*`Inbuild AVL` tree in `java` is `TreeMap`.Let's Implement as a `Code`*

```java
import java.util.TreeMap;

public class AVLTreeExample {

    public static void main(String[] args) {
        // Create a new TreeMap, which is an implementation of an AVL tree in Java
        TreeMap<Integer, String> treeMap = new TreeMap<>();

        // Add some elements to the tree
        treeMap.put(1, "One");
        treeMap.put(2, "Two");
        treeMap.put(3, "Three");

        // Print the elements of the tree in order
        for (Integer key : treeMap.keySet()) {
            System.out.println(key + " : " + treeMap.get(key));
        }
    }
}
```