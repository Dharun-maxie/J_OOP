*`Enumeration` or `enum` are Named constants.*

*Lets create an `Threads.Main class`*

```java 
enum status
{
	Running, Failed, Pending, Success;
}

class Threads.Main
{
	public static void main(String[] args)
	{
		status s= status.Running;
		
		System.out.println("Output:");		
		System.out.println(s);
		System.out.println(s.ordinal());
		
		swich(s)
		{
			case Running:
				System.out.println("All Good.");
				break;
			case Failed:
				System.out.println("Try Again.");
				break;
			case Pending:
				System.out.println("Wait.");
				break;
			default:
				System.out.println("Done...");
				break;
		}
	}
}
```

```java
Output: 
Running
0
```

**We can also use Switch case with `enum`**

#VeryImportantNote 
- **`ENUM` is type `class` and the variables inside the `enum class` are objects.**
- **even if `Enum` is type class we can not extends to another `class`.**
- **since `enum` is a `class` we can use functionality of `class` as well. like having an constructor, Methods and variables.**
- **`enum class` extends `Enum class`.**

```java
// Enum class with custom constructor, default constructor, and private variables
enum Direction {
    NORTH("N"), SOUTH("S"), EAST("E"), WEST("W");
    
    private String abbreviation;
    
    private Direction(String abbreviation) {
        this.abbreviation = abbreviation;
    }
    
    private Direction() {
        this.abbreviation = "N/A";
    }
    
    public String getAbbreviation() {
        return abbreviation;
    }
}

public class Threads.Main {
    public static void main(String[] args) {
        Direction north = Direction.NORTH;
        System.out.println("Abbreviation for NORTH: " + north.getAbbreviation());
        
        Direction defaultDirection = Direction.WEST; 
        System.out.println("Abbreviation for " + defaultDirection + ": " + defaultDirection.getAbbreviation());
    }
}

```

#Example

Enums are used in various scenarios where you have a fixed set of constant values representing some predefined choices. Here's another example of using enums in a scenario where we model different types of coffee drinks:

```java
enum CoffeeType {
    ESPRESSO, AMERICANO, LATTE, CAPPUCCINO
}

// Class representing a coffee order
class CoffeeOrder {
    private CoffeeType type;
    private int size; // In ounces

    // Constructor
    public CoffeeOrder(CoffeeType type, int size) {
        this.type = type;
        this.size = size;
    }

    // Getter methods
    public CoffeeType getType() {
        return type;
    }

    public int getSize() {
        return size;
    }

    // Method to prepare the coffee
    public void prepare() {
        System.out.println("Preparing a " + size + "oz " + type + "...");
        // Logic to prepare the coffee based on its type
    }
}

// Threads.Main class
public class CoffeeShop {
    public static void main(String[] args) {
        // Creating coffee orders
        CoffeeOrder order1 = new CoffeeOrder(CoffeeType.ESPRESSO, 2);
        CoffeeOrder order2 = new CoffeeOrder(CoffeeType.LATTE, 12);

        // Displaying order details
        System.out.println("Order 1: " + order1.getType() + ", Size: " + order1.getSize() + "oz");
        System.out.println("Order 2: " + order2.getType() + ", Size: " + order2.getSize() + "oz");

        // Preparing orders
        order1.prepare();
        order2.prepare();
    }
}
```

In this example:

- The `CoffeeType` enum class defines different types of coffee drinks.
- The `CoffeeOrder` class represents an order for a coffee drink, with properties such as type and size.
- The `CoffeeShop` class contains the `main` method where we create instances of `CoffeeOrder` using different types of coffee drinks from the `CoffeeType` enum.
- We then display the details of each order and simulate preparing the coffee orders, which can involve different preparation steps based on the type of coffee drink.