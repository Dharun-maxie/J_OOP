
`Method Overloading mean Methods inside a class having same name for method but differnt parameters`
`When it call it will call the specific method that the Threads.Main called`

**Lets create an class called `calculator`**

```java
class calculator 
{

	public int add(int a,int b)
	{
		System.out.println("Method `1` called");
		return a+b;
	}
	
	public int add(int a,int b,int c)
	{
		System.out.println("Method `2` called");
		return a+b+c;
	}
	
	public int add(int a,int b,int c,int d)
	{
		System.out.println("Method `3` called");
		return a+b+c+d;
	}
}
```

The `claculator` class has three method called add specifically which add two numbers and three number and four numbers. these method has same name as well

```java
publlic class Threads.Main
{
	public static void main(String[] args)
	{
		calculator obj=new calcultor();
		
		System.out.println("Output:");
		
		System.out.println(obj.add(10,20,30));      //calls the method 2
		System.out.println(obj.add(10,20));         //calls the method 1
		System.out.println(obj.add(10,20,30,40));   //calls the method 3
	}
}

```

```java
Output:
60
30
100
```

*This is called Method Overloading*

## **Method Overriding**

*Method overriding in `Java` refers to the process where a `subclass` provides a specific implementation for a method that is already defined in its `superclass`. This allows the `subclass` to customize or extend the behavior of the method inherited from the `superclass`*

Code Sample :

```java 

class Animal {
    public void sound() {
        System.out.println("Animal makes a sound");
    }
}

class Dog extends Animal {
    @Override
    public void sound() {
        System.out.println("Dog barks");
    }
}

public class Threads.Main {
    public static void main(String[] args) {
        Animal animal = new Animal();
        animal.sound(); // Output: Animal makes a sound
        
        Animal dog = new Dog(); // Upcasting
        dog.sound(); // Output: Dog barks
    }
}

```

#Note 
*Conditions*
	1. The subclass must define a method with the same name, return type, and parameter list as the one in the superclass.
	2. The method in the subclass must be annotated with `@Override` to indicate that it is intended to override a method in the superclass (though this annotation is optional)