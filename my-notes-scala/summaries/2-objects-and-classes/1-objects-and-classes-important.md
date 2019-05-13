#### Class definition

*)We can create object by doing  new Rational(1, 2)

```
class Rational(x: Int, y: Int) {  def numer = x  def denom = y }
```

This deﬁnition introduces two entities:  
* A new type, named Rational ( class).   
* A constructor Rational to create elements of this type (objects).
Scala keeps the names of types and values in diﬀerent namespaces. So there’s no conﬂict between the two deﬁntions of Rational.

#### Access to the members

```
val x = new Rational(1, 2) > x: Rational = Rational@2abe0e27
x.numer > 1
x.denom > 2
```
#### Scala provides these scope visibility options

* private[this]:  The method is available only to the current instance of the class it’s declared in.
* private : The method is available to the current instance and other instances of the class it’s declared in.
* protected:  The method is available only to instances of the current class and subclasses of the current class.
* private[model]: The method is available to all classes beneath the com.acme.coolapp.model package.
* private[coolapp]: The method is available to all classes beneath the com.acme.coolapp package.
(no modifier):  The method is public.

* Object-private scope : The method is available only to the current instance of the current object.
```
class Foo {
    private[this] def isFoo = true
    def doFoo(other: Foo) {  if (other.isFoo) {  // this line won't compile   // ...  }  }
}
```
* Package-specific: private to the current package with the private[packageName] syntax.

```
package com.acme.coolapp.model {
    class Foo {
        private[model] def doX {}
        private def doY {}
    }
    class Bar {
        val f = new Foo
        f.doX  // compiles
        f.doY  // won't compile
    }
}
```


#### Default initialization

The =_ is the default initialization
```
class A (){ var pepe:String=_}
```

#### Constrcutors
```
class Rational (x: Int, y: Int) {
	
  require(y > 0, ”denominator must be positive”)
  
  def number = x
  def demom = y	
}
```


#### Require

* require is used to enforce a precondition on the caller of a function. For example it can be used to validate the constructor parameters.

* In Scala, a class implicitly introduces a constructor. This one is called the primary constructor of the class.
* class Rational (x: Int, y: Int) the primary constructor is (x: Int, y: Int).
* Each class must have one Primary Constructor: Either Parameter constructor or Parameterless constructor.
* These members definitions "def number = x and def demom = y" use the values comming from the primary constructor.
* The primary constructor: * takes the parameters of the class and executes all statements in the class body.



#### Auxiliary constructors or secondary.

* The Auxiliary constructors are methods named "def this".
* Auxiliary Constructors cannot call a super class constructors. 
They should call them through Primary Constructor only.
```
class Rational(x: Int, y: Int) {
	
	def this(x: Int) = this(x, 1)
...
}

new Rational(2) > 2/1

```
	
#### Class attribute and constructor arguments at the same time.

* This defines at the same time constructor parameters and class attributes
* These are evaluated as val only once when the object is created by the constructor. 

```
class Cons (_head : Int , _tail : IntList) extends IntList {
	val head = _head
	val tail= _tail
}

--> is the same
class Cons (val head: Int, val tail: IntList) extends IntList{
  
  override def isEmpty = false
} 

```

*) Not need to define the attributes because they have been defined in (val head: Int, val tail: IntList)  

#### Create an instance of a Class without using ‘new’ keyword in Scala

Internally it make a call to appropriate apply method available in Companion object. 
Here appropriate apply method means that matched with parameters.

Example1:
```
class Person private (name: String){

  object Person{  def apply(name: String) = new Person(name) }
}
Person("pepe")

```


Example2:
// we will be able to use this object as a function, as well as an object
```
object Foo {   var y = 5;  def apply (x: Int) = x + y }

Foo (1) // using Foo object in function notation 
```



#### Companion Object

A companion object is an object with the same name as a class or trait and is defined in the same source 
file as the associated file or trait. A companion can access to private members
```
class MyString(val jString:String) {
  private var extraData = ""
  override def toString = jString+extraData
}
object MyString {
  def apply(base: String, extras: String) = {
    val myString = new MyString(base)
    myString.extraData = extras
    myString
  }
}

```

#### No static function in the constructor chain 

* Scala does not have primitive data types and also does not have static members.
* Functions can be declared any where and used before attributes initialization without the need to be static
* object singleton can be used as static classes.
```
class Rationals (x: Int, y: Int){
  
  require(y !=0 ,"denominator must be nozero")
  
  private val g = greatestCommonDenominator(x,y)
  
  private def greatestCommonDenominator( a: Int, b: Int):Int ={

    //In scala the code is interpreted that is why
    //the function should be declared before it is used.
    if ( b==0) a
    else greatestCommonDenominator(b, a % b)
  }  
}
```


#### Super classes

* scala.Any is the super class.
* scala.AnyVal is the super class of all data types (Integer, Char etc) but not String. 
* scala.AnyRef super class of (List, Seq , String and collection)

#### Classes At the top of the type hierarchy

* scala.Any the base type of all types   Methods: ‘==‘, ‘!=‘, ‘equals‘, ‘hashCode, ‘toString‘

* scala.AnyRef The base type of all reference types; Alias of ‘java.lang.Object‘

* scala.AnyVal The base type of all primitive types


#### scala.Null

* The type of Null has a null.
* Null is a subtype of every class that inherits from Object; 
* it is incompatible with subtypes of AnyVal. AnyVal Always accept their default values.
* Null is a Type (final class) in “scala” package as “scala.Null”. 

scala> val myNullRef : Null = null
myNullRef: Null = null


```
val z: Int = null // error: type mismatch. it is incompatible with subtypes of AnyVal.
val x = null // x: Null x has not a declared type therefore it the type is Null.
val y: String = null // y: String. Y is type String with a Null value.

```


#### scala.collection.immutable.Nil.type

*) Nil is an object, which is used to represent an empty list with Nil tail. 
It is defined in “scala.collection.immutable” package as shown below:
	 
   *head::Nil. A Nil tail

#### scala.Nothing

* It is a subtype of every other type ins scala. It is at the bottom of everything.
* Nothing is a Type (final class).
* Nothing is never instantiated and is there for the benefit of the type system. 

Use Cases of Nothing In Scala:-

    * object None extends Option[Nothing]
    * list: List[Nothing] = List()--> list: List[Nothing] = List()
    * We can use Nothing as a return type of methods which never return.
    * We can use Nothing as a return type of methods which terminates abnormally.
    * You only use Nothing if the method never returns: 
    def error ( msg : String) = throw new java.lang.Error("error") --> scala type checker shows: -->error ( msg : String) Nothing. 


#### scala.Unit

* Unit is a subtype of scala.AnyVal
* A method with return type Unit is analogous to a Java method which is declared void.


