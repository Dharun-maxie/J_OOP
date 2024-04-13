
# Java Exception Hierarchy


```Markdown
Throwable
├── Exception (Recoverable Errors)
│   ├── Checked Exceptions (Declare in throws clause)
│   │   ├── IOException (File/Network Issues)
│   │   │   ├── FileNotFoundException
│   │   │   └── EOFException
│   │   │   └── ... (many more)
│   │   └── ... (many more Checked Exceptions)
│   └── Unchecked Exceptions (Runtime Errors)
│       ├── RuntimeException (General Runtime Issues)
│       │   ├── IndexOutOfBoundsException
│       │   ├── NullPointerException
│       │   ├── NumberFormatException
│       │   └── ... (many more)
│       └── ... (many more Unchecked Exceptions)
└── Error (Severe Errors, Not Generally Recoverable)
    └── ... (many more Errors)
```


**Checked Exception Example (IOException):**

```java
public void readFile(String fileName) throws IOException {
    try (FileReader reader = new FileReader(fileName)) {
        // Read data from the file
    } catch (FileNotFoundException e) {
        // Handle case where the file doesn't exist
        System.out.println("Error: File not found - " + fileName);
    }
}
```

In this example, `readFile` throws an `IOException` because the `FileReader` constructor might throw a `FileNotFoundException` (a checked exception subclass of `IOException`) if the file isn't found. This forces the caller to handle this potential error using a `throws` clause or catching the exception.

**Unchecked Exception Example (NullPointerException):**

```java
public void greetUser(User user) {
    if (user != null) {
        System.out.println("Hello, " + user.getName() + "!");
    } else {
        // Handle case where user is null
        System.out.println("Error: User object is null!");
    }
}
```

Here, if the `greetUser` method is called with a `null` user object, it throws a `NullPointerException` when trying to access `user.getName()`. This is an unchecked exception because it's usually a programmer error (not checking for null before accessing the object's methods).

**Custom Exception Example:**

```java
public class InvalidAgeException extends Exception {
    public InvalidAgeException(String message) {
        super(message);
    }
}

public void registerUser(int age) throws InvalidAgeException {
    if (age < 13) {
        throw new InvalidAgeException("User must be at least 13 years old.");
    }
    // Register user logic
}
```

This `InvalidAgeException` can be used to signal an error when a user tries to register with an invalid age. The advantage is that you can provide a more specific error message to the user compared to a generic exception.