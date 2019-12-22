![](https://lh5.googleusercontent.com/5KYuLmrdOs_YZMNpcMM7k0-QMb0v6NDLXnfwx_XIgqglm3SFfb1K-iGHT-s3MYEKk4peeot3g38qaJWDDcc_MARcGpjNxKED4lNqm3ANIdpVO_5VPG3oSLDzyNyW4gVreiMsRd9p "linha horizontal")

# Kotlin Programming Language

July, 8 of 2019
Augusto Calado Bueno

## VARIABLES

Kotlin provides us two types of variables. One is var that can be resigned with other values. The other one is val, which, when assigned, will have always the same value.

#### About variable

A variable in Kotlin cannot be used until it has been assigned.

#### Collection and Val
```kotlin
val people = HashMap<Int, KotlinPerson>()

people.put(1,KotlinPerson(1,"Augusto"))
```
Although the var people is assigned with a hashmap, it can still add or remove values from the hashMap, which still mutable. The people keyword that is immutable.

### Nullable Variables

In Kotlin, there is a distinction between references that can hold null (nullable references) and those that can not (non-null references).

For example, a regular variable of type String can not hold null

“var name: String = null” It will not compile, because when we declare an object with explicit type, it cannot have the value null.

In Kotlin is allowed nulls when we declare a variable as nullable string, written String?

“var name: String? = null” -> nullable string. Take a look at the question mark "?"

  
  

## Safe Calls

When there is a null-able variable, if that (nullable variable) is followed by a question mark (?) then this now means if the name variable is null, we receive as result null, otherwise, call the method to uppercase.
```kotlin
var result = name?.toUpperCase()
```

### Safe Calls on the LEFT SIDE

A safe call can also be placed on the left side of an assignment. Then, if one of the receivers in the safe calls chain is null, the assignment is skipped, and the expression on the right is not evaluated at all:

// If either `person` or `person.department` is null, the function is not called:
```kotlin
person?.department?.head = managersPool.getManager()
```

### Let Function

All the objects in Kotlin have the let function, which executes a block ON our specific object.

Also, to perform a certain operation only for non-null values, you can use the safe call operator together with let.

  

  ```kotlin

var favoriteColor: String? = null

fun getLasLatter(a : String) = a.takeLast(1)

fun getLastLetterOfColor(): String {

return favoriteColor?.let {getLasLatter(it)} ?: ""

// favoriteColor is not null with a question mark, dot, (?.) then we'll run our let function and our lambda is going to be getLastLetter of it.

}
```
  

The examples bellow are problemes solved by using SAFE CALL with LET

```kotlin
return if (favoriteColor == null) "" getLasLatter(favoriteColor)

return getLasLatter(favoriteColor) ?: "" // this won't compile because favoriteColor is a nullable variable and getLastLetter can only be called with a non-null variable.

return getLasLatter(favoriteColor!!) ?: "" // will give us a NullPointerException
```
  

### Elvis Operator

When we have a nullable reference r, we can say "if r is not null, use it, otherwise use some non-null value x"

  

Example: Java way verification

var favoriteColor: String? = null

fun getUpperCaseColor(): String {

return if (favoriteColor == null) "" else favoriteColor.toUpperCase()

}

  

Example: Kotlin way verification - Elvis Operator

Ex to solve WarningA:

fun getUpperCaseColor(): String {

return favoriteColor?.toUpperCase() ?: "" //

}

  
  

### The !! Operator

The not-null assertion operator (!!) converts any value to a non-null type and throws an exception if the value is null. We can write b!!, and this will return a non-null value of b (e.g., a String in our example) or throw an NPE if b is null

val result = name!!.toUpperCase() // can result a null point exception

### The type Nothing

If we set a variable without a specific type equals null ( var name = null), then that variable receives a special object which is called Nothing.

var example = null

The variable example is not a nullable string or a nullable integer, it is absolutely just an instance of nothing.

## STRINGS

Strings are represented by the type String. Strings are immutable. Elements of a string are characters that can be accessed by the indexing operation: s[i].

### Raw String

A raw string is delimited by a triple quote ("""), contains no escaping and can contain newlines and any other characters:

val myString = """It is a test

|Don't do this in production environment""".trimMargin("|")

Use 3x (") to have a multiline string. We use the method trimMargin("|") to remove indentation caused by the extra spaces.

### String Templates

String literals may contain template expressions, i.e. pieces of code that are evaluated and whose results are concatenated into the string. A template expression starts with a dollar sign ($) and consists of either a simple name:

  

//Code next page

val i = 10

println("i = $i") // prints "i = 10"

or an arbitrary expression in curly braces:

val s = "abc"

println("$s.length is ${s.length}") // prints "abc.length is 3"

## NUMERIC TYPES

### How is a double in Kotlin?

Kotlin double will be compiled to a Java literal double (the one which has the 'd' lowercase in java).

So, although there are no literals in Kotlin, so every double or integer is always an object, actually, it will be compiled into a literal to be run on the JVM.

var myDouble: Double = 17.1

### Int Kotlin x int Java

The Java integer (the object that represents a int), in Kotlin is an Int with a capital I. It's not an Integer with a capital I.

var myInt: Int = 19

### How is a Float or Long in Kotlin?

val myFloat: Float = 13.6f

val myLong: Long = 12L

## IF STATEMENTS

In Kotlin if statements can be thinking as a function that returns a value

return if (myAnge > 20) true else false

  

### When Operator

An alternative of *else if ()* statements is the when operator

  

Example - When Operator

fun getColorType(): String {

val color = getUpperCaseColor();

return when (color) {

"" -> empty // return if(color == "") empty

"RED", "GREEN", "BLUE" -> "RGB"

else -> "other"

}

}

## EXCEPTIONS AND TRY-CATCH BLOCKS

All exceptions in Kotlin are UNCHECKED.

In Java, if you are calling a method which we know throws a particular type of exception, called a checked exception, then the compiler forces us to deal with that exception, either, handling it in a try-catch block or throwing it from the method we are working in.

Moreover, there is no WARN about whether an operation/method/logic will throw an exception (WE NEED TO BE CAREFUL WITH THIS SITUATION)

### @Throws - Throwing an exception

The important thing here is that when we put this annotation does not make any difference. In other words, it does not warn us about the possible exception might receive

So, why should I use this annotation? If there is some code in java using Throws, it can catch these exceptions.

@Throws (InterruptedException::class)

fun divide(a: Int, b:Int):Double {

//some code that throws an exception

}

### Try as an Expression

In Kotlin, just like the if statement, the try statement is an expression. In other words, it can return a value.

  

Example - Assign the results of a try to a varible

var result = try {

doSomething()

}

catch (e: Exception) {

println(e)

}

  

#### Try with Resources x Use Statement

This kind of *try* was introduced in java 7 and is used when there is an event that crashes, inside the codeblock of that *try*, any object that has been declared will be closed automatically.

The Kotlin version is de codeblocks defined with use statements, whose action is exactly the same as the try with resources.

  

  

val input = FileInputStream(“file.txt”)

input.use {

//An exception could be thrown here

//If that happens, so the object will be closed automatically

}

## EXPLORING CASTING

### SmartingCasting

myVar is Double //Kotling Casting

SmartCasting: Means that if we have checked the data type with 'if', then within the code block of the statement, or variable will be automatically cast into the data type that we have checked for

Also, smartcasting will happens if the do a "null safe check"

  

Exemplo - SmartingCasting Kotlin

SmartCasting: if(result is BigDecimal) {

result.add(BigDecimal(43))

// Here we already can access the method of BigDecimal after the automatic casting

}

### Explicit Casting

When there is NO EXPLICIT TYPE CHECK we explicitly use the keyword: 'as'

var myString = result as String

## LOOPS

  

Loops Examples

[Basic for loop]

for(variable: Type in SomeCollection) { //implementation}

for(variable in SomeCollection) { //implementation}

for((id, title, firstName) in people) {// implementation} //Destructuring

for( i in 0..9) {//implementation} //this sintaxe is called range (number A to number B)

(0..9).forEach{ i -> println(i)}

[range in Kotlin]

(0 downTo 9).forEach{}

(0 until 9).forEach{}

(0..9 step 2).forEach{}

## FUNCTIONS

To declare a function in kotlin we need to use the keyword fun. The parameter besides the name, we also need to declare their types.

fun someMethod(value: Type): ReturnType {}

In Kotlin, the equivalent of a void function RETURNS A 'Unit' Object. We don't need explicit return that.

fun someFunc() {}

// It is a void function that returns Unit. Unit type declaration is opticonal

### Single Expression Function

When a function has just a single expression or one line, the curly braces can be removed and the function declaration receives using the equal signal (=), the expression.

fun addTwoNumbers(one: Double, two: Double): Double = one + two

### Change parameter order

We can, when calling a function, change the order of the parameters by using their names and assigning them their respective values.

fun printSomeMaths(one: Double, two: Double) = //SomeCode

//calling the printSomeMaths

printSomeMaths(two=2.1, one=1.1)

### Optional Parameters

Optional Parameters came to provide a better way to improve the Overloaded functions from java. In order to do that we need to define default parameters in the method body.

fun printSomeMaths(one: Double = 1.1, two: Double = 2.1) = //some code

//calling the printSomeMaths

printSomeMaths(two = 5.6)

Since we set default values for the parameters one and two, I don't need to specify the value of both.

### BIG OBSERVATION - Parameters of a Function

Are the parameters of a function val or vars?

All of the parameters in a function name are effectively vals rather than vars. In other words, they are immutable.

### Varargs Parameter

A parameter of a function (normally the last one) may be marked with vararg modifier to to have a variable number of arguments.

fun <T> asList(vararg ts: T): List<T> {//some code}

### Top-Level Functions & Member Functions

Top-level-functions are functions that aren't defined within a class, In addition to top level functions, Kotlin functions can also be declared local, as member functions and extension functions.

  

Example - Member Functions

fun dfs(graph: Graph) {

val visited = HashSet<Vertex>()

fun dfs(current: Vertex) { // Member Functions

if (!visited.add(current)) return

for (v in current.neighbors)

dfs(v)

}

dfs(graph.vertices[0])

}

### Lambda as Parameter

Java allows us to pass functions as parameter to others function:

public void methodTakesALambda(String input, Function<String, Integer> action)

// This method receives an String input and a function that will convert the string into a int

Kotlin Way to pass lambda as Parameter

fun methodTakesALambda (input: String, action: (String) -> Int) {//somecode}

  

Example - Kotlin Way to pass lambda as Parameter

fun foo(bar: Int = 0, baz: Int = 1, qux: () -> Unit) { ... }

foo(1) { println("hello") } // Uses the default value baz = 1

foo(qux = { println("hello") }) // Uses both default values bar = 0 and baz = 1

foo { println("hello") } // Uses both default values bar = 0 and baz = 1

  
  
  
  
  

## SUPERCLASS

### Any Superclass

Unlike Java, where every class extends from the superclass Object. In Kotlin, the root of the Kotlin class hierarchy is Any. In other words, Every Kotlin class has Any as a superclass.

Now in Kotlin instead of 'Object' the data type is called 'Any' with a capital 'A'. That the Kotlin equivalent to Java's 'object'.

Object result; // Java code

var result: Any // Kotlin code

## CLASSES

All Classes in Kotlin are final. We cannot extend it unless we use the open keyword in order to make a class extendable.

If a class is declared as private so that just can be visible within the package that it was declared

### Constructor

#### Default Constructor

It is possible to define the class and provide parameters immediately after the class name in round brackets. This part is referred as default constructor

class Customer (val name: String, val address: String, var age: Int) { //Implementation}

This is a shorthand way of saying there is a class with these as internal fields that they're publicly visible, but we also now get a constructor, which sets each of these variables.

#### Secondary Constructors

Besides the default constructor we have secondary constructors. They effectively are functions. And as were shown before, all function has its parameters categorized as val, in other words, is not allowed to change its value.

To exemplify lets imagen that we want to create a customer who is going to have an empty address.

class Customer (val name: String, val address: String, var age: Int) {

constructor(name: String, age: Int) : this(name, “”, age) //secondary constructor

}

There is a restriction in secondary constructors, which is the obligation to call the primary constructor.

How to put some code to run in the code block of the primary constructor? The way to do this is using a block that starts with the keyword init.

  

Example: Primary and Secondary Constructor

class Customer (val name: String, val address: String, var age: Int) {

constructor(name: String, age: Int) : this(name, “”, age) {

//secondary constructor

println(“Hellow here is the secondary constructor”)

}

init {

println(“Hellow here is the init from primary constructor”)

}

}

Important: When there are codes in the secondary constructor and in the init block. If an object was created by using the secondary constructor. First, all the code implemented in the init block runs and, only after that, the code declared in the secondary constructor will run.

val customer = Customer(“John”,31)

//Output

Hellow here is the init from primary constructor

Hellow here is the secondary constructor

  

Alternative ways to class design

class Customer (val name: String, var age: Int) {

val address: String

constructor(name: String, address: String, age: Int) : this(name, age) {

//secondary constructor

this.adress = address

}

init {

address = “”

}

}

class Customer (val name: String, val address: String = “”, var age: Int) { }

### Overriding Getters and Setters

The getters and setters methods are not explicit in the body class in Kotlin. However, they are still there. If for some reason there is the necessity to override one of them so immediately after the variable declaration, we then are going to write a method called *set*.

  

Example - Override Set Method

class MyCustomer (val name: String, var age: Int) {

var approved: Boolean = false;

set( value) {

if( age >= 21 ) {

field = value //the keyword 'field' refers to approved variable

}

else {

println("cannot be approved")

}

}

  

val nextAge

get() = age + 1

}

Although we use the keyword set and get, we still reference the own field name (approved in or case) to perform those operations.

val customer = MyCustomer(“John”, 31)

customer.approved = true //set method beeing used

### Static and Overridden Functions

The kotlin way to create static functions requires a special block of code which starts with the keywords “companion object”. Everything inside that block is going to be a static function.

Rather than Java, in kotlin to override a function why don't use the annotation @override. We just need to start the function that we intend to override with the keyword *override*

![](https://lh6.googleusercontent.com/Pb7UWiHxpL8vf2y1uOXcq_2PIT3qjG-Vwbuz_GMfACxu4qsA1VnYcMbZO3T0l8XLtb0G8N-I3GPYTMu8Kq1RCfPjMUxo-taWyczP0ZYCrsZRlLxWf7F65gIGmv7YjLPI7B0W2o5k)

![](https://lh5.googleusercontent.com/oILSg43fVZiqjIAftzaRenzehZJdafWTEz0lrcro_U8FLW1xSj9LEYKrFmUGvDsxtSUGunsJhfNbaAN5ubEp0Xg79MwpNM7COvCtltxp9SoPkPWJRRsfIRRqWDRZz096j8yHjGVX)

### Data Classes

An alternative way to create a class, mainly when the goal of that class is to store data. Besides de standards getters and setters method we, also, got the toString, hashcode and equals method

Any variable defined in the primary constructor will be used by the hash and equal methods

data class Customer (var name:String){}

#### Special feature from data classes - copy method

val customer5 = customer4.copy(name="newName")

#### Special feature from data classes - Destructuring

This is a shortcut way of creating multiple variables and assigning them to the fields within an object, and the ability to do that is called destructuring.

val (name, address, age) = customer5

  

### Companion - Kotlin Static Components

If a class has a companion object defined, you can also define extension functions and properties for the companion object:

class MyClass {

companion object { } // will be called "Companion"

}​

fun MyClass.Companion.foo() { ... }

Just like regular members of the companion object, they can be called using only the class name as the qualifier.

## INTERFACES AND EXTENDING CLASSES

### Interfaces

In Kotlin interfaces can be there function definitions, variable declarations and even function implementations

![](https://lh4.googleusercontent.com/Y2M4hRfzS6YTlDt98sXAfQbCBpl4TGkqN6HR90D-K338RjSzbyNITqR_rRgEsSjtYnSG174wnnZxG912WqqYGDvs25Ispjsjrs57TlI5SU8BKVm6_9XoWHOzIkuOVLIeGTgsq8sy)

Implementation

![](https://lh5.googleusercontent.com/7Qgpzf_CwkltgFp4EaQwnR2AG46O7Ebrrjc88iheZfJQ0V7jGg4uAnPFuLsAA43z1g6-TX5H3I9Ho43pFF-7HNlGGbVC3QWj5KmJhWOhHI_BZOdJvlkXZk_RWltSvmv-CKedZdsr)

So this colon-syntax-- after the class name is, if what follows is an interface than we are implementing the interface-- if what follows is an class, then we are extending the class. There is one other difference though and that is if we are extending a class, we must call its constructor passing in any parameters that the class we're extending need.

### Creating Custom Exception

In Kotlin, to create a custom exception, what we need to do is to create a class that extends the class called Throwable.

![](https://lh6.googleusercontent.com/KlTsYt2nm0XmQt3qzOWkykAkJDlTdN4iVHq9sISF3rc1_VZMTYBiJX1iEE_k3OUo2b3gFzaemsa-3Lg9xIBn-WyLEVCZwLa6QGztsSpx23tz_5V4vyJHXJvW5mV0JIt6CuiiKY3S)

  

## COLLECTIONS

#### Immutable Lists

method listOf("Red","Blue"), provide us a immutable list in Kotlin

#### Mutable lists

method mutableListOf<myType>(),  provided by Kotlin allows us to instanctiate an mutable list

#### Mutable set or immutable set - mutableSetOf() x setOf()

val months = mutableSetOf("Jab","Feb")

#### Mutable Maps or immutable maps - mutableMapOf() x mapOf()

val webColors = mapOf("red" to "ff0000", "blue" to "00ff00")

// here the type of each key and value is inferred

#### Array - typeArrayOf()

In Kotlin array is a class, and it acts very much like a collection. All arrays in Kotlin are mutable. There is no immutable array such as sets and map

val intArray : IntArray = intArrayOf(1,2,3,4,5)

intArray.set(3,-4)

intArray[3] = -7

## OBJECT EQUALITY

How to compare reference and value equality in Kotlin

Reference equality object1 === object2

Value equality object1 == object2

## EXTENSION FUNCTIONS

Kotlin allows us to add functions to existing classes. Any classes, even final classes, that has not been opened and it is possible to add additional functions into that class.

The extension function is the functions that were added in some existing class. If I create a new method for String class means that the entire package which we are working in, strings now have an additional function,

  

Example - Extension Functions - String class

fun String.myNiceName(): String { //Do Something….}

## FUNCTIONAL PROGRAMMING

In Kotlin, when we want to provide a lambda expression to a function and it is the last parameter. It can be provided outside the round brackets *()*

fun applyFunctionString( input:String, myFunction: (String) -> String) : String {

return myFunction(input);

}

//main

var myString = applyFunctionString("augusto"){x-> x.toSentenseCase()} //

var myString = applyFunctionString("augusto"){it.toSentenseCase()} //

Keyword "it" refers to the default parameter if it's a single parameter in lambda

fun toSentenseCase(input: String) : String {

return input[0].toUpperCase() + input.substring(1)

}

//main

var myString = applyFunctionString("augusto", ::toSentenseCase)

//:: is called reflection sintaxe

The above code shows us that in kotlin we can refer a function and pass it as a parameter to another function.

### Working with Collections and Functional Programming

[MAP] collection method map returns a list containing the results of applying the given transform function to each element in the original array.

val numbers = listOf(1, 2, 3)

println(numbers.map { it * it }) // [1, 4, 9]

  

[Filter] A collection method Filter returns a list containing the results of applying the given transform function to each element in the original array.

// It generates an one to one mapping

val originalMap = mapOf("ç0" to 0, "key2" to 2, "key3" to 3)

val filteredMap = originalMap.filter { it.value < 2 }

[FlatMap] A collection method FlatMap returns a single list of all elements yielded from results of transform function being invoked on each element of original array.

colorCollection.flatMap{if (it.startsWith("b")) listOf (it,it) else listOf(it)}.forEach{println(it)}

[Reduce] A collection method reduce will convert a collection to a single value.

colorCollection.reduce(result,value -> result + value + ",")

//there are loops that happens and every time the loop happens, result becomes a result plus value plus a comma.

[Fold] An collection methood Fold accumulates value starting with initial value and applying operation from left to right to current accumulator value and each element.

colorCollection.fold(0){result,value -> result + value + ",")}

//fold(initial value){...}

  

## Spring Boot and Kotlin

### Autowired Differences - Lateinit

If we declare a dependency injection like we tend to do in Java we get a error that says “Property must be initialized or be abstract”.

@Autowired

val theater: TheaterService

There is an extra keyword we need to use in Kotlin when we are Autowiring in an object when we use a dependency injection to create the instance of an object into our class. And that additional keyword is lateinit.

@Autowired

lateinit var theater: TheaterService

When lateinit is added in the variable autowired, it is saying that that object is going to be initialised sometime very soon after the controller it is on. Also, it tells to Kotlin there is some other code somewhere that is responsible for doing that initialization.

Observation - lateinit only works with var and is used to create dependencies injection

### Backing Bean - Kotlin and Spring

The way that Spring will create backing beans, first Spring instantiates a new Backing beans and it is going to use the set methods to bound the values from the original Backing Beans to it newest bean. In view of that, is import determine which variable will be var or val, because when Spring is filling the new object backing bean it will not be able to set up the val variables.

### Example - Spring Backing Bean Behavior

```kotlin
@PostMapping("checkAvailability")

fun checkAvailability(bean: CheckAvailability): ModelAndView {

//Do Something
  return ModelAndView("seatBooking", "bean", bean)
}
```

### Deal with Hibernate Limitation
When hibernate loads data from a database, it instantiates the object using the default constructor, and then sets each of our properties using setter methods. It can be a problem is there is no default constructor, set methods for the variables and variabels declared as val.

To solve that problem, the Kotlin developers have released compiler plugins. One of them is allow JPA instantiate entity objects with a default constructors and then call setters, however it does not allow any other code to do that.

  

### Dependencies Plugin
```xml
<dependency>
  <groupId>org.jetbrains.kotlin</groupId>
  <artifactId>kotlin-maven-allopen</artifactId>
  <version>${kotlin.version}</version>
</dependency>
<dependency>
  <groupId>org.jetbrains.kotlin</groupId>
  <artifactId>kotlin-maven-noarg</artifactId>
  <version>${kotlin.version}</version>
</dependency>
``` 

#### Hibernate The Find Method’s Return
The methods findBySomething perhaps return an object, however is possible anything match with the criteria, thus the return will be null. But in kotlin it is not the case, if nothing is found so our return is an Optional<Object>.

  
  
  

### Dependencies Plugin
