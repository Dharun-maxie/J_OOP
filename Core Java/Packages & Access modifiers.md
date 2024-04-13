
`packages` is term that contain more than one file that is called `package`. `java` is come with some inbuild `packages` as well.

*Very common `package` is `lang` & `util` that come with every `java` machine*
```java
import java.lang.*;
```

```java
import java.util.*;
```

*The asterisk(\*) is used to mention all `class` in the `package`*

*Ok. Lets create an package for our classes*

### Packages

```java
// Employee.java
package com.company;

public class Employee {
    protected String name;
    protected double salary;

    public Employee(String name, double salary) {
        this.name = name;
        this.salary = salary;
    }

    public void display() {
        System.out.println("Name: " + name);
        System.out.println("Salary: " + salary);
    }
}

```

```java
// Manager.java
package com.company;

public class Manager extends Employee {
    private String department;

    public Manager(String name, double salary, String department) {
        super(name, salary);
        this.department = department;
    }

    public void display() {
        super.display();
        System.out.println("Department: " + department);
    }
}

```

### Access Modifiers

- `Employee` class has `protected` access for its `name` and `salary` fields. This means they are accessible within the same package and by subclasses.
- `Manager` class inherits from `Employee` and accesses its `name` and `salary` fields using the `protected` access modifier.
- `display()` method in both classes has default (package-private) access.

```java
// MainProgram.java
package com.company;

public class MainProgram {
    public static void main(String[] args) {
        Employee employee = new Employee("John Doe", 50000);
        Manager manager = new Manager("Jane Smith", 70000, "Sales");

        employee.display();
        System.out.println("---------------------");
        manager.display();
    }
}

```

### Explanation

- Both `Employee` and `Manager` classes belong to the `com.company` package.
- `Manager` class extends `Employee` and inherits its `name` and `salary` fields, thanks to the `protected` access modifier.
- The `display()` method in both classes can access the `name` and `salary` fields due to the `protected` access modifier.
- The `main()` method in the `MainProgram` class can access both `Employee` and `Manager` classes since they are in the same package.


#VeryImportantNote
### Access Modifier Cheat Sheet

|                                      | Private | Protected | Public | Default |
| ------------------------------------ | ------- | --------- | ------ | ------- |
| Same class                           | Yes     | Yes       | Yes    | Yes     |
| Same package<br>subclass             | NO      | Yes       | Yes    | Yes     |
| Same package<br>non-subclass         | NO      | Yes       | Yes    | Yes     |
| Different package NO<br>subclass     | NO      | Yes       | Yes    | NO      |
| Different package NO<br>non-subclass | NO      | NO        | Yes    | NO      |
