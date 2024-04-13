
*There are two types of Polymorphism. they are,*
	->*Runtime Polymorphism* *(Method Overriding)* 
	->*Compile time Polymorphism* *(Method Overloading)*

[[Method Overloading & Overriding]]
#### Dynamic dispatch 

```java 
class A
{
	public void Show1()
	{
		System.out.println("In Class A");
	}
}
class B extends A
{
	public void show2()
	{
		System.out.println("In Class B");
	}
}
class C extends A
{
	public void show3()
	{
		System.out.println("In Class C");
	}
}
class Threads.Main
{
	public static void main(String[] args)
	{
		A obj=new A();
6		obj.show2();//can not access the show2 method 
		obj.show3();
		
		obj = new B();
		obj.show2();
		
		obj = new C();
		obj.show3();
	}
}
```

*In this case the Line 6 does not work because the Parent `class` does not aware of it child `class`*
