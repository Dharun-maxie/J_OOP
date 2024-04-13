*A `thread` is the smallest `unit` of execution within a process. In simple terms, it's a sequence of instructions that can be executed independently by a processor core.*

*Threads are commonly used in programming to perform multiple tasks simultaneously or to handle `asynchronous` events. For example, in a graphical user interface (GUI) application, one `thread` might handle user input while another `thread` updates the display.*

Let create an Thread to test some its function.

```java
class A extends Thread
{
	public void run()
	{
		for(int i=0; i< 10; i++)
		{
			System.out.print("Hello ");
            try {
                Thread.sleep(10);
            }catch (Exception e) { System.out.println("Thread Failed");}
		}
	}
}
class B extends Thread
{
	public void run()
	{
		for(int i=0; i< 10; i++)
		{
			System.out.print("world! ,");
            try {
                Thread.sleep(10);
            }catch (Exception e) { System.out.println("Thread Failed");}
		}
	}
}
class Main
{
	public static void main(String[] args)
	{
		A obj = new A();
		B obj1 = new B();
		obj.start();
        
        try {
            Thread.sleep(7);
        } catch (Exception e) { System.out.println("Thread Failed");}
        
		obj1.start();
	}
}
```

**The Output**
```java
Hello world! ,Hello world! ,Hello world! ,Hello world! ,Hello world! ,Hello world! ,Hello world! ,Hello world! ,Hello world! ,Hello world! ,
```

*As we can see the output is simultaneous. This isn't only way we can use `Thread`,instead we can implement `Runnable interface`. which is implemented into `Thread class` since `Thread class` has constructor which take `Runnable` object, and then we can create an separate object of `Thread` to pass the `Runnacble class` object to it.*

#Note  **Use Ctrl click the class and Interface to View the inbuild class.**

```java
class A implements Runnable  
{  
    public void run()  
    {  
        for(int i=0; i< 10; i++)  
        {  
            System.out.print("Hello ");  
            try {  
                Thread.sleep(10);  
            }catch (Exception e) { System.out.println("Thread Failed");}  
        }  
    }  
}  
class B implements Runnable  
{  
    public void run()  
    {  
        for(int i=0; i< 10; i++)  
        {  
            System.out.print("world! ,");  
            try {  
                Thread.sleep(10);  
            }catch (Exception e) { System.out.println("Thread Failed");}  
        }  
    }  
}  
class Main  
{  
    public static void main(String[] args)  
    {  
        Runnable obj = new A();  
        Runnable obj1 = new B();  
          
        Thread t1=new Thread(obj);  
        Thread t2=new Thread(obj1);  
          
        t1.start();  
        t2.start();  
    }  
}
```
## Thread Management

*The `Thread` is are Processed by `CPU CORE`. The number of `core` in `CPU` are number of `Thread` handled Simultaneously.*

#VeryImportantNote 
![[Pasted image 20240316180431.png]]
## Thread Priority

*In `java` we can set a priority for a `Thread`. The Higher the priority the faster the `Thread` get processed.*

```java
class Threads.Main
{
	public static void main(String[] args)
	{
		A obj = new A();
		B obj1 = new B();
		
		System.out.println(obj.getPriority());  // normal priority
		System.out.println(obj1.getPriority());
		
		obj.setPriority(Thread.MAX_PRIORITY);   // Max priority
		obj1.setPriority(Thread.MIN_PRIORITY);  // Min priority
		
		System.out.println(obj.getPriority());
		System.out.println(obj1.getPriority());
		
	}
}
```



## Threads using Lambda Expression

*Since `Runnable` is an `Functional interface` we can use `Lambda` Expression create an `run` method.*

![[Pasted image 20240316184052.png]]

**Lets Code it.**

```java
class Threads.Main  
{  
    public static void main(String[] args)  
    {  
        Runnable obj = () -> {              // Lambda Function
            for(int i=0; i< 10; i++)  
            {  
                System.out.print("Hello ");  
                try {  
                    Thread.sleep(10);  
                }catch (Exception e) { System.out.println("Thread Failed");}  
            }  
        };  
        Runnable obj1 = new Runnable() {    // Normal Runnable Implementation
            @Override  
            public void run() {  
                for(int i=0; i< 10; i++)  
                {  
                    System.out.print("world! ,");  
                    try {  
                        Thread.sleep(10);  
                    }catch (Exception e) { System.out.println("Thread Failed");}  
                }  
            }  
        };  
        
        Thread t1=new Thread(obj);  
        Thread t2=new Thread(obj1);  
        
        System.out.println("Output:")
        
        t1.start();  
        t2.start();  
    }  
}
```

```java
Output:
Hello world! ,world! ,Hello Hello world! ,Hello world! ,world! ,Hello world! ,Hello Hello world! ,Hello world! ,world! ,Hello Hello world! ,
```

**The Output is depends on the `OS Scheduler` and number of `core` in `CPU`.**

#VeryImportantNote 
## MUTATION  [[Mutation]]

**Mutation can be a powerful tool in programming, allowing objects to represent changing data and enabling dynamic behavior. However, it also introduces complexity, especially in concurrent or multithreaded environments where multiple threads may attempt to mutate the same object simultaneously, potentially leading to data inconsistency or race conditions. Therefore, it's essential to carefully manage mutation, often through techniques such as encapsulation, synchronization, and immutable data structures, to ensure program correctness and maintainability.**

#VeryImportantNote 
## Thread with Mutation

*`Threads` can concurrently `mutate` shared `data`, leading to potential conflicts.*

```java
class Threads.Counter
{
	int count;
	public void countIncremnt()
	{
		count++;
	}
}
class Threads.Main  
{  
    public static void main(String[] args)  
    {  
	    Threads.Counter c_obj = new Threads.Counter(); 
        Runnable obj = () -> {              // Lambda Function
            for(int i=0; i< 500; i++)  
            {  
               c_obj.countIncrement();
            }  
        };  
        Runnable obj1 = () -> {  
            for(int i=0; i< 500; i++)  
            {  
                c_obj.countIncrement(); 
            }  
        };  
        
        Thread t1=new Thread(obj);  
        Thread t2=new Thread(obj1);  
        
        System.out.println("Output:")
        
        t1.start();  
        t2.start();  
        
        
        // join comes here
	    
	    
	    System.out.println(c_obj.count); // The Output : 1000
    }  
}
```

*The real output is not 1000.it will be <=1000. it happens because of the `shared object`.*
![[Pasted image 20240316203212.png]]


## Thread safe

*To Avoid this Mutation caused by Shared Object. we need Add this `join` method to code. it will simply wait till the all or selected `Thread` complete it process. In our case `t1` and `t2`.*

```java
try {  
    t1.join();  
} catch (InterruptedException e) {  
    throw new RuntimeException(e);  
}  
try {  
    t2.join();  
} catch (InterruptedException e) {  
    throw new RuntimeException(e);  
}
```

*Even this not enough to solve this. The Solution to this problem is to `Synchronized` the method it will limit the `Thread` accessing the method by one at a time.*

```java
class Threads.Counter  
{  
    int count;  
    public synchronized void countIncrement()  
    {  
        count++;  
    }  
}
```

#VeryImportantNote 
**You can Read more about Thread Safe in [[Concurrency]]**

## Thread Status or Life Cycle.

![[Pasted image 20240316211017.png]]

