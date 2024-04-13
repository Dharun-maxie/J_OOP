
`Object is instance of an class`
`Every object has it own chracteristic and methods(Functions)`

*Let is take a pen as a Example*
	*-> class is the blueprint of an object it is let us to create an object*
	*-> the pen object has different set method and characteristics*
	*-> like dimension of the pen height diameter*
	*-> color of the pen, etc.*

*Lets create an class called calculator*
```java
class calculator
{
	calculator
	{
		System.out.println("Constructor Called")
	}
	public int add(int a, int b)
	{
	    return a + b;
	}
	public int sub(int a, int b)
	{
	    return a - b;
	}
	public int mul(int a, int b)
	{
	    return a * b;
	}
	public float div(int a, int b)
	{
	    return a / b;
	}
}
```

**Creating an object to access the methods**
```java
claculator obj=new calculator();

// we can also use for one time use like this

new calculator();  // It is called anonymous class

new calculator().add(10,20); // we can also do that
```

**Anonymous class**
	it only create an `object` in heap memory. when it called again it will create an new `object` in the heap memory.

`obj` -> is the Instance variable or `object` reference 
`calculator` -> is the class that want access by creating Instance of the class using `new` keyword it allocate new space in memory for the newly created `obj`.  


**CODE EXAMPLE:**

```java
public class Threads.Main{
  public static void main(String[] args)
  {
    calculator obj=new calculator();
    System.out.println("OUTPUT:")
    System.out.println(obj.add(10,20));
    System.out.println(obj.sub(10,20));
    System.out.println(obj.mul(10,20));
    System.out.println(obj.div(10,20));
  }
}
```

```java
OUTPUT:
30
-10
200
0.0
```

## OBJECT CLASS 

*We can simply say that `object class`  is `class` which is inherited by every other parent `class`*

```java
class parent // extends Object which we don't actually have to extend it
{
	int kids;
	int name;
	
	public void p()
	{
		System.out.println("In Parent Class");
	}
	// code <toString> goes here.
}
```

*Object `class` has so many Build-in Methods, Here some the Methods*

LETS CREATE AN MAIN METHOD TEST THIS,

#### toString() -> it is Object class method return a string which contains class name, method name, and some hash value at the end.


```java
class Threads.Main
{
	public static void main(String[] args)
	{
		parent obj=new parent();
		obj.kids=2;
		obj.name="John";
		System.out.println("Output :");
		System.out.println(obj);
	}
}
```

*printing `object` with `object reference`*

```java
Outout:
parent@<Some hashValue>
```

*It is printing the `toString` method that is inherited from the `Object class`. we can return correct values by Method Overriding.*

```java
public String toString()
{
	return "Name : "+name+"\n"+"Kids : "+kids; 
}
```

*to call this we have to print it `obj.toString()`, and It will return this*

```java
Output :
Name : John
Kids : 2
```

#### equals() -> is an Object class method which take an object as a input return Boolean value if other object is equal or not.


```java
class parent // extends Object which we don't actually have to extend it
{
	int kids;
	String name;
	
	public void p()
	{
		System.out.println("In Parent Class");
	}
	public String toString()
    {
    	return "Name : "+name+"\n"+"Kids : "+kids; 
    }
    public boolean equals(parent that)
    {
        return this.name.equals(that.name);
    }
}
class Threads.Main {
    public static void main(String[] args) {
        parent obj=new parent();
		obj.kids=2;
		obj.name="John";
		System.out.println("Output:");
		System.out.println(obj.toString());
        parent obj2 = new parent();
        obj2.kids=2;
		obj2.name="John";
        
		System.out.println(obj.equals(obj2));
    }
}
```

```java 
Output:
Name : John
Kids : 2
true
```

#Note

*we can also ignore some variable are checking equal or not in the `Object` by not adding in the `equals` Method*

### ABSTARCT CLASS

*It is a type of class where it method are need to be override by all the class the inherit it*

```java
abstract class vehicle
{
	public abstract void wheels();
	
	public void Song()
	{
		System.out.println("Music ON");
	}
}

class AutoRickShaw extends vehicle  // it is called concrete class
{
	public void wheels()
	{
		System.out.println("Auto RickShaw has 3 wheels");
	}
}

class Threads.Main {
    public static void main(String[] args) {
        // vehicle obj=new vehicle();

        // vehicle obj=new AutoRickShaw();
        AutoRickShaw obj = new AutoRickShaw();
		System.out.println("Output:");
		
		// vehicle obj =new vehicle();
		// we can't create object from abstract class
		// we can only create from the it chlid or Subclass
		
		obj.wheels();
		obj.Song();
    }
}


```

#Note
 *If we decide not to use some the abstract function we can choose not use or we can also make the `child class` into `Abstract class` as well. but we also need to create new `class` to access the `child class` since `abstract class` can't have `objects`*
 #VeryImportantNote 
 *If we want access `abstract class` for one time purpose we can use `Anonymous inner class`
 more about that later.*


### INNER CLASS

*`Inner class` mean, when there is `class` created inside another `class` called `inner class`.*

```java
class A
{
	int num=3;
	public void show()
	{
		System.out.println("In 'class' A");
	}
	
	class B
	{
		int num=9;
		public void show()
		{
			System.out.println("In 'class' B");
		}
	}
}

class Threads.Main
{
	public static void main(String[] args)
	{
		A obj=new A();
		
		System.out.println(obj.num);
		obj.show();
		// to acces the Class B
		 A.B obj1 = obj.new B();
		 System.out.println(obj1.num);
		 obj1.show();		
	}
}
```

```java
3
In 'class' A
9
In 'class' B
```

*If we declare `inner class` as `static class`, we declare `object` like this*

```java
A.B obj1 = new A.B();
```

It is because `static class` or Method can be called by it's `class` name. if it not `static` then we have to call it by it's `object`.

#Note

*We can create an `static class` other then `MAIN class` but only as an `inner class`.*

### ANONYMOUS INNER CLASS

*`Anonymous class` is a `class` that does not have reference `variable`. It is mostly used for one time uses or only one purpose of doing something once.*

```java
class A
{
	public void show()
	{
		System.out.println("In A class");
	}
}
class B extends A
{
	public void show()
	{
		System.out.println("In B class");
	} 
}

class Threads.Main
{
	public static void main(String[] args)
	{
		// Test it as you like it
	}
}
```

*if We want override `class` A's Method we can do that via `class` B's `object`. like this*

```java
class Threads.Main
{
	public static void main(String[] args)
	{
		B obj=new B();
		obj.show();
	}
}
```

*Because of the only one purpose of `override` we had to create an whole new `class`. instant we can do this*

```java
class Threads.Main
{
	public static void main(String[] args)
	{
		A obj = new A()
		{
			public void show()
			{
				System.out.println("In Anonymous Inner class");
			}
		};
		obj.show();
	}
}
```

*We are creating an new `inner class`  of A. since it has no Name it called `Anonymous inner class`.*

#Note 

**We can also use `Anonymous Inner class` for the `Abstract class` as well. just like previous code Example.**
```java
abstract class A
{
	public abstract void show();
}
class Threads.Main
{
	public static void main(String[] args)
	{
		A obj = new A()
		{
			public void show()
			{
				System.out.println("In Anonymous Inner class");
			}
		};
		obj.show();
	}
}
```

**In Here we are not creating an object of an `abstract class`, we are creating an `Anonymous Inner class` of the `Abstract class`.**

### SEALED CLASS

**`sealed calss` used when we want only some or selected `class` to `inherit` the `property` some other `class`. it use `permits` keyword to allow the `class`.**

```java
sealed class A permits B,C {}
class B extends A{}
class C extends A{}
class D extends A{}

class Threads.Main
{
	public static void main(String[] args)
	{
		System.out.println("Hello World!!!");
	}
}
```

#Note 
*It will give an `Compile` time Error since we trying to inherit `class A` method to `class D`. Because we Didn't permit `class D` to inherit `class A`. This is `Sealed class`.The inherited `class` should be `final`, `sealed` or `non-sealed` to this this type of `heritance`.*


### **RECORED CLASS**

- Introduced in Java 16, record classes are a concise way to define immutable data holders.
- They provide a lightweight syntax and automatically generate common methods like `equals()`, `hashCode()`, and `toString()`.
- Ideal for representing simple data objects like DTOs (Data Transfer Objects) where immutability and consistent behavior are desired.
- Data holding `variable` in `class` are called state. it is Final and immutable.

```java
record Person(String name, int age) {
    // Custom logic can be added here if needed
}
```

*The `name` and `age` are called `state` variable or `state` description. And it basically create an `constructor`, In our case it create `constructor` which take two `parameter`*

**Compact Canonical Constructor**

```java
record person(int age, String name){
	// it is a Default Constructor
	person() 
	{
		this(0,""); 
		// call the parameterized constructor and pass some dummy value
	}
	// since the variable are final we shouldn't have pass dummy value.
	
	
	// this Normal Constructor which is automatically create by record class 
	person(int age,String name) // parameterized Constructor 
	{
		this.age=age;
		this.name=name;
	}
	// we dont really have to create this this will cause error for other constructor
	
	public person // compact canonical constructor  
	{  
	    if(age < 18)  
	        throw new IllegalArgumentException("The Person cannot be Under 18");  
	}
}

class Threads.Main
{
	public static void main(String[] args)
	{
		person p1 =new person(21 , "Jerome");
		person p2 =new person(22 , "Kisore");
		person p3 =new person(21 , "Dharun");
		person p4 =new person(22 , "Ahmed");
	}
}
```

**Key Characteristics:**

- **Immutable:** Once created, a record's state cannot be changed. Fields are implicitly `final`.
- **Implicitly final:** Records themselves cannot be extended (subclassed).
- **Concise Syntax:** Defined using the `record` keyword, followed by field declarations in parentheses.
- **Automatic Methods:** The compiler generates `equals()`, `hashCode()`, `toString()`, and a constructor based on the fields.

### **FINAL CLASS**

- A class declared with the `final` keyword cannot be subclassed.
- Useful for preventing unintended modification of class behavior through inheritance.
- Can be mutable or immutable (fields can be final or non-final).

```java
final class MathUtils {
    public static int add(int a, int b) {
        return a + b;
    }
}
```

Here, the `MathUtils` class is declared as `final`, preventing subclasses from extending it.

**When to Use Which:**

- Use record classes for simple, immutable data objects where you want automatic methods and a concise syntax.
- Use final classes when you explicitly want to prevent inheritance and ensure the class's behavior remains unchanged.

| Feature      | Record Class                                     | Final Class                 |
| ------------ | ------------------------------------------------ | --------------------------- |
| Immutability | Implicitly immutable                             | Can be mutable or immutable |
| Inheritance  | Implicitly final (not subclassable)              | Explicitly non-subclassable |
| Syntax       | Concise (`record` keyword)                       | Regular class declaration   |
| Methods      | Automatic `equals()`, `hashCode()`, `toString()` | No automatic methods        |
