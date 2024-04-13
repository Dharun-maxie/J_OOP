#VeryImportantNote 
*In Java, a `stream` **==represents a sequence of elements==** that can be processed sequentially or in parallel. `Streams` allow you to perform various operations on collections of `data`, such as `filtering`, `mapping`, `sorting`, and `aggregating`, in a concise and fluent manner.
`Streams` are part of the `Java Stream API`, which was introduced in `Java 8`. They are primarily used with `collections` (e.g., lists, sets, maps) and `arrays`, providing a functional programming style to manipulate and process `data`.*

But before that lets talk about `forEach` loop.  `Collection List` had a Method called `forEach` which explicitly `return` a single value at time. With help of `Consumer Interface` we can `print` the value or do some `calculation` with it. 

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);

// it is Functional Interface
Consumer<Integer> consumer = new Consumer<Integer>() {  
    @Override  
    public void accept(Integer integer) {  
        System.out.print(integer * 2 +" ");  
    }  
};
// we can also Write it like this.
Consumer<Integer> consumer = (integer) -> System.out.println(integer);

numbers.forEach(consumer)

//Another Way of Doing it is,

numbers.forEach((integer) -> System.out.println(integer))

// there is also Another way

numbers.forEach(System.out::println())

```

**`Stream` Just like the Name say we cannot use same Stream Again.**

![[Pasted image 20240318225639.png]]

*The `stream` of`list` return an `Generic Stream`. But once we use the `Stream` we can't reuse it.*

```java
import java.util.Arrays;  
import java.util.List;  
import java.util.stream.Stream;  
public class stream {  
    public static void main(String[] args) {  
        List<Integer> lst = Arrays.asList(1,2,3,4,5,6,7,8,9);  
        
        System,out.println("Output :");
        Stream<Integer> stream1 =  lst.stream();  
        
        stream1.forEach(n -> System.out.print(n+" "));
        
        // stream1.forEach(System.out::println);
        
        stream1.forEach(n -> System.out.println(n));  
    }  
}
```

**The Output**

![[Pasted image 20240319080418.png]]

#Note 
Here Some of Stream API Methods.
```java
import java.util.Arrays;  
import java.util.List;  
import java.util.stream.Stream;  
public class stream {  
    public static void main(String[] args) {  
        List<Integer> lst = Arrays.asList(1,2,3,4,5,6,7,8,9);  
        
        Stream<Integer> stream1 = lst.stream();  
        Stream<Integer> stream2 = stream1.filter(x -> x%2==0);
        Stream<Integer> stream3 = stream2.map(x -> x*2);  
        
        int result = stream3.reduce(0, Integer::sum);    
        
        System.out.println(result);  // The Output is 40
        
        List<Integer> lst = Arrays.asList(1,2,8,9,3,6,7,5);
        
        Stream<Integer> lst1= lst.stream().sorted();
        lst1.forEach(System.out::println);
    }  
}
```

**We can also Do this.**

```java
int result = lst.stream().filter(x->x%2==0).map(x->x*2).reduce(0,Integer::sum);
// this return the total sum of even number multiplied by 2
System.out.println(result); // The Output is 40.
```

*Methods Explanation.*

```java
// functional Interface
Predicate<Integer> pred = new Predicate<Integer>() {  
    @Override  
    public boolean test(Integer n) {  
	    // testing Logic goes here. In our case we need to find Even number. so,
        return n%2==0;  
    }  
};  
  
Function<Integer, Integer> func=new Function<Integer, Integer>()  
{  
    @Override  
    public Integer apply(Integer n)  
    {  
        return n+2;  
    }  
};  
  
BinaryOperator<Integer> sum=new BinaryOperator<Integer>() {  
    @Override  
    public Integer apply(Integer n1, Integer n2) {  
        return n1+n2;  
    }  
};
```

#VeryImportantNote 
- **The `filter` take an object of `Predicate` which define the logic of filtering value and `return` a `boolean`.**
- **The `map` take an object of `Function` which call the `apply` method. then it return applied mathematical funcion.**
- **The `reduce` method two parameter one is `Identity` the another one is `BinaryOperator Interface` has one method that `apply`. it is an return type which take two parameter.**

```java
List<Integer> lst = Arrays.asList(1,2,8,9,3,6,7,5);  
  
Stream<Integer> lst1= lst.stream().sorted();  
  
lst1.forEach(System.out::println);
```

#VeryImportantNote 
**If we want use `stream` with `Threads` we have use `parallelStream`. And using Sorted with `ParallelStream` is not a good Idea because Sorting need entire `Stream` to `compare` to Sort the List, It will cause Instability in the `Threads`. We can sort it after `Thread join`.**

```java
Stream<Integer> lst1= lst.parallelStream().filter(x-> x%2==1); // for ODD Number
```

