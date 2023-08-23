*My Kotlin Studies*

*var x val*
Kotlin provides for us two type of variables. One is var that can be resigned with other values. The other one is val, which when assigned will have always the same value

	[val with collections]
Although people is assigned with an hashmap, it can still add or remove values from the hashMap, which still mutable. The people keyword that is immutable.
val people = HashMap<Int, KotlinPerson>()
people.put(1,KotlinPerson(1,"Augusto"))


*Multiline triple-quoted strings*
val myString = """It is a test
	|Don't do this in production environment""".trimMargin("|")
Use 3x (") to have a multiline string. We use the method "trimMargin("|")" to remove identation caused by the extra spaces.

 
[AUG]*How to see a variable class?* 
myVar::class.qualifiedName


*How is a double in Kotlin?*
Kotlin double will be compiled to a Java literal double (the one which has the 'd' lowercase in java). 
[AUG]So, although there are no literals in Kotlin, so every double or integer is always an object, actually, it will be compiled into a literal to be run on the JVM.
	var myDouble: Double = 17.1


*Int Kotlin x int Java*
The Java integer (the object that represents a int), in Kotlin is an Int with a capital I. It's not an Integer with a capital I.
	var myInt: Int = 19


*How is a Float or Long in Kotlin?*
val myFloat: Float = 13.6f
val myLong: Long = 12L


*About variable*
A variable in Kotlin cannot be used until it has been assigned.


*Object from Java x Any from Kotlin* 
Now in Kotlin instead of 'object' the data type is called 'Any' with a capital 'A'. That the Kotlin equivalent to Java's 'object'.
	Java code: Object result;
	Kotlin code: var result: Any
	

*Exploring casting*
	Kotlin code: myVar is Double
SmartCasting: Means that if we have checked the data type with 'if', then within the code block of the statement, or variable will be automatically cast into the data type that we have checked for
Also, smartcasting will, also happens if the do a "null safe check"
Ex - SmartCasting: if(result is BigDecimal) {
			result.add(BigDecimal(43)) // Here we already can acess the method of BigDecimal after the automatic casting
		   }

When there is NO EXPLICIT TYPE CHECK
keyword: 'as'
		else {
			var myString = result as String
		}
		
		
*Nullable Variables*
	[AUG]var name: String = null -> It will not compile, because when we declare an object with explicit type, it cannot have the value null;
	
	var name: String? = null -> nullable string. #Take a look at the question mark "?"
	println("$name".toUpperCase()) -> Strange way to safe call an nullable string 
	
	[AUG]Null safe operator -> It works like the following: 
		 when there is a null-able variable, if you follow it by a question mark (?) then this now means if the name is null, print null, otherwise, call the method to uppercase.
		 var result = name?.toUpperCase()
	[AUG] Non Null Asserted Operator (!!) -> Use when we need to assuring Kotlin that the variable does not contain null value
		val result = name!!.toUpperCase() -> can result a null point exception 
		
	[AUG] If we set a variable without specific type as null ( var name = null), then that variable receives a special object which is called *"Nothing"*.
	var example =  null -> is not a nullable string or a nullable integer, it is absolutely just a instance of nothing
		WE CANNOT REASSING example TO SOMETHING ELSE; 
			example = "Hi" -> it appears as an error on the IDE
			
			
*Functions*
	fun someMethod(value: Type): ReturnType {}
	
	In Kotlin, the equivalent of a void function RETURNS A 'Unit' Object. We don't need explicit return that
	[AUG] Top-level-functions -> Are functions that aren't defined within a class
	
	Single Expression Function -> fun addTwoNumbers(one: Double, two: Double): Double = one + two
	Named Parameters -> Allows us to change the order of the parameters
		fun printSomeMaths(one: Double, two: Double) = //SomeCode
		//calling the printSomeMaths
		printSomeMaths(two=2.1, one=1.1)
		
	[Optional Parameters] Came to provide a better way to improve the Overloaded functions from java
	we need to define default parameters in the method body 
		fun printSomeMaths(one: Double = 1.1, two: Double = 2.1) = //some code
		//calling the printSomeMaths
		printSomeMaths(two = 5.6) # As we defined default values for the parameters one and two, i don't need to specify the value of both
		
	[AUG] Are the parameters of a function val or vars? All of the parameters in a function name are effectively vals rather than vars. In other words, they are immutable.
	
	[AUG] Lambda as function parameter. 
	Java allow us to pass functions as parameter to others function
		public void methodTakesALambda(String input, Function<String, Integer> action) // This method receives an String input and a function that will convert the string into a int
	
	Kotlin way
		fun methodTakesALambda (input: String, action: (String) -> Int) {
			action(input) //Just invoke the action directly
		}
		[AUG] Function Programming
	
	
*Classes* 
There may be as much classes as you like within a Kotlin file.
If a class is declared as private, so that just can be visible within the package that it was declared

Data Classes - Kotlin
	Alternative way to create a class, mainly when the goal of that class is to store data. Besides de standarts getters and setters method we, also, got the toString, hashcode and equals method
	
	Any variable defined in the primary constructor will be used by the hash and equal methods
	
	data class Customer (var name:String){}
	
	special feature from data classes - copy method
	 val customer5 = customer4.copy(name="newName") 
	
	special feature from data classes - Destructuring
	 This is a shortcut way of creating multiple variables and assigning them to the fields within an object, and the ability to do that is called destructuring.
	 val (name, address, age) = customer5
	 
	 
*IF statement*
In Kotlin if statements can be thinking as a function that returns a value
	
	return if (myAnge > 20) true else false

Null safe check and eventually problems with smartcasting
 IDE possible message: "Smart cast to "int" is impossible, because age is a property that has open or custom getter"
 
 [AUG]non-null assertion operator
 [Elvis Operator] Another way of doing null safe check
 data class Person(val dateBirth: Calendar?){
    val safeAge: Int
	    get() {
			return age?: -1
		 }
	
	val age : Int?
		get() = getAge(dateBirth)
 }
 
 [Elvis Operator] 
	WarningA: Smart cast to "String" is impossible, because "favoriteColor" is a mutable property that could have been changed by this time
	Ex with warningA: 
	var favoriteColor: String? = null
	fun getUpperCaseColor(): String {
		return if (favoriteColor == null) "" else favoriteColor.toUpperCase()
	}
	Ex to solve WarningA:
	fun getUpperCaseColor(): String {
		return favoriteColor?.toUpperCase() ?: "" // 
	}
	Above, in case of favoriteColor be equal null, so the return will be an empty string

 [Let Function]
All the objects in Kotlin have the let function, which perform the execution of a block on specific object; 
 
 Ex:
	val hello = "hello world"
	val uppercaseHello = hello.let {it.toUpperCase()} // equal to val uppercaseHello = hello.toUpperCase()
	//Observation val uppercaseHello = hello.let {it.toUpperCase()} is equal to 
				  val uppercaseHello = hello.let {x -> x.toUpperCase()}
				  
The "let function allows us to perform null fase check

	Ex:
	var favoriteColor: String? = null
	
	fun getLasLatter(a : String) = a.takeLast(1)
	
	fun getLastLetterOfColor(): String {
		//return if (favoriteColor == null) "" getLasLatter(favoriteColor)
		//return getLasLatter(favoriteColor) ?: "" // this won't compile because favoriteColor is a nullable variable and getLastLetter can only be called with a non-null variable.
		//return getLasLatter(favoriteColor!!) ?: "" // will give us a NullPointerException
		return favoriteColor?.let {getLasLatter(it)} ?: "" // favoriteColor is not null with a question mark, dot, (?.) then we'll run our let function and our lambda is going to be getLastLetter of it. 
	}
	
	[Object Equality]
How to compare reference and value equality in Kotlin

	Reference equality  object1 === object2
	value equality object1 == object2
				  
	[*when* operator]
An alternative of *else if ()* 	statements is the when operator

	fun getColorType(): String {
		val color = getUpperCaseColor();
		return when (color) {
			"" -> empty // return if(color == "") empty
			"RED", "GREEN", "BLUE" -> "RGB"
			else -> "other"
		}
	}
	
		
*Loops*

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
	

*Collections* 

	[Immutable Lists]
method listOf("Red","Blue") provide us a immutable list in Kotlin

	[Mutable lists]
method mutableListOf<myType>() provided by Kotlin allows us to instanctiate an mutable list

	[Mutable set or immutable set] [mutableSetOf() x setOf()]
val months = mutableSetOf("Jab","Feb")
	
	[Mutable Maps or immutable maps] [mutableMapOf() x mapOf()]
val webColors = mapOf("red" to "ff0000", "blue" to "00ff00") // here the type of each key and value is inferred 

	[Array] [typeArrayOf()]
In Kotlin array is a class, and it acts very much like a collection. All arrays in Kotlin are mutable. There is no immutable array such as sets and map

	val intArray : IntArray = intArrayOf(1,2,3,4,5)
	intArray.set(3,-4)
	intArray[3] = -7
	

*Exceptions and TryCatch Blocks*
[AUG] All exception in Kotlin are UNCHECKED. 

In Java if you are calling a method which we know throws a particular type of exception, called a checked exception, then the compiler forces us to deal with that exception, either, handling it in a try-catch block or throwing it from the method we are working in.

[AUG] Moreover, there is no WARN about whether an operation/method/logic will throws an exception (WE NEED TO BE CAREFUL WITH THIS SITUATION)

	[@Throws - Throwing an exception]
The important thing here is that when we put this annotation does not make any difference. In other words, it does not warn us about the possible exception might receive
So, why should i use this annotation? If there is some code in java  using tho
	@Throws (InterruptedException::class)
	fun divide(a: Int, b:Int):Double {
		//some code that throws exception
	}
	
	
*Functional Programming*
In Kotlin, when we want to provide a lambda expression to a function and it is the function last parameter> It can be provided outside the round brackets *()*

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
	var myString = applyFunctionString("augusto",::toSentenseCase) //:: is called reflection sintaxe
	
The above code shows us that in kotlin, we can refer a function and pass it as a parameter to another function.
	
	[Working with collections and functional programming]
	
[MAP]collection method map returns a list containing the results of applying the given transform function to each element in the original array.

	val numbers = listOf(1, 2, 3)
	println(numbers.map { it * it }) // [1, 4, 9]

[Filter] A collection method Filter returns a list containing the results of applying the given transform function to each element in the original array. 
		 It generates an one to one mapping
		 
	val originalMap = mapOf("ç0" to 0, "key2" to 2, "key3" to 3)
	val filteredMap = originalMap.filter { it.value < 2 }
	
[FlatMap] A collection method FlatMap returns a single list of all elements yielded from results of transform function being invoked on each element of original array.
	colorCollection.flatMap{if (it.startsWith("b")) listOf (it,it) else listOf(it)}.forEach{println(it)}
	
[Reduce] A collection method  reduce will convert a collection to a single value.
	colorCollection.reduce(result,value -> result + value + ",") //there are loops that happens and every time the loop happens, result becomes a result plus value plus a comma.
	
[Fold] An collection methood Fold accumulates value starting with initial value and applying operation from left to right to current accumulator value and each element.
	colorCollection.fold(0){result,value -> result + value + ",")}
					//fold(initial_value){r,v ->...}




