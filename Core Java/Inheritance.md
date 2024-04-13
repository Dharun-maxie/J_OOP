*`Inheritance` is a technique that used to access another `class` methods and variable by using `extends` keyword to the `Threads.Main class` or any other `class`.*

#### super() -> is used to call the parent `class` from the child `class`

```java
// MULTILEVEL INHERITANCE
class A{
	A()
	{
		super();
		System.out.println("In A is Default constructor");
	}
	A(int x)
	{
		super();
		System.out.println("In A is Parameterized constructor");
	}
}
class B extends A{
	B()
	{
		super();
		System.out.println("In B is Default constructor");
	}
	B(int x)
	{
		super();
		System.out.println("In B is Parameterized constructor");
	}
}
```

*In this code `A` is the parent `class` and `B` is the child `class` .child `class` can inherit the methods and variable as well.*

#Note 
**Every `class` inherit it parent `class` using `super` keyword it being called even we did not called the  `super`.where `B` call `A` and `A` call the parent of `A class`,the `Object class`**

*Lets create an `Threads.Main class` to test this*

```java
class Threads.Main
{
	public static void main(String[] args)
	{
		System.out.println("Output :");
		B obj =new B();
		System.out.println();
		B obj2 =new B(5);
	}
}
```

```java
Output :
In A is Default constructor
In B is Default constructor

In A is Default constructor
In B is Parameterized constructor
```
 *If we pass the parameter to the `super(x)` from `B`'s parameterized constructor, it will call the `A`'s parameterized constructor.*

#### this() -> is used to call it self or it own constructor when the `Object` is Created

```java
class A{
	A()
	{
		super();
		System.out.println("In A is Default constructor");
	}
	A(int x)
	{
		super();
		System.out.println("In A is Parameterized constructor");
	}
}
class B extends A{
	B()
	{
		super();
		System.out.println("In B is Default constructor");
	}
	B(int x)
	{
		this();
		System.out.println("In B is Parameterized constructor");
	}
}
```

*Lets create an Threads.Main class to test  this `this()` method*

```java
class Threads.Main
{
	public static void main(String[] args)
	{
		System.out.println("Output :");
		B obj =new B();
		System.out.println();
		B obj2 =new B(5);
	}
}
```

```java
Output :
In A is Default constructor
In B is Default constructor

In A is Default constructor
In B is Default constructor
In B is Parameterized constructor: 5
```

##### *IN `JAVA` THERE IS FEW TYPE OF `INHERITANCE` THEY ARE,*
	-> **SINGLE LEVEL INHERTANCE**
	-> **MULTIPLE LEVEL INHERUTANCE**

#VeryImportantNote 

->*JAVA DOES NOT SUPPORT MULTIPLE INHERTANCE*
	 **MULTIPLE INHERITANCE**:
			Multiple inheritance create ambiguity in code.
			Multiple inheritance mean where child `class` more then one Parent `class`.
