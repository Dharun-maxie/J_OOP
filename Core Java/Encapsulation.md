*`Encapsulation` is a technic that is used to Restrict data by every one in class it is achieved by using the keyword called `private`*.
*`private` variable and method are can't be accessed by instantiated object because of the security
reasons. if object has access to class variable it can manipulated.*
*because of that we make it inaccessible to the object. it can accessed only via `getters` and `setters`*
*The `getters` and `setters` are `object` methods that can be Accessed by `objects`*


```java
class humen
{
	private String name;
	private int age;
	// constructor
	public humen()
	{
		name="";
		age=0;
	}
	// parameterized constructor
	public humen(int age,string name)
	{
		this.name=name;
		this.age=age;
	}	
	// getters
	
	// setters
}
```

#####  *`constructor` -> is used to set default value to instance variable. `constructor` is usually have the class name as the calling name* 

##### *`getters()` -> is used to get the data from the `object`*

```java 
public String getName()
{
	return this.name;
}
public int getAge()
{
	return this.age;
}
```
###### *`getters` can be static as well, but we have to give the object as a parameter in order to access the data*

##### *`setters()` -> is used to set the data by user*

```java
public void getName(String name)
{
	this.name=name;
}
public void getAge(int age)
{
	this.age=age;
}
```

*In `setters` the object data is set by `this` keyword. `this` keyword used to specify the current object it's in.*

*Lets create an Threads.Main class*

```java
public class Threads.Main
{
	public static void main(String[] args)
	{
		humen obj=new humen();
		obj.setName("Dharun");
		obj.setAge(21);
		
		System.out.println(obj.getName());
		System.out.println(obj.getAge());
		
	}
}
```


