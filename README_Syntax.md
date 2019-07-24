Function declaration:

	fun methodName(params:paramType): ReturnType {
		// fun body
	}

example:

	fun sum(a: Int, b: Int): Int {
    		return a + b
	}

if there is just one line for fun body, we can say (Single-Expression functions):

	fun sum(a: Int, b: Int) = a + b

Unit return type can be omitted: // Unit equals `void`, no return
value;

	fun printSum(a: Int, b: Int): Unit {
    		println("sum of $a and $b is ${a + b}")
	}

we can assign the default value for params, like:

	fun foo(a: Int = 0, b: String = "") { ... }

we can use `vararg` to indicate Variable number of arguments.

Generic Functions:
	fun <T> singletonList(item: T): List<T> { ... }

Extension Functions:
we can use Extension Funcs to extend the method in the original class.

	fun ClassType.functionName(parmas:pramaType): ReturnType {
		// func body
	}

for example. we can extend String class with firstAndLast() func.
Extensions are resolved statically.

Anonymous function: lambda
anonymous function can be used for the params of other function or return vlaue
of other function.

	{ params:paramsType -> func body }

	for example: { x:Int, y:Int -> x + y }

we can also assign Anonymous function to one variable like:

	var sum = { x:Int, y:Int -> x + y }
	println(sum(2, 3))

sum just points to the funtion.

Higher-Order Functions:

function type declaration:

	(paramsType) -> ReturnType

	for example:   (Int, Int) -> Int

higher order function example:

	fun compute(a:Int, b:Int, c:(Int, Int) -> Int):Int = c(a,b)

Inline Functions:

Defining variables:
val: read-only, equals to "final" in Java
var: variable

	var <variableName>:<variableType> = <initial value>

	var <variableName>:<variableType> = <intial value>

example:

	val a: Int = 1  // immediate assignment
	val b = 2       // `Int` type is inferred
	val c: Int      // Type required when no initializer is provided
	c = 3           // deferred assignment

	var x = 5       // `Int` type is inferred
	x += 1


Using nullable values and checking for null: `?`
A reference must be explicitly marked as nullable when null value is possible.

example:

	var b: String? = "abc"
	b = null // ok
	print(b)

	var a: String = "abc"
	a = null // compilation error sine a is defined as NonNull able variable


	// check if variable is null or not
	var strNull:String? = "Kotlin"
	if (strNull == null) {
    		println("null");
	} esle {
    		println(strNull.length)
	}

we can say as below:
	var strNull:String? = "Kotlin"
	println(strNull?.length)

we can also use `let` funcation and lambda to execute:
	var strNull:String? = "Kotlin"
	strNull?.let({println(it)})   // check `let` function

Elvis Operator: `?:`

	return a ?: b

when a is non-null, return a; otherwise, return b;


The `is` Operator: (equals to isInstance in Java)

The `!!` Operator:
the not-null assertion operator (!!) converts any value to a non-null type and
throws an exception if the value is null.

	example:
		val l = b!!.length

if b is not null, return a non-null value of b; or throw an NPE if b is null.


Safe Cast: `as?`
make sure the type compatible. Otherwise, it's better to use `is` check type in advance.

	val aInt: Int? = a as? Int


Loop:
	val items = listOf("apple", "banana", "kiwifruit")
	for (item in items) {
    		println(item)
	}

When experssion:  (equals to `switch`)

	when (variable) {
    		case1 -> { body 1 } or value
    		case2 -> { body 2 } or value
    		...
    		else -> { body unknown} or value
	}


Using the range:
	val x = 10
	val y = 9
	if (x in 1..y+1) {
    		println("fits in range")
	}


@Lable:
Any expression in Kotlin may be marked with a label.
Labels have the form of an identifier followed by the @ sign, for example: abc@.

	loop@ for (i in 1..100) {
    	for (j in 1..100) {
        	if (...) break@loop
    	}
	}

Return at Labels:


Class:

constructor exmaple: pirmary constructor
A class in Kotlin can have a primary constructor and one or more secondary constructors.
The primary constructor is part of the class header: it goes after the class name (and
optional type parameters).

	class Person <constructor>(firstName: String) { ... }

The primary constructor cannot contain any code. Initialization code can be placed in
initializer blocks, which are prefixed with the init keyword.

for declaring properties and initializing them from the primary constructor:

	class Person(val firstName: String, val lastName: String, var age: Int) { ... }

The class can also declare secondary constructors, which are prefixed with constructor:

	class Person {
    		var children: MutableList<Person> = mutableListOf<Person>();
    		constructor(parent: Person) {
        		parent.children.add(this)
    		}
	}

secondary MUST delegate to the primary constructor. like `constructor() : this()`

	creat a class instance:
		val customer = Customer("Joe Smith")

Inside an inner class, accessing the superclass of the outer class is done with the `super`
keyword qualified with the outer class name: super@Outer.

Kotlin has no static method, we can define `Companion Objects` to access the class' member
or method. Or we can use package top-level method to do that.


Properties and Fields:

The full syntax for declaring a property is

	var <propertyName>[: <PropertyType>] [= <property_initializer>]
    	[<getter>]
    	[<setter>]

Late-Initialized Properties and Variables: `lateinit` keyword


Delegated Properties: `by` keyword
	var m:String by Test()

	class Test() { //common logic }


Extensions:
provides the ability to extend a class with new functionality without having to inherit from
the class or use any type of design pattern such as Decorator.

if extenstion function has the same name with member function, member func always wins.


Data Classes:
	data class User(val name: String, val age: Int)

Destructuring Declarations:
	val (name, age) = person

Sealed Classes:
	useful to deal with `when` experssion, don't need to cover `else` since sealed class already
	covers all caese.

Anonymous inner classes:
Anonymous inner class instances are created using an object expression.
functional Java interface (i.e. a Java interface with a single abstract method), using lambda instead.


