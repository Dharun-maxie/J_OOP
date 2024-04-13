
*`Interface` is collection of `abstract` Methods in simple terms*

Here's a simple example in Java of an interface called `Shape`:

```java
// Interface definition
interface Shape {
    double calculateArea();
    double calculatePerimeter();
}

// Class implementing the interface
class Circle implements Shape {
    private double radius;

    public Circle(double radius) {
        this.radius = radius;
    }

    @Override
    public double calculateArea() {
        return Math.PI * radius * radius;
    }

    @Override
    public double calculatePerimeter() {
        return 2 * Math.PI * radius;
    }
}

// Class implementing the interface
class Rectangle implements Shape {
    private double length;
    private double width;

    public Rectangle(double length, double width) {
        this.length = length;
        this.width = width;
    }

    @Override
    public double calculateArea() {
        return length * width;
    }

    @Override
    public double calculatePerimeter() {
        return 2 * (length + width);
    }
}

// Threads.Main class
public class Threads.Main {
    public static void main(String[] args) {
        Circle circle = new Circle(5);
        System.out.println("Area of Circle: " + circle.calculateArea());
        System.out.println("Perimeter of Circle: " + circle.calculatePerimeter());

        Rectangle rectangle = new Rectangle(4, 6);
        System.out.println("Area of Rectangle: " + rectangle.calculateArea());
        System.out.println("Perimeter of Rectangle: " + rectangle.calculatePerimeter());
    }
}
```


In this example:

- We have an interface called `Shape` with two methods: `calculateArea()` and `calculatePerimeter()`.
- The `Circle` class implements the `Shape` interface and provides its own implementations for the `calculateArea()` and `calculatePerimeter()` methods.
- Similarly, the `Rectangle` class implements the `Shape` interface and provides its own implementations for the `calculateArea()` and `calculatePerimeter()` methods.
- In the `Threads.Main` class, we create objects of `Circle` and `Rectangle` classes and call their methods to calculate area and perimeter.

#Note 

- *The Methods in the `interfaces` are always `public Abstract` Methods even we don't mention it*
- *The Variable that are defined in the `interface` are `static` and `final` so we can't modify it and we can call it via it's `interface` Name.*
- *`interface` also support multiple `interface` implementation *
	-> *for `class -> class` use extends*
	-> *for `class -> interface` use implements*
	-> *for `interface -> interface` use extends*

### TYPES OF INTERFACES

- *Normal Interface*
- *Functional Interface or SAM(Single Abstract Method Interface)*
- *Marker Interface*

**Normal Interface :**

*Normal `Interface` is when we have more then one or two method in the `Interface` is called `Normal Interface`.*

**Functional Interface :**

*Functional `Interface` is When we only one method inside an `Interface` is called Functional `Interface`.*

*This type of interface has extra functionality as well.*

```java
interface A
{
	void add();
}

interface B
{
	int mul(int a,int b);
}

class Threads.Main
{
	public static void main()
	{
		// code here.
	}
}
```

**We know that we can't create an object from Interface.**
- *If we want access it we have to implement the `interface` to an `class` then `Override` the method to get the Result.*
- *In another way we can create an `anonymous inner class` and override the method to get the Result.*
- *But there is another short cut to that. it is been there since `java 8`*

### Lambda function -> it is used to reduce the number of code the we have write.

```java
class Threads.Main
{
	public static void main()
	{
		System.out.println("Output :");
		// void type Method.
		A obj =new A()    // Anonymous Inner class
		{
			void add()
			{
				System.out.println("5+5 = 10");
			}
		};
		A obj1=() -> {
				System.out.println("5+5 = 10");
			};  // lanmbda Function
		
		obj.add();
		
		obj1.add();
		
		// return Type Method.
		
		B obj2 =new B()    // Anonymous Inner class
		{
			int mul(int i,int b)
			{
				return i*j;
			}
		};
		
		B obj3 = (int i ,int j) -> i*j;
		
		obj2.add(5,5);
		
		obj3.add(10,10);
	}
}
```

```java
Output : 
5+5 = 10
5+5 = 10
25
100
```
