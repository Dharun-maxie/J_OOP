
`Static keyword is used to create variable and method that are common to all the Object it been instantiated. if static variable changed it will affect all the instantiated Object as well.`

*Lets create an static variable and static method*
```java
class student{
	String name;
	int id;
	String section;
	static String school;
	student
	{
		name="";
		id=0;
		section="";
		System.out.print("constructor block called");
	}
	static
	{
		school="DHSS";
		System.out.print("Static block called");
	}
	public void show();
	{
		System.out.println("Name : "+name+"\n"+"ID : "+id+"\n"+"Section : "+section+"\n"+"School : "+school);	
	}
	public static void show3(student obj)
	{
		System.out.println("Name : "+obj.name+"\n"+"ID : "+obj.id+"\n"+"Section : "+obj.section+"\n"+"School : "+school);	
	}
}
```

*static methods and variable are called by it class name not by the object name it can also be called by object as well but it not a good coding practice.*

**STATIC BLOCK**

`static` block is second load after class.
```java
static
	{
		school="DHSS";
	}
```

**STATIC METHOD**

`static` method are also known as class method mostly used for it inner computational.

`static` method are can't be called by it's instantiated object, because multiple object `java` does not know which object called the `static` method.

*to resolve we can pass the object instance variable.*
```java
public static void show3(student obj)
	{
		System.out.println("Name : "+obj.name+"\n"+"ID : "+obj.id+"\n"+"Section : "+obj.section+"\n"+"School : "+school);	
	}
```


*Let create an main method*

```java
class Threads.Main
{
	public static void main(String[] args)
	{
		student s1=new student();
		
		s1.name="Dharun";
		s1.id=2020104032;
		s1.section="A";
		
		student s2=new student();
		
		s2.name="Jerome";
		s2.id=2020104054;
		s2.section="A";
		
		s1.show();
		s2.show();
		
		student.show1(s1);
		
	}
}
```

```java
Static block called
constructor block called
Dharun
2020104032
A
DHSS
constructor block called
Jerome
2020104054
A
```

 #Note 
 *THE `static block` will be called only one when class is Loaded that is also why it can't be accessed by it's instantiated object*.

*THE `class` IS LOAD FIRST TO LOAD BY `class loader` after that `static block`  then constructor loads*


*We can load `class` in `class loader` by calling this method*

```java
Class Main1
{
	public static void main(String[] args)
	{
		Class.forName(class : "student");
	}
}
```

```java
Static block called
```

###### *This `forName` Method from `Class` class used initialize class. It is Mostly used in  `JDBC`*

#Note 
##### *The reason why main block has  `static` in it. let say if we remove the `static` from the main method it became non static method.*
##### *We all know by now if we want access method inside an class we have create an object of the class right.*
##### *Since the main is the first to executed now we can not access the main without object of it Threads.Main class, because of that we use static call it when the java file executed.*






