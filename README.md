
# **KOTLIN**
- [Example of Java Code Vs Kotlin Code](#example-of-java-code-vs-kotlin-code)
- [Kotlin Java Working Together](#kotlin-java-working-together)

### Why Kotlin Over Java?
It is a statically typed programming language for modern multi-platform applications like Web, Android and Enterprise applications. It works over JVM and thus is platform-independent.
It has the following advantages over Java:
1. Concise
2. Safe
3. Interoperable
4. Tool-friendly


### Example of Java Code Vs Kotlin Code
```
// Java Code
public class Main {
	public static void main(String[] args) {
		System.out.println("Hello World");
	}
}
```
```
// Kotlin Code
fun main(args : Array<String>) {
	println("Hello World");
}
```
-----------------------------------------------------------------------------------------
In Java, **constants** are declared with **final** keyword, while in Kotlin, **constants** are declared with **val** keyword. Similarly, **variables** in java are defined with specific type, while in Kotlin, we use **var** keyword.
```
// Java Code
public class Student {
	public String name = "";
}
```
```
// Kotlin Code
class Student {
	var name : String = "";
}
```
-----------------------------------------------------------------------------------------
In Kotlin, creating an instance of a class does not need the **new** keyword.
```
var std1 = Student(); 	// → Student std1 = new Student();
std1.name = "Ashish"; 	// → std1.name = "Ashish";
println(std1.name); 	// → System.out.println(std1.name)
```
-----------------------------------------------------------------------------------------  
Kotlin also supports **${}** syntax to print statement. This makes the representation of print statement much more simpler and easy to read for the other users as **concatenation** takes a lot of space.
```
System.out.println("This " + college + " has a good reputation");	// → Java	| 
println("This " + college + "has a good reputation"); 				// → Kotlin | Traditional way
println("This_ _**${**__college__**}**_ _has a good reputation"); 	// → Kotlin | Modern way
```
-----------------------------------------------------------------------------------------

### Kotlin Java Working Together

Unlike other languages, we do not need any interface when working with Kotlin and Java. They are easily compatible with each other. Hence, we can run java class while working with Kotlin application and vice-versa.

By default, in editors, when a private variable is declared, we can use the **generators** to create their setters/getters. In case of private variables in a class, the Kotlin uses this property and syntax to access these **getters/setters** via private variable name by default. If the **getters/setters** are not editor generated syntax then it is better to use traditional way as in **Java**.

-----------------------------------------------------------------------------------------
```
// Teacher.java
public class Teacher{  
	private String name;
	
	public Teacher(String name) {
		this.name = name;
	}
	public String getName() {  
		return name;  
	}  
	public void setName(String name) {  
		this.name = name;  
	}
}
```
In Kotlin, the above class would look like this
```
class Teacher(var name : String)
```
which is **far less code** than traditional way, as it uses **default getters and setters** for the variable in the instance.


The below code shows the usage of default getters and setters in Kotlin code of the above Java Code.
```
// Main.kt
fun main(args : Array<String>) {
	var teacher = Teacher("Ashish"); 	// → Teacher teacher = new Teacher("Ashish");
	println(teacher.name); 				// → sout(teacher.getName());
	// output → "Ashish"

	teacher.name = "Ashish Hattimare"; 	// → teacher.setName("Ashish Hattimare");
	println(teacher.name); 				// → sout(teacher.getName());
	// output → "Ashish Hattimare"
}
```
-----------------------------------------------------------------------------------------
```
var num1 : Int = 3; 		// Java Code → int num1 = 3;
var str1 : String = "Ashi";	// Java Code → String str1 = "Ashish";
```
-----------------------------------------------------------------------------------------

### Condition Statement

Unlike in Java, Kotlin treats conditional statements as expression (also statements);  
```
// Java Code
{
	int num1 = 5, num2 = 7;
	int result = 0;
	
	if(num1 < num2) result = num2;
	else result = num1;
}
```
```
// Kotlin Code

var num1 : Int = 5, num2 : Int = 7;
var result : Int = 0;

// Traditional Way
{
	if(num1 < num2) result = num2;
	else result = num1;
}

// Modern Way → Expression Condition (else conditon is mandatory)
{
	result = 	if(num1 < num2) num2
				else num1
}
```
-----------------------------------------------------------------------------------------

### Null Handling

By default, the Kotlin does not support null assigning to a variables.
```
var str1 : String = null; // → this is not valid as null cannot be assigned to non-null type String
```
Thus, in order to make the code assign null, we have
```
var str1 : String? = null; // → this is a valid statement in Kotlin (safe keyword - ?)
```

The below code displays an example of how **safe?** can be used in Kotlin
```
// Student.kt
class Student {
	var name : String? = null;
}
```
```
// Main.kt
fun main(args : Array<String>) {
	
	var std = Student();
	println(std.name); 			// → null, but it can be "Ashish" as well
	println(std.name.length); 	// ERROR, because "name" variable is of type "can-be null"
	
	println(std.name?.length); 	// Valid statement. We must use ? keyword if the type is "can-be null"

	// everywhere the variable is used (replaced with "safe")
}
```
Similar to defined types, we can use **?** With user-defined Objects as well in Kotlin.
```
{
	var std1 : Student = Student(); // → valid statements 	(1)
	std1 = null; 					// → invalid statement 	(2)
}
```
In order to make the statement (2) valid, we need to provide **'\<ClassName\>?'** to the statement (1)
```
{
	var std1 : Student? = Student();// → valid statement 	(1)
	std1 = null; 					// → valid statement 	(2)
}
```
-----------------------------------------------------------------------------------------

### Switch and When Expression

In Kotlin, we do not support **switch** statement. Instead, we make use of **when** statement, which works similarly to the switch statement **without break statement**.
```
// Java Code

{
	int num = 3;
	switch(num) {
		case 1 : sout("First");
				 break;
		case 3 : sout("Third");
				 break;
		
		default: sout("None");
	}
}
```
```
// Kotlin Code
{
	var num : Int = 3;

	when(num) {
		1 → { println("First") }
		3 → { println("Third") }
		
		else → { println("None") } // Mandatory Condition unlike Default in switch
	}
}
```
**when** statement also behaves like **if** conditions **(Both provide expression feature)**

-----------------------------------------------------------------------------------------

### Loops and Range

In Kotlin, the **while** and **do-while** loops works in the same way as in Java.

The difference is with the **for-loop**
```
1. var nums = 1 .. 16; 		// → [1, 16]
2. var nums = 1 until 16; 	// → [1, 16)
```
```
// Java Code
{
	for (int i = 0; i <=  13; i+=2) {	// from 0 -> 13
		System.out.println(i);
	}// → [0, 2, 4, 6, 8, 10, 12]

	for (int i = 13; i >= 0; i-=2) {	// from 13 -> 0
		System.out.println(i);
	}// → [13, 11, 9, 7, 5, 3, 1]
}
```
```
// Kotlin Code
{
	var ascRange = 0..13
	for (i in ascRange step 2) { // step 1 is by-default
		println(i);
	}// → [0, 2, 4, 6, 8, 10, 12]

	var desRange = 13 downTo 0; // → same as 13.downTo(0) as downTo is a infix method of Int
	for (i in desRange step 2) {
		println(i)
	}// → [13, 11, 9, 7, 5, 3, 1]
}
```
-----------------------------------------------------------------------------------------

### Lists and Map

In Java, we have different **Collections API** such as List, Stack, Queue, Priority Queue, HashMap and so on.

**LISTS**
```
// Java Code
{
	List<Integer> nums = Arrays.asList(1,2,3,4,5);

	for (int x : nums) { // → get all the elements of the list
		sout(x);
	}
	
	// element with index
	for (int i = 0; i < nums.size(); i++) {
		sout(i + " : " + nums.get(i));
	}
}
```
```
// Kotlin Code 
{
	var nums = listOf(1,2,3,4,5);

	for (x in nums) { // → get all the elements of the list
		println(x);
	}

	// element with index
	for ((index, element) in nums.withIndex()) {
		println("${index} : ${element}");
	}
}
```

**MAPS**
```
// Java Code
{
	Map<String, Integer> map = new HashMap<>(); // → HashMap in Java
	maps.put("Ashish", 1997);
	maps.put("Amit", 1994);
}

```
```
// Kotlin Code 
{
	var map = HashMap<String,Int>();// → HashMap in Kotlin
	map["Ashish"] = 1997; 			// → Insertion in Map like in C++ using []
	map["Amit"] = 1994;

	for((name, year) in map) { 		// → Iterate map using in operator, like Lists
		println("${name} = ${year}");
	}
}
```
-----------------------------------------------------------------------------------------

### Function Expression

In Kotlin, we use **fun** keyword to declare functions/methods.
In Kotlin, by default the functions are **static/global** in _Kotlin file_
```
fun add(a : Int, b : Int) { // → public void add(int a, int b) {}
	println("${a} + ${b} = ${a+b}");
}

fun add(a : Int, b : Int) : **Any?** { // → public int add(int a, int b) {}
	return a + b;
}

// Inline Function
fun add(a : Int, b : Int) : Any = a + b;
```
-----------------------------------------------------------------------------------------

### Calling Kotlin Code From Java
```
// Kotlin Code : Main.kt

fun main(args : Array<String>) {
	var result = add(2, 4);
}

fun add(a : Int, b : Int) : Any? = a + b; 	// → Static function Main.kt file
fun max(a : Int, b : Int) : Int{ 			// → Static function Main.kt file
	return (a > b) ? a : b;
}
-----------------------------------------------------------------------------------------

// Kotlin Code : Operation.kt

class Operation {
	fun multiply(a : Int, b : Int) : Int { 	// → Instance method of Operation.kt Class
		return a * b; // cannot be null
	}
}

fun minus(a : Int, b : Int) : Int? { 		// → Static method of Operation.kt file  
	return a – b; // can be null  
}
-----------------------------------------------------------------------------------------

// MainFunction.java

public class MainFunction {
	public static void main(String[] args) {
		
		sout(MainKt.add(4, 3)); // → 7 | STATIC METHOD
		sout(MainKt.max(3,1)); 	// → 3 | STATIC METHOD
		
		sout(Operation().multiply(4,3));// → 12 | INSTANCE METHOD
		sout(OperationKt.minus(3,4)); 	// → -1 | STATIC METHOD
	}
}
```

By default, when the Kotlin code compiles, if the class name is **Operation.kt**, then the **OperationKt.class** is generated by the JVM. If we want to override this naming, then we should put **@file:JvmName("\<Class_Name\>")** at the top of the .kt file to create **\<Class_Name\>.class** file at compile time for this file.

-----------------------------------------------------------------------------------------

### Default Parameter and Named Parameter

Sometimes, we want to use the default parameters to methods (like we do in C++). In Java, this is not possible.
```
// Kotlin Code : Main.kt

fun main(args : Array<String>) {

	var amount1 = calcAmount(50, 0.02); // interest = 0.02
	println(amount1);					// amount = 51

	var amount2 = calcAmount(50); 		// interest = 0.04 (**default parameter**)
	println(amount2); 					// amount = 52
}

// Use of default parameter in interest variable
fun calcAmount(amount : Int, interest : Double = 0.04) : Int {
	return (amount + amount*interest).toInt();
}
```

This works fine in Kotlin via **default parameter** property. But, In Java, this would not work. It should have two method of **calcAmount** in Main.kt for java to call these functions separately, like in Kotlin.

For this, we use the keyword **@JvmOverloads** at the top of the **default parameter function** to specify the JVM to create multiple methods of it, to perform that functionlity.

Hence, the calcAmount method looks like this:
```
@JvmOverloads
fun calcAmount(amount : Int, interest : Double = 0.04) : Int {
	return (amount + amount*interest).toInt();
}
```
-----------------------------------------------------------------------------------------

**Named Parameter :** Sometimes, when the user reads his code, it is hard for him to identify for what purpose the parameters are used and what do each parameter signify, especially when the parameter is a constant value.

Hence, Kotlin uses named parameter feature for the user to help in this scenario. **ONLY WORKS IN KOTLIN**
```
var amount1 = calcAmount(amount = 50, interest = 0.05);
var amount1 = calcAmount(interest = 0.05, amount = 50); // With named parameters, both are same_
```
Here, the "amount" and "interest" keyword in the calcAmount calling method are **Named Parameters**.

-----------------------------------------------------------------------------------------

### Exceptions Handling

In Kotlin, Try/Catch is also an expression
```
try {
	// statements
} catch(ignored : Exception) {}
```
-----------------------------------------------------------------------------------------

### Extension Functions  

Sometimes, we do not have the access to a class to make modification to it. In those cases, it is hard to make changes to the code and difficult as well. Hence, Kotlin provides the **extension functions** which are used as external functions to a class.
```
// Kotlin Code : Student.kt

class Student(var course : String) {}
```
Student class has no **plus function** inside it
```
// Kotlin Code : Main.kt

fun main(args : Array<String>) {

	var s1 = Student("Java"); // → course : Java
	var s2 = Student("SQL"); // → course : SQL
	var s3 = s1.plus(s2); // →course : "SQL Java"
}

// Extension Function
fun Student.plus(other : Student) : Student {
	var tempStudent = Student(other.course + " " + this.course);
	return tempStudent;
}
```
-----------------------------------------------------------------------------------------

### Infix Functions

Sometimes, you may write the function calling more like English Language.

For example,
```
for (i in 16 downTo 0) println(i)
```

Here, **in** and **downTo** operator are infix functions. Infix functions only take one argument.

In the last example for extension function,

To make a function an **infix function**, we need to put "**infix**" at the beginning of the function.

-----------------------------------------------------------------------------------------

### Operator Overloading Functions

We can also use the unary operation like +, -, ++ and their functions as we do in C++ operator overloading. There are specific function for each operator overloading.

To make a function an **overloading function**, we need to put "**operator**" at the beginning of the function.

For example,

**Expression Translated to**
- a + b a.plus(b)
- a – b a.minus(b)
- a / b a.div(b)
 
```
var s3 = s2.plus(s1);	// → it can be written as infix functions.
var s3 = s2 plus s1; 	// → Infix functions – plus()

var s4 = s2 + s1; 		// → operator overloading
```
```
operator infix fun Student.plus(other : Student) : Student
{
	var tempStudent = Student(other.course + " " + this.course);
	return tempStudent;
}
```
**BOTH INFIX AND OPERATOR OVERLOADING FUNCTION**

-----------------------------------------------------------------------------------------

### Constructors
```
fun main(args : Array<String>) {

	var stud1 : Student = Student("Ashish");
	stud1.think();
	// → New Object Created
	// → Hello Ashish! Your age is 0

	var stud2 : Student = Student("Ashish Gopal", 45);
	stud2.think();
	// → New Object Created
	// → Constructor calling
	// → Hello Ashish Gopal! Your age is 45
}
```
```
class Student(var name : String) // → Primary Constructor
{
	var age : Int = 0; // → default value
	
	// → Constructor overloading
	constructor(name : String , age : Int) : this(name) { // → Primary Constructor call needed
		this.age = age;
		printfln("Constuctor calling");
	}
	
	// → when we call the constructor of this object, the constructor calls this init block
	init {
		println("New Object Created");
	}
	
	fun think() {
		println("Hello ${name}! your age is ${age}");
	}
}
```
-----------------------------------------------------------------------------------------

### InHeritance

Same rules as Java are applied here. **No Multiple Inheritance** as well.

To stop other from extending your class, we use the keyword **final** on the class. By default, the Kotlin makes use of this property, and does not allow the direct inheritance in Kotlin programming. You should explicitly indicate in the code, that the class should be extended by other class.

  

By default, the classes are **final** in Kotlin

// → class Student **is same as** final class Human

  

Besides this, we need to explicitly make the use of **override** and **open** keyword for a class to inherit other super class methods. This is useful as you restrict other class to simply make use of these functionality, when **permission not provided**.

```
// Kotlin Code : Human.kt

open class Human // → Open to be extended by other classes  
{
	var myname : String = "";  
	constructor(name : String) {  
		myname = "<" + name + ">";  
		println("Human Constructor");  
	}
	
	init {  
		println("Human Init");  
	}
	
	open fun think() {  
		println("Human : ${myname} is thinking..");
	}  
}  
```
```
// Kotlin Code : Student.kt

final class Student(var name : String) : Human(name) 		// → Primary Constructor
{  
	var age : Int = 0;  
	constructor(name : String, age : Int) : this(name) {	// → call the Primary Constructor
		println("Student Constructor");  
		this.age = age; 
	}

	init {  
		println("Student Init");  
	}

	override fun think() {  
		println("Hello ${myname}, your age is ${age}");  
	}
	
	fun print() {
		println("My name is ${myname}");
	}  
}
```
```
// Kotlin Code : Main.kt

fun main(args : Array<String>) {
	var hum = Human("Sonali")  
	hum.think()  
	_println_("===================================")  
	var stud : Student = Student("Ashish GH", 12);  
	stud.think()  
	stud.print()
}
```
Ouput to the above code is as follow:
```
Human Init
Human Constructor
Human : <Sonali> is thinking..
===================================
Human Init
Human Constructor
Student Init
Student Constructor
Hello <Ashish GH>, your age is 12
My name is <Ashish GH>
```
-----------------------------------------------------------------------------------------

### Data Class

For the developers, the need of **toString()**, **hashCode()**, and **equals()** is always needed to check whether the two objects have same data or not.

In Java, we are required to override these following methods to get the desired data. The developers of Kotlin realised it as it is always needed with every class. Also, in C++.

Thus, the Kotlin provides this functionality by making the class as **data class \<ClassName\>**.

```
// Kotlin Code : Laptop1.kt

class Laptop1(var brand : String, var price : Int)  
{
	override fun toString(): String {
		return "${brand} ${price}";
	}
	fun equals(other: Laptop1): Boolean {
		return this.brand.equals(other.brand) && this.price.equals(other.price);
	}
	fun copy() : Laptop1 {
		return Laptop1(this.brand, this.price);
	}
}
```
```
// Kotlin Code : Laptop2.kt

data class Laptop2(var brand : String, var price : Int);  
```
```
// Kotlin Code : Main.kt

fun main(args : Array<String>) {

	var lap1 = Laptop1("Asus", 2000);
	var lap2 = Laptop1("Asus", 2000);
	
	var lap3 = lap1.copy();
	lap3.brand = "Apple";
	
	println(lap1); println(lap1); println(lap3);
	println(lap1.equals(lap2));
	println(lap1.equals(lap3));
	println("===================================");
	
	var lap4 = Laptop2("Asus", 2000);
	var lap5 = Laptop2("Asus", 2000);
	
	var lap6 = lap4.copy();
	lap6.brand = "Apple";
	  
	println(lap4); println(lap5); println(lap6);  
	println(lap4.equals(lap5));
	println(lap4.equals(lap6)); 
}
```
Ouput to the above code is as follow:
```
Asus 2000
Asus 2000
Apple 2000
true
false
===================================
Laptop2(brand=Asus, price=2000)
Laptop2(brand=Asus, price=2000)
Laptop2(brand=Apple, price=2000)
true
false
```

Laptop1 and Laptop2 are both designed to work the same. The Laptop1 class is written in Java terms where the user is required to override and implement the **toString(), equals** and **copy()** functions.

The Kotlin provides the same functionality by adding **‘data’** keyword at the front of class. And it saves a lot of time for the developers to focus on the other content, than on the commonly needed functions.

-----------------------------------------------------------------------------------------

### Object Keyword (Singleton Object)

How can we create Singleton Object in Kotlin? Keyword : **object \<ClassName\>**
It defines that there would be no multiple object of this class.
```
// Kotlin Code : Book.kt

data class Book(val name : String, var price : Int);
	object Shelf {
	var bookList = arrayListOf<Book>();
	
	fun showBooks() {
		for(book in bookList) {
			print(book); print(" ");
		}
		println();
	}
}
```
```
// Kotlin Code : Main.kt

fun main(args : Array<String>) {

	var shr = Shelf; var shw = Shelf;
	
	Shelf.bookList.add(Book("Java", 10));
	Shelf.bookList.add(Book("C++", 15));
	
	Shelf.showBooks(); 	// → From the object Shelf  
	shr.showBooks(); 	// → From the reference of Shelf Object
}
```
Ouput to the above code is as follow:
```
Book(name=Java, price=10) Book(name=C++, price=15)
Book(name=Java, price=10) Book(name=C++, price=15)
```
-----------------------------------------------------------------------------------------

### Companion Object

(Used to declare **static** variables/methods in Kotlin)

**@JvmStatic :** If the Kotlin code is used in Java code, it makes the content inside the **companion object** visible from the class only.
```
// Java Code

public class Member {

	public static int counter = 0;
	private String name;
	private int age;

	public Member(String name, int age) {
		this.name = name;
		this.age = age;
	}
	public static void staticFunction() {
	}
}
```
```
// Kotlin Code

class Member(var name : String, var age : Int) {

	companion object {
		var counter : Int = 0;
		
		@JvmStatic
		fun staticFunction() {
		}
	}
}
```
-----------------------------------------------------------------------------------------
