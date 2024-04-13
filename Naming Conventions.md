
Naming conventions is a term that is used for naming variables, methods and class. java has it own naming conventions.
#### **`Java` use Camel casing**

*`class` name are start with Capital letter*

```java
class Student
{
	public static void main(String[] args)
	{
		System.out.println("Hi, I am Java. I use Camel casing");
	}
}
```

*`method` name are start with small letter and Capital letter, and `variable` name are in smaller case*


```java
class Maths
{
	public static int fiboOfNumber(int num)
	{
		if(num == 1)
		{
			return num;
		}
		return num*fiboOfNumber(num-1);
	}
	public static void main(String[] args)
	{
		int num=5;
		System.out.println("Output:");
		System.out.println(fiboOfNumber(num));
	}
}
```

```java
Output:
120
```

*`CONSTANT` variable are declared in Capital case*

```java
class Threads.Main
{
	public static final float PIE = 3.142f;
	public static void main(String[] args)
	{
		final int LUCK=389;
		System.out.println("PI VALUE: "+ PIE);
		System.out.println("Lucky Number: "+ LUCK);
	}
}
```