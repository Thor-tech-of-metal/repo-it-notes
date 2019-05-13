#### inheritance

In Java, as well as in Scala, a class can only have one superclass. 

#### abstract class 


* Abstract classes can contain members which are missing an implementation (in our case, incl and contains).
* Consequently, no instances of an abstract class can be created with the operator new.
```
abstract class IntSet {
	def incl(x: Int): IntSet
	def contains(x: Int): Boolean
}
```

#### Implementing a class 


* Empty extend the class IntSet.
*  An object of type Empty can be used wherever an object of type IntSet is required.
*  IntSet is called the superclass of Empty.
*  Empty is a subclass of IntSet.

```
class Empty extends IntSet {
	def contains(x: Int): Boolean = false
	def incl(x: Int): IntSet = new NonEmpty(x, new Empty, new Empty)
}
```

#### OverLoad constrcutors

```
class Poly ()(termsParameter:Map[Int,Double]){

	val terms= termsParameter withDefaultValue 0.0
		  	
	//overload the constructor.
	def this(bindings: (Int,Double) *) = this (bindings.toMap)

	// (Int,Double) * This means that it can take a n numbers  of convinations of (Int,Double)
	//this(bindings.toMap) calls the constructor.
}
```

#### Override

* In scala you can override members ( methods and attributes)
* the override  key word can bbe used to indicate to the compiler the intention of overriding. It will guarantee that the overwritten can be done.
```
For Example:

abstract class Base { 
	def foo = 1 
}

class Sub extends Base {
	override def foo = 2
} 
```

#### Overload

* In scala we can overload method in the same way that we can in java. T
* The compiler will work out the method call based on the argument numbers and type.
```
def + (x:Int) :Int
def + (x:Long) :Long
def + (x:Double) :Double

```
#### Single instance


* This defines a singleton object named Empty.
* Singleton objects are values, so Empty evaluates to itself.
* The singleton objects are referred using this name directly.
```
object Empty extends IntSet {
	def contains(x: Int): Boolean = false
	def incl(x: Int): IntSet = new NonEmpty(x, Empty, Empty)
}
```

#### traits


A trait encapsulates method and field definitions.  
* Classes, objects and traits can inherit from at most one class but many traits. A class can extend N trait
* A trait is declared like an abstract class.
* Traits resemble interfaces in Java, but are more powerful because they can contains fields and concrete methods. 
* Traits cannot have (value) parameters, only classes can. like class Rationals(Int:x, Int:y)
```
Example:
abstract class Animal {  def speak }

trait WaggingTail {   def startTail="walk"; def stopTail="tail"; }

trait FourLeggedAnimal {  def walk;  def run; }

class Dog extends Animal with WaggingTail with FourLeggedAnimal {
  // implementation code here ...
}
```

#### Using a trait like a Java abstract class

```
trait Pet {
  def speak { println("Yo") }   // concrete implementation of a speak method
  def comeToMaster              // abstract
}

class Dog extends Pet {
  // don't need to implement 'speak' if you don't want to
  def comeToMaster { ("I'm coming!") }
}

class Cat extends Pet {
  // override 'speak'
  override def speak { ("meow") }
  def comeToMaster { ("That's not gonna happen.") }
}
```
* note the use of the def in trait 1) def speak in the trait then is overload  override def speak { ("meow") } 

#### trait: A Diamond Problem

```
A Diamond Problem is a Multiple Inheritance problem. Some people calls this problem as Deadly Diamond Problem.

trait A{ def display(){ println("From A.display")  } }

trait B extends A{  override def display() { println("From B.display") } }

trait C extends A{  override def display() { println("From C.display") } }
class D extends B with C{ }
 
object ScalaDiamonProblemTest extends App {
    val d = new D
    d display
}

```
It always takes teh definition of the last one in the Right ! it will prints "From C.display"


#### trait Sealed

A sealed trait can only be extended within the file in which it defined.
This allows the compiler to perform exhaustiveness checking for pattern matches on that trait.
Why? Because the compiler must know all the possible subtypes to do the checks,
```
sealed trait Option[+A]
final case class Some[+A] extends Option[A]

object None extends Option[Nothing]
```

#### Final

final class cannot be extended anywhere.final classes do not get exhaustiveness checking.
a combination of "sealed" and "final" in the same file is a good practise.

#### Case classes


Case classes can be seen as plain and immutable data-holding objects
that should exclusively depend on their constructor arguments.

the case keyword generates for us:

    * toString, equals, and hashCode methods.
    * The constructor parameters you specify become properties with getters and setters.
    * You no longer have to use ’new’ to create an instance of your class.
    * You can use convenient extractors in match/case statements.
    * apply() and unapply() methods in the companion object.
    * copy() methods for clone.

This functional concept allows us to

   decompose them using pattern matching


#### Equals


When we compare two instances with ==, Scala calls that object’s equals() method automatically.


#### Case classes extension


case class extension should be avoided but you could convert your Edge class into a trait.
If you want to avoid the private statements you can also mark the variables as override
```
trait Edge{
  def a:Strl
  def b:Strl
}

case class EdgeQA(override val a:Strl, override val b:Strl, right:Int, asked:Int ) extends Edge

```

#### Case to case classes inheritance


* case-to-case inheritance is prohibited.




#### Instance of 

*)	instance of
def isInstanceOf[T]: Boolean

*) "def asInstanceOf[T]: T" Use the asInstanceOf method to cast an instance to the desired type.

val recognizer = cm.lookup("recognizer").asInstanceOf[Recognizer] 



#### Persistence data structures

In computing functional programming, a persistent data structure is a data structure that always preserves 
the previous version of itself when it is modified. Such data structures are effectively immutable always. 

*) example that links vectors such as 1 should be linked with next ite.
[1]
--add a new vector [3,5]
[1]-->[3,5]

--add a new vector [2,3,4]
[1]-->[3,5]
 \--->[2,3,4]
--Keeps the history of the previous operation 

#### Evaluation of return types 

if (true) 1 else false. It can be: 

a) Int b) Boolean c) AnyVal c) Object d) PIJA  The expression will always return 1. Therefore it can be Int. 

But the scala type checker takes in account both possible returns (Int and Boolean). 

* As result of that is always chose the closet super class between both returns. In this case it is AnyVal.


#### Method dispatch.

* This means that the code invoked by a method call depends on the runtime type of the object that contains the method.
* Dynamic dispatch of methods is analogous to calls to higher-order functions.

#### getter and setters. 

-In Scala getters are done by the _attribute and setter attribute_ 
HOWEVER IT IS NOT RECOMMENDED TO USE MUTABLE DATA STRUCTURES.

```
class Person() {
 private var _age = 0  var name = ""
 
 // Getter 
 def age = _age

 // Setter 
 def age_= (value:Int):Unit = _age = value 
} 
```

* how to set: 
	personAccessorMutable.age = (1)
	personAccessorMutable.age_= (1)
	personAccessorMutable.name="trolo"
	
* How to get:
	personAccessorMutable.age
    personAccessorMutable.name
	

#### How val functions calls are represented as Objects

Functions val example:
```
val f = (x: Int) => x * x
f(7)

that would be converted in to: 

val f = new Function1[Int, Int] {
	def apply(x: Int) = x * x
}
f.apply(7)
```
