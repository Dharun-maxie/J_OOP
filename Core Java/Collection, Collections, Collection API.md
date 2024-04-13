- *Collection -> Interface*
- *Collections -> class*
- *Collection Frameworks (or) Collection API -> Concept*

![[Pasted image 20240317093550.png]]

*Lets Implement some this,*

```java
import java.util.Collection;
import java.util.HashSet;
import java.util.ArrayList;
import java.util.TreeSet;

class Threads.Main
{
	public static void main(String[] args)
	{
		Collection<Integer> list1 = new ArrayList<>();  // -> List
		Collection<Integer> list2 = new HashSet<>();    // -> Set
		Collection<Integer> list3 = new TreeSet<>();    // -> Set
	}
}
```

*`ArrayList`  Allows duplicate value and Unsorted but `HashSet` is Unsorted but No Duplicate in the Other hand `TreeSet` is Sorted and No Duplicate. And We have to use it respective `parent class` for implementation. Because the `Collection Interface` does not have `Indexing` method. but `List` do.*

**The `Collection Framework` has `Parent class` which is `Iterable`.**

![[Pasted image 20240317102221.png]]

**ok Lets implement it.**

```java
List<Integer> list1 = new ArrayList<>();  // -> List  
Set<Integer> list2 = new HashSet<>();     // -> Set  
Set<Integer> list3 = new TreeSet<>();     // -> Set  
  
for (int i = 1; i <= 10; i++) {  
    list1.add((int) (i*(Math.random() * 10)));  
    list2.add((int) (i*(Math.random() * 10)));  
    list3.add((int) (i*(Math.random() * 10)));  
}

Iterator<Integer> l1 = list1.iterator();  
Iterator<Integer> l2 = list2.iterator();  
Iterator<Integer> l3 = list3.iterator();  
  
while(l1.hasNext())  
{  
    System.out.print(l1.next()+ " ");  
}  
System.out.println();  
while(l2.hasNext())  
{  
    System.out.print(l2.next()+ " ");  
}  
System.out.println();  
while(l3.hasNext())  
{  
    System.out.print(l3.next()+ " ");  
}
```

**The Output Will be Random value.**

```java
3 16 28 36 0 30 32 20 78 5 
48 17 2 38 23 10 11 91 76 
3 7 9 13 18 40 57 69 82 88
```

*And We also have `Map` which is not a part of `Collection`. Lets do implementation for that.*

```java
// Syntax
Map<K, V> map =new HashMap<>();
```

```java
import java.util.Map;
import java.util.HashMap;
class Threads.Main
{
	public static void main(String[] args)
	{
		Map<Integer, Integer> map =new HashMap<>();
		for (int i = 1; i <= 10; i++) {  
		    map.put(i,(int) (i*(Math.random() * 10))); 
		}
		for(int i : map.keySet())
		{
			System.out.println("Key : "+ i +" "+"Value : "+ map.get(i));
		}
	}
}
// output 
```

#VeryImportantNote 
**When we need use `Map` for `Threads` we can use `HashTable`**



# Collections

#Sorting **Collection Sorting**

```java
import java.util.ArrayList;  
import java.util.Collections;  
import java.util.List;  
  
public class CollectionSortStringByLength {  
    public static void main(String[] args) {
        
        List<String> list=new ArrayList<>();  
        
        list.add("Hello World!");  
        list.add("Dharunpandi");  
        list.add("Jerome");  
        list.add("Ahmed");  
        
        Collections.sort(list);  
        System.out.println("Output:");
        System.out.println(list);  
    }  
}
```

```java
Output:
[Ahmed, Dharunpandi, Hello World!, Jerome]
```

*Question What if we want to compare by it's length of the `String`. with `Comparator Interface`. we can modify our sorting differently.*

```java
Comparator<String> comparator = new Comparator<>()
	{
		public void compare(String s1,String s2)
		{
			return s1.length() < s2.length() ? 1:-1; 
		}	
	};
List<String> list=new ArrayList<>();  
        
        list.add("Hello World!");  
        list.add("Dharunpandi");  
        list.add("Jerome");  
        list.add("Ahmed");  
        
        Collections.sort(list,comparator);  
        System.out.println("Output:");
        System.out.println(list);  
```

*This how we can do custom compare. Since Comparator is Functional interface we can use `Lamnda Expresstion` to simplifies code.*

```java
Comparator<String> comparator = (s1, s2) -> return s1.length() < s2.length() ? 1:-1;
```

#Note 
*We can Also Compare `class` as well with `Comparator interface` or `Comparable interface`.*
*The `Comparable interface`.This gives the power to the class to compare itself.*

```java
class student implements Comparable<student>  
{  
    int Rank;  
    String Name;  
  
    public student(int rank, String name) {  
        Rank = rank;  
        Name = name;  
    }  
    public String toString() {  
        return "student{" +  
                "Rank=" + Rank +  
                ", Name='" + Name + '\'' +  
                '}';  
    }  
  
    @Override  
    public int compareTo(student o) {  
        return this.Rank > o.Rank? 1:-1;  
    }  
}
```

```java
[student{Rank=1, Name='Ahmed'}, student{Rank=2, Name='Jerome'}, student{Rank=7, Name='Ishaq'}, student{Rank=9, Name='Dharunpandi'}]
```

We can also use Comparator as well.

```java
public class Threads.Main {  
    public static void main(String[] args) {  
        
        Comparator<student> comp = (o1,o2) -> o1.Rank > o2.Rank ? 1:-1; 
        
        List<student> list=new ArrayList<>();  
        
        list.add(new student(7,"Ishaq"));  
        list.add(new student(9,"Dharunpandi"));  
        list.add(new student(2,"Jerome"));  
        list.add(new student(1,"Ahmed"));  
        
        Collections.sort(list,comp);  
        
        System.out.println(list);  
    }  
}
```

