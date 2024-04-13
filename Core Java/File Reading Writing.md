#Note 
In `java`, to read an `file` or an `Image` we use `Byte Stream` and `Character Stream`.

![[Pasted image 20240401124633.png]]

#VeryImportantNote 
[CODE SAMPLE](https://replit.com/@KunalsReplit/File-handling#Main.java)

There are two main types of streams in Java:

1. **Byte Streams:**
    
    - Byte streams are used for handling raw binary data, such as images, audio, or video files.
    - They are represented by classes in the `java.io` package.
    - The fundamental classes for byte streams are `InputStream` and `OutputStream`, which are abstract classes representing input and output byte streams, respectively.
2. **Character Streams:**
    
    - Character streams are used for handling character data, typically text data.
    - They are represented by classes in the `java.io` package.
    - The fundamental classes for character streams are `Reader` and `Writer`, which are abstract classes representing input and output character streams, respectively.

Now, let's delve into each of these types:

- **Byte Streams:**
    
    - `InputStream`: This abstract class serves as the superclass for all classes representing input byte streams. It defines the basic contract for reading bytes of data from a source. Some commonly used subclasses include `FileInputStream`, `ByteArrayInputStream`, and `BufferedInputStream`.
    - `OutputStream`: This abstract class serves as the superclass for all classes representing output byte streams. It defines the basic contract for writing bytes of data to a destination. Common subclasses include `FileOutputStream`, `ByteArrayOutputStream`, and `BufferedOutputStream`.
- **Character Streams:**
    
    - `Reader`: This abstract class serves as the superclass for all classes representing input character streams. It defines the basic contract for reading characters of data from a source. Some commonly used subclasses include `FileReader`, `InputStreamReader`, and `BufferedReader`.
    - `Writer`: This abstract class serves as the superclass for all classes representing output character streams. It defines the basic contract for writing characters of data to a destination. Common subclasses include `FileWriter`, `OutputStreamWriter`, and `BufferedWriter`.

![[Screenshot 2024-04-01 125305.png]]
Character streams are often preferred over byte streams when dealing with text data because they automatically handle character encoding and decoding, ensuring proper handling of different character sets and reducing the risk of encoding-related issues.

Let take about character stream.

[INPUT_STREAM_READER](file:///D:/Study/1.programming%20material/NO.1%20Priority/docs/api/java.base/java/io/package-summary.html)
	*==*The `InputStreamReader`An InputStreamReader is a bridge from byte streams to character streams==: It reads bytes and decodes them into characters using a specified [charset]. The charset that it uses may be specified by name or may be given explicitly, or the [default charset] may be used.**

*which take an [IMPUT_STREAM](file:///D:/Study/1.programming%20material/NO.1%20Priority/docs/api/java.base/java/io/InputStream.html) as an parameter*,
	This abstract class is the superclass of all classes representing an input stream of bytes.

**[FileReader](file:///D:/Study/1.programming%20material/NO.1%20Priority/docs/api/java.base/java/io/FileReader.html)**
	public class `FileReader` extends [InputStreamReader] Reads text from character files using a default buffer size. Decoding from bytes to characters uses either a specified [charset] or the [default charset].

The `FileReader` is meant for reading streams of characters. For reading streams of raw bytes, consider using a `FileInputStream`.

```java
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.FileReader;

class Main{
	public static void main(String[] args)
	{
		try(InputStreamReader isr =new InputStreamReader(System.in))  
		{  
		    int line=isr.read();  
		    while(line != -1) {  
		        System.out.print((char) line);  
		        line = fr.read();  
			}  
		}  
		catch (IOException e)  
		{  
		    System.out.println(e.getMessage());  
		}
		
		// Using FileReading class to read file from specific File
		try(FileReader fr =new FileReader("D:\\Study\\1.programming material\\NO.1 Priority\\Java + DSA\\codeOOP\\src\\Stream\\TEXT.txt"))  
		{  
		    int line=fr.read();  
		    while(line != -1) {  
		        System.out.print((char) line);  
		        line = fr.read();  
			}  
		}  
		catch (IOException e)  
		{  
		    System.out.println(e.getMessage());  
		}
	}
}
```


*We can use `InputStreamReader` read File as well. with help of `BufferedReader`. by giving the location of the file.*

```java
class Main{
	public static void main(String[] args)
	{
		// through File.
		BufferedReader br = new BufferedReader(new FileReader("File location")); 
		// through keyboard.		
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
	}
}
```


### Use Cases for Byte Streams:

1. **File I/O with Binary Data:**
    
    - Byte streams are commonly used for reading and writing binary files, such as images, audio, and video files, where the data is represented as raw bytes.
    - Example: Reading and writing image files, audio files, or any other binary files.
2. **Network I/O:**
    
    - Byte streams are used for reading from and writing to network connections, such as sockets, where data is transferred as byte streams.
    - Example: Implementing client-server communication protocols using TCP or UDP sockets.
3. **Serialization:**
    
    - Byte streams are used for object serialization and deserialization, where objects are converted into a stream of bytes for storage or transmission.
    - Example: Saving and loading objects to/from files or sending objects over a network.
4. **Low-level File I/O Operations:**
    
    - Byte streams provide low-level access to files, allowing fine-grained control over file operations, such as reading and writing individual bytes.
    - Example: Reading and writing data from/to specific file positions or manipulating file metadata.

### Use Cases for Character Streams:

1. **Text File I/O:**
    
    - Character streams are commonly used for reading and writing text files, where the data is represented as characters encoded in a specific character set (e.g., UTF-8, ASCII).
    - Example: Reading and writing configuration files, log files, or any other text-based files.
2. **Text Processing:**
    
    - Character streams are used for processing text data, such as parsing, tokenization, or searching, where characters are manipulated at a higher level of abstraction.
    - Example: Implementing text processing tasks like parsing CSV files, XML files, or JSON files.
3. **Character Encoding Conversion:**
    
    - Character streams automatically handle character encoding and decoding, making them suitable for converting text data between different character encodings.
    - Example: Converting text files between different character encodings (e.g., UTF-8 to ISO-8859-1).
4. **Console I/O:**
    
    - Character streams are used for reading input from the console (standard input) and writing output to the console (standard output), allowing interaction with the user via text-based input/output.
    - Example: Reading user input from the console for command-line applications or displaying output messages to the console.




# Class File
- Module [java.base]
- Package [java.io]

Overall, byte streams are more suitable for handling binary data and low-level I/O operations, while character streams are more suitable for handling text data and high-level text processing tasks. The choice between byte streams and character streams depends on the specific requirements of the application and the type of data being processed.

Ah, I see! You're referring to the `File` class provided by Java for file-related operations such as creating, deleting, renaming, or checking the existence of files and directories. Here's how you can use the `File` class for creating, reading, and writing files:

```java
import java.io.File;
import java.io.FileWriter;
import java.io.FileReader;
import java.io.IOException;

public class FileExample {

    public static void main(String[] args) {
        // Create a File object representing a file named "example.txt"
        File file = new File("example.txt");

        try {
            // Create the file if it doesn't exist
            if (file.createNewFile()) {
                System.out.println("File created: " + file.getName());
            } else {
                System.out.println("File already exists.");
            }

            // Write content to the file
            FileWriter writer = new FileWriter(file);
            writer.write("Hello, World!\nThis is a sample text.");
            writer.close();
            System.out.println("Content written to the file.");

            // Read content from the file
            FileReader reader = new FileReader(file);
            int character;
            System.out.println("File content:");
            while ((character = reader.read()) != -1) {
                System.out.print((char) character);
            }
            reader.close();

        } catch (IOException e) {
            System.out.println("An error occurred.");
            e.printStackTrace();
        }
    }
}
```

Explanation:

- We create a `File` object named `file` representing a file named "example.txt" in the current directory.
- We use the `createNewFile()` method to create the file if it doesn't already exist.
- We use a `FileWriter` object to write content to the file using the `write()` method.
- We use a `FileReader` object to read content from the file using the `read()` method.
- We close the writer and reader objects to release system resources properly.
- We handle `IOException` to catch and handle any exceptions that may occur during file operations.

This example demonstrates basic file creation, writing, and reading operations using the `File` class in Java.