
*We all know that `String` are `Immutable`, but `StringBuffer` are `mutable`.It  does not Create an new `Object` in `String Bool`. and the Previous on will be cleared by `Garbage collector`.*

```java
public class StringBufferExample{ 
	public static void main(String[] args) { 
		// Create a new StringBuffer
		StringBuffer stringBuffer = new StringBuffer("Hello");
		// Append text to the StringBuffer 
		stringBuffer.append(" World"); 
		// Insert text at a specific position 
		stringBuffer.insert(5, " Java"); 
		// Delete characters from the StringBuffer 
		stringBuffer.delete(5, 10); 
		// Reverse the contents of the StringBuffer 
		stringBuffer.reverse(); 
		// Display the final result 
		System.out.println(stringBuffer.toString());
	}
}
```


- *The `StringBuffer class` in `Java` represents a `mutable` sequence of characters, providing an alternative to the `immutable String class`. It allows for modifying the contents of a `string` without creating a new object each time.*
- *`StringBuffer` objects are mutable, meaning their contents can be changed without creating a new `object`.*
- *Important methods of the `StringBuffer class` include `append()` for adding text at the end, `insert()` for inserting text at a specified position, `delete()` for removing characters, and `reverse()` for reversing the order of characters.*
- *`StringBuffer` is `thread-safe`, allowing multiple `threads` to access and modify it simultaneously.*
- *It offers advantages over regular `String objects` in terms of `efficiency` and `mutability`.* 
- *Additionally, `StringBuffer` has constructors to set the initial `capacity` and `methods` like `length()`, `capacity()`, and `ensureCapacity()` for various operations on the `buffer`.*
