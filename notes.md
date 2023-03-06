# Html
# Css
# Javascript
# Typescript
# React
# JAVA

## Java basics

### concepts about the programming language

- Object-Oriented - structured around classes and their objects
- It was developed by James Gosling and his team at Sun Microsystems in the mid-1990s, and is now owned by Oracle Corporation.
- Rich APIs (e.g. Collections API) (Collections)
- Write Once Run Anywhere
    - which means that Java code can be written once and run on any platform that has a Java Virtual Machine (JVM) installed, without the need for recompilation.
- strongly typed(have to declare int, char)
- Automatic garbage collection
    - simplifies memory management, eliminating the need for manual memory allocation and deallocation. 
- verbose
    -lots of lines of code

### compilation process
- The .java file is passed to the javac java compilier from the JDK(Java development kit)
- into Bytecode (.class low level representation of Java code that  can be executed by JVM in any mchine that has JVM)
1. Class-Loader - loads all classes that are used in the program
2. Bytecode verifier - checks that bytecode and makes sure that it doesn't have damaging instructions (ex: using a variable before it's initialized)
3. Just-In-Time Compiler convert bytecode into machine code

![Diagram of Compilation](https://media.geeksforgeeks.org/wp-content/uploads/java.jpg)
### JDK
- Java Development kit
    contains JRE(Java runtime Environment) which then contains the JVM(Java Virtual Machine)
    - JRE: software package that provides the minimum set of resources necessary to run Java applications on a computer system
    - JVM: interpreter that executes Java bytecode

- IDE - Interactive Development Environment
    - IntelliJ (Recommended) - Community edition is fine for our purposes
        - Create associations with .java file
        - Add bin to path
    - Eclipse
### Packages
- Like folders/directories
- We also specify which package each class is in
- Packages help us determine what variables can and can't be accessed

### Main Method
- The starting/entry point for our class
- Key words
    - public - call this method from anywhere in the program
    - static - the method is associated with the class rather than an instance (this is good because we wouldn't to be required to create an instance of this class before we call the main method)
    - void - doesn't return anything
- Parameters
    - String [] args - an array of strings which indicate that arguments that we pass in to our program
        - If we run our program from the command line, we can pass in additional arguments to use in the program
- Body - what runs when we execute the program
    - this can call other methods

``` Java
class HelloWorld{
    public static void main(String args[]){

    }
}
```

### Primitive Types:
- any type that isn't a class
- char - letter/symbol ('a', '2', '$')
- int - whole number
- byte, shorts - whole numbers with a lower range than int
- long - whole number that has a higher range than int
- doubles/floats - a number with decimal places (doubles have more precision than floats)
- boolean - true/false values
- In order from smallest to largets: boolean, byte, short/char, int/float, long/double
- Most commonly used: int, double, boolean, char
    - Sometimes use longs if we want guaranteed larger range

### String
- Declaring String with the new keyword vs the primitive-esque assignment
    - String s = new String("Hello");
        - This is how we normally declare classes
        - This does not leverage the String pool
        - All strings created with the new keyword have their own spot in memory
    - String s = "Hello";
        - String pool
            - A way to save memory by using the same memory locaiton for identical strings
            - If we declare 3 different strings all with the same value (ex: "Hello"), only one instance of that string will be created in the String pool
            - Each of those variables will reference the same exact location
            - Strings are immutable in Java, we can't change the String itself
                - This makes sense because changing the memory would affect all references to that same String
        
![String Pool](https://journaldev.nyc3.digitaloceanspaces.com/2012/11/String-Pool-Java1.png)

### enhanced for loop
- similar to python
``` Java
for (int i: arr){
    //do this
}
```
### Scopes:
- method - a variable that we declare in a method won't be accessible from outside the method
- block scope - a variable declared in a block can't be accessible from outside
    - this is useful with for loops because it lets us redeclare the int i counter for every for loop
- Static/Class scope - method/variable is tied to the class itself. Class variables are initialized automatically to default values when the class is loaded, and they can also be explicitly initialized in a static block.(example: Calculator.PI)
- Instance/Object scope - variables that are attached to the particular instance (example: animal.species)

### Access Modifiers:
- Access modifier is a keyword that we apply to a method, class, variable that indicates where in the program it can be accessed
- public - it can be accessed anywhere in the project (no matter what package it's in)
- private - it can only be accessed within that same class
    - methods can only be called from other methods in that class
    - variables can only be accessed by methods in that class
- default - accessible within the same package
    - The tricky part is that we don't actually declare anything as default
    - "Default" in this case means we don't give an access modifier
- protected - accessible within the same package and sub-classes
    - can apply to methods and variables

### Non-Access Modifiers:
- These are modifiers that don't affect our access to the methods/variable/class
- abstract
    - apply to class to make it possible to have abstract methods
    - apply to method to make that method abstract (we don't need a method body)
    - In Java, an abstract class is a class that cannot be instantiated, meaning that you cannot create an object of the class directly. Instead, an abstract class is intended to be subclassed, meaning that it provides a template for other classes to inherit from.

    ``` Java
    public abstract class Shape {
   public abstract double area();
   public abstract double perimeter();
    }
    ```
- static
    - Scopes the method/variable to the class rather than an instance
        - ex: A calculator class, we could have a static field for PI because PI will not vary depending on which instance we have
        - We use the static keyword on our main methods because we don't actually need an instance of our class to run them
    - We can't call non-static methods or access non-static variables from a static context/method
    - We CAN call static methods and access static variables from a non-static/instance method
- final
    - 3 different contexts:
        - If we apply it to a variable, it means we can't reassign it
            - If we have an object declared as final, we can reassign the fields
        - If we apply it to a method, we can't override it
        - If we apply it to a class, we can't extend it

### This keyword:
- We use the "this" keyword in our methods to indicate that we want this particular instance's field or method
```java
class Animal {
    String name;

    
    public Animal(String nameInput) {
        // the "this" keyword denotes that we want to access the instance's name field rather than the parameter that we passed in:
        this.name = nameInput;
    }
}

```
## SUper
- "super" is a keyword that is used to refer to the parent class of a subclass. 

``` Java
public class Car extends Vehicle {
   private int numWheels;
   
   public Car(String make, String model, int numWheels) {
      super(make, model); // call parent constructor
      this.numWheels = numWheels;
   }
}

```
### == vs .equals()
- The "==" operator compares the reference identity of two objects, meaning that it checks whether the two variables point to the same object in memory.
- On the other hand, the ".equals()" method compares the content equality of two objects, meaning that it checks whether the two variables have the same value or state.

### arrays 
``` Java
        // Arrays in Java are statically-sized:
        // meaning we can't change the size and we can't push new elements on
//        arr.length = 6;
//        arr.push("New Word");

        // we can instnaitate an array like this
        int [] numbers = {1,2,3,4,5};

        // instantiate a new array of size 10 with all empty slots:
        boolean[] booleans = new boolean[10];
        booleans[5] = true;
        for(int i = 0; i < booleans.length; i ++) {
            System.out.println(booleans[i]);
        }
```

## OOP

### Abstraction
- Hiding the details of our implementation
- For example, we define the expected output/input/general behavior in a parent class but leave the specific implementation up to a child class
- In Java, we can achieve abstraction in 2 ways:
    - Abstract class
        - concrete methods have a body and actual code
        - Can have concrete and abstract methods
        - You can't have abstract methods in a concrete class
        - If we extend an abstract class, we either have to declare it as abstract or fill out the methods
        - We cannot instantiate an abstract class
        - IntelliJ shortcut: Right-Click + Generate + Implement Methods + Select methods that you want to override (taken from the parent class)
    - Interface
        - An interface is totally abstract (no concrete methods*)
            - Exceptions are default and static methods
        - An interface only has abstract methods and must be *implemented* instead of extended
- Example:
    - Shape has abstract area method which is filled out in child classes

### Encapsulation
- We take properties/methods and "encapsulate' them into one related class, or one unit
- For example, making a car class with properties (speed, color, milage)
- Hiding our members using access modifiers
    - Example: making our variables private and using public getters/setters to access them
        - Gives us more control to the underlying data

### Inheritance
- Parent-child relationships
- We've seen this with the Object class in that every class in Java inherits from that class meaning it has all of the parent's methods and fields
- If a child extends a parent class, it will have access to all of the fields and methods that the parent can have
    - We can change how the methods work in the child (Overriding), we can also add new methods and fields
- Open for extension, closed for modification
- Animal -> Mammal -> Cat/Dog
- ![Inheritance](https://img.brainkart.com/imagebk37/yhYyQsQ.jpg)

#### Types of Inheritance
- Single - Class A inherits from B
- Multilevel - Class A inherits from B which inherits from C, etc.
- Hierarchical Inheritance - one parent can have as many children as they want
- Multiple Inheritance (NOT ALLOWED IN JAVA*) - one class extending many parents
- Hybrid (NOT ALLOWED IN JAVA) - combination of multiple and hierarchical
- Key Takeaway: One class cannot inherit multiple parents
- The exception to the Multiple and Hybrid rules is that we can implement multiple interfaces
    - We just have to implement all abstract methods we get from every interface (unless the class that's implementing is abstract)
    - See Flying Fish Example (Tuesday.OOP.Inheritance.interfaces)

### Polymorphism
#### Run-Time (Dynamic) Polymorphism
- Overriding - overriding what the parent method defined with the child implementation

```Java
class Animal {
    public void makeSound() {
        System.out.println("Some sound");
    }
}

class Cat extends Animal {
    @Override
    public void makeSound() {
        System.out.println("Meow");
    }
}
```
- For a given class, we can only override a method once
- Inheritance and overriding
- When we override a method from a parent class, this is an example of polymorphism
- poly - many
- morphism - forms
- Same method signature (same name, same parameter, return types)
    - But in the sub-class we change the body of the method
#### Compile-Time (Static) Polymorphism
- Overloading
    - different number of parameters
    - different types of parameters
    - different order of parameters
    - key takeaway: as long as two methods don't have the exact same sequence of parameter types, it's a "valid" overload
- 2 or more methods with similar declaration (same name, but different parameters)
- We can overload a method as many times as we want, as long as we keep giving different parameters

```Java

public class OverloadingExample {
    public static int add(int a, int b) {
        return a + b;
    }
    
    public static double add(double a, double b) {
        return a + b;
    }
```

## Streams
``` Java
// mapping them to the squares of the original number and then returning a list
        List<Integer> squares = numbers.stream().map(x -> x * x).collect(Collectors.toList());
        System.out.println("Squares:" + squares);

        // filter and keep the evens and then sort:
        List<Integer> evens = numbers.stream().filter(x -> x % 2 == 0).sorted().collect(Collectors.toList());
        System.out.println("Even: " + evens);

        evens.stream().forEach(val -> {
            System.out.println("This is the forEach: " + val);
        });

        //                     start at 0, at each step, we add 1 to accumulated value:
        int numEven = evens.stream().reduce(0, (ans, current) -> ans + 1);
        System.out.println("Number of even numbers: " + numEven);


        int sumEven = evens.stream().reduce(0, (accumulator, current) -> accumulator + current);
        System.out.println("Sum of all even numbers:" + sumEven);

        int productEven = evens.stream().reduce(1, (accumulator, current) -> accumulator * current);
        System.out.println("Product of all even numbers:" + productEven);


        List<Integer> cubed = numbers.stream().map((x) -> x * x * x).collect(Collectors.toList());
        System.out.println(cubed);
```

## COllections

- Arraylist vs linked list
``` Java
// ArrayList is an implementation of the List interface
        // pass in the type that we want to store in the <>:
        List<String> names = new ArrayList<>();
        List<String> names2 = new LinkedList<>();

        names.add("Rory");

        // .iterator returns an iterator that points to the list:
        Iterator<String> iterator = names2.iterator();
        // .hasNext tells us if there is another element that the iterator points to:
        while(iterator.hasNext()){
            // .next advances the iterator and returns that next value:
            String name = iterator.next();
            System.out.println(name);
        }
```

## Generics

- Generics allow you to define a class, interface, or method that operates on a parameterized type. By using generics, you can create reusable code that can work with different types of objects without having to write the same code multiple times for each type.

```Java
public class Box<T> {
    private T contents;

    public void set(T contents) {
        this.contents = contents;
    }

    public T get() {
        return contents;
    }
}

```
```Java
Box<String> stringBox = new Box<>();
stringBox.set("hello");
String str = stringBox.get();

Box<Integer> intBox = new Box<>();
intBox.set(42);
int i = intBox.get();

```
- useful for lots of types

## Java 8

### Lambda expressions
- parameter -> expression
    - takes in a single value and returns a single expression
- (parameter1, parameter2) -> expression
    - takes in multiple parameters and returns an expression
- (parameter1, parameter2) -> {code}
    - takes in multiple parameters and executes some code
``` Java
names.forEach(name -> System.out.println("Hello, " + name));
```

### Functional interface
- defined a functional interface named Calculator that takes two int parameters and returns an int value.  this interface is intended to be used as a functional interface, which means it should have exactly one abstract method.

```Java

public interface Calculator {
    int calculate(int a, int b);
}

```

```Java
Calculator adder = (a, b) -> a + b;
Calculator subtractor = (a, b) -> a - b;

int sum = adder.calculate(2, 3); // sum = 5
int difference = subtractor.calculate(5, 2); // difference = 3

```
- We can use these to store lambda expressions
    - When we write lambda expression, we want to adhere to the method signature of the FI

- Built-In Functional Interfaces:
    - Consumer - takes in a value and doesn't return anything
        - ex: take in a string and print it out
    - Predicate - takes in a value and returns a boolean
        - ex: takes in a number and returns even/odd
    - Function - takes in a value and returns a value
        - square/cube function that takes in an integer and returns an integer squared/cubed
    - Supplier - doesn't take in a value but does return a value
        - ex: returns a random number
    - Bi-Versions -  
        - BiConsumer takes in 2 values
        - BiPredicate takes in 2 values
        - BiFunction takes in 2 values

## Error handling

- error vs exception
    - we can handle exceptions

``` Java
try {
            // because this constructor tries to create a file reader based on a file that might
            // not even exist, we have to handle the checked exception (FileNotFound) before we can run the program
            FileReader file = new FileReader("tst.txt");
            System.out.println("File found");
            System.out.println(numbers[100]);
        }
        catch(FileNotFoundException exception) {
            System.out.println("File doesn't exist :(");
        }
```
- throw

``` Java
    // if we make this helper throw an exception, that is propogated to where the
    // method is being called from
    public static void helper() throws FileNotFoundException{
        FileReader file = new FileReader("test.txt");
    }
```

## Design patterns

- Singleton pattern - ensures that only one instance of a class is created and provides a global point of access to it.
- Factory pattern - provides a way to create objects without exposing the creation logic to the client and refers to the newly created object through a common interface.

## Maven

- Build automation tool
    - helps us build our projects, incorporating all of the dependencies we needs (such as JUnit)
    - We use it for JDBC (Java Database Connectivity) as well

### POM - Project Object Model
- Contains metadata like name, version, etc.
- A list of dependencies or external libraries that we're working with
- Whenever we want to add a new dependency, we just update the pom.xml and sync the project
    - In IntelliJ, we should see a blue circle icon to sync

### JUnit
- a framework in Java that lets us write unit tests for our code
- testing our program in the smallest increments/pieces as possible
- In Java we usually write unit tests that test a particular method
    - Given some input, make sure it returns the correct output
- JUnit is an external dependency, we can't access it without first installing it

### Annotations (Jupiter Annotations)
- @Test - we use it to annotate methods, indicating that the method is testing something (usually a method from main directory)
- @BeforeAll - we use it on a static method, to indicate that it should run before all the tests in that class are run
    - We can use this to do any set up we need at the beginning of all testing methods of that particular class
- @BeforeEach - we annotate a non-static method to indicate that this method should run before every test
    - initialization before each test (ex: maybe resetting a value)
- @AfterAll - clean up after all tests are run
- @AfterEach - clean up after each individual test

### Junit vs Jupiter
- Instead of BeforeEach, we get Before in JUnit
- Instead of BeforeAll, we get BeforeClass in JUnit
- In JUnit we can use Assert.assertEquals (or any of the assert methods)

### Testing Methods
- assertEquals - ensure that 2 values are equal, otherwise the test fails
- assertTrue - ensures that the value returns true
- assertArrayEquals - ensures that 2 arrays have the same length and the same values
- https://junit.org/junit5/docs/5.0.1/api/org/junit/jupiter/api/Assertions.html

``` Java
public class CounterTest {
    // set up a Counter object that we can use in our tests
    static Counter counter;

    @BeforeClass
    public static void setUp() {
        // only initialize the counter once
        counter = new Counter();

    }

    @Before
    public void init() {
        // reset the counter back to 0:
        counter.reset();
    }

    @After
    public void cleanUp() {
        System.out.println("Clean up");

    }

    @AfterClass
    public static void cleanUpClass() {
        System.out.println("Clean up after class");

    }

    @Test
    public void testGetValue() {
        // assert just takes in a boolean and asserts that it's true
        Assert.assertEquals(0, counter.getValue());
    }

```
### Test-Driven Development (TDD)
- Writing tests before we write our code
- Benefits
    - Helps us write good code
        - Identify edge cases
        - Helps to point out awkward method declarations
        - Identify areas to improve
    - Nice workflow and lets us see tangible progress as we fill out our methods

### Testing Scenarios
- When applicable, we want to test both the positive case and negative case
    - ex: we have a method that returns whether a value is even or odd
        - We would want at least 2 tests to test the positive and negative case
    - Code Coverage - a measure of which lines of your code are being run when you test
        - let's say we have an if/else statement, we would want to make sure we have test cases that cover both possible scenarios in order to get the most coverage
        - IntelliJ lets you see coverage by right-click and run tests with coverage
        - Testing a folder/package will test everything in that folder
            - We can also just test a class
            - We can also just test a method
- When testing methods that accept some sort of collection of data
    - empty collection
    - collection with exactly 1 element
    - collection with 2 or more