
*Older way of taking an input from the user is bit of headache.*

```java
import java.io.InputStreamReader;
import java.io.BufferedReader;
class Threads.Main
{
	public static void main(String[] args)
	{
        System.out.println("Enter the Number :");
        int num=0;
		InputStreamReader put = new InputStreamReader(System.in);
		BufferedReader bf = new BufferedReader(put);
	    // or we can use it  like this
	    BufferedReader bf = new BufferedReader(new InputStreamReader(System.in));
        try{
            num=Integer.parseInt(bf.readLine());
		}
        catch(Exception e)
        {
            System.out.println(e);
        }
        finally
        {
	        bf.close();
        } 
        // another way try with resource
        // it will automatically close the resource 
        try(BufferedReader bf=new BufferedReader(new InputStreamReader(System.in)))
        {
	        num=Integer.parseInt(bf.readLine());
        }
        catch(Exception e){
            System.out.println(e);
        }
		System.out.println(num);
	}
}
```

#VeryImportantNote 
- *`println`  is method of `PrintStream class` which print a `newline` to Access `println` method we need an `object` of `PrintStream` which is out as `static` variable that is declared in `System class`, since we can access an `static` variable using `class` name that what we are doing here `System.out.println()`.*
- *same for `in` as well it is `object` of an `InputStream` that declared in the `System class`*


**Another way of get data from user is to use `Scanner class`**

```java
import java.io.Scanner;

class Threads.Main
{
	public static void main(String[] args)
	{
		System.out.println("Enter the Number :");
		Scanner put=new Scanner(System.in);
	}
}
```

#Note 
- *`Scanner class` is introduced in `java 1.5`*

