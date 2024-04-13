
*Lets Create an Junit5 Test for an Method.*

```java

public class PrefixString {  
    public String longestCommonPrefix(String[] strs) {  
        if (strs == null)  
        {  
            throw new NullPointerException();  
        }  
        if(strs.length == 0)  
        {  
            return "";  
        }  
        Arrays.sort(strs);  
        String s1 = strs[0];  
        String s2 = strs[strs.length-1];  
        int idx = 0;  
        while(idx < s1.length() && idx < s2.length()){  
            if(s1.charAt(idx) == s2.charAt(idx)){  
                idx++;  
            } else {  
                break;  
            }  
        }  
        return s1.substring(0, idx);  
    }  
}
```

# Test cases for Testing the Method

```java
 // Junit 5
 import org.junit.jupiter.api.Test;  
 import static org.junit.jupiter.api.Assertions.*;  
 
 public class PrefixStringTest {  
 
 PrefixString obj=new PrefixString();    
	@Test  
	public void testEmptyInput() {  
		assertEquals("", obj.longestCommonPrefix(new String[]{}));  
	}  
	@Test  
	public void testSingleStringInput() {  
		assertEquals("a", obj.longestCommonPrefix(new String[]{"a"}));  
	}  
	@Test  
	public void testAllSameStrings() {  
		assertEquals("flower", obj.longestCommonPrefix(new String[]{"flower", "flower", "flower"}));  
	}  
	@Test  
	public void testDifferentPrefixes() {  
		assertEquals("", obj.longestCommonPrefix(new String[]{"dog", "racecar", "car"}));  
	}  
	@Test  
	public void testEmptyPrefix() {  
		assertEquals("", obj.longestCommonPrefix(new String[]{"", "b", "c"}));  
	}  
	@Test  
	public void testMixedCase() {  
		assertEquals("Fl", obj.longestCommonPrefix(new String[]{"Flower", "Flamingo", "Flash"}));  
	}  
	@Test  
	public void testNumbers() {  
		assertEquals("1", obj.longestCommonPrefix(new String[]{"123", "124", "1"}));  
	}  
	@Test  
	public void testSymbols() {  
		assertEquals("", obj.longestCommonPrefix(new String[]{"$", "%", "&"}));  
	}  
	@Test  
	public void testLongStrings() {  
		assertEquals("This is a ", obj.longestCommonPrefix(new String[]{"This is a Big string 1", "This is a long string 2"}));  
	}  
	public void testNullInput() {
		Executable executable = new Executable(){  
	        @Override  
	        public void execute() throws Throwable {  
	            obj.longestCommonPrefix(null);  
	        }  
	    };  
    // We can also use Lambda FUNCTION Since Executable is a Functional Interface. 
		    assertThrows(NullPointerException.class, executable);  
		}
	}  
}
```

*The `assertEquals` is used to check is actual Output and Expected Output by Comparing them.*

![[Pasted image 20240321111303.png]]
