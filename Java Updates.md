# LVTI - (Local Variable Type Inference)

*It is an new Update that came in `java 8` and got even new Update in `java 10`.*

```java
Public static void main
{
	ArrayList<Integer> obj = new ArrayList<>();
	// instead we can use this
	var obj = new ArrayList<>();
}
```

*It's very new Only updated release in `JDK 21`. it called `Unnamed class` and `instance main Method`.*

```java
void main()  
{  
    System.out.println("Hello World!!!");  
}
```

*if We want to `Execute` single `java` file in the `Terminal` . we have `compile` it then `Execute` it, but now we don't have to.*

```java
public class Threads.Main  
{  
    public static void main(String[] args) {  
        System.out.println("Hello World !!!");  
    }  
}
```
![[Pasted image 20240319102357.png]]

# String Modification in java

Now we can use `Modified String` in `java`. pretty Straightforward. it came in `JDK 21` Release.

```java
class Main
{
	public static void main(String[] args)
	{
		String name="Dharunpandi";
		int age=21;
		
		System.out.println(STR."Hi, my name is \{name} and i am \{age} years Old.");
	}
}
```