#### Type classes

Type classes are a powerful and flexible concept that adds ad-hoc polymorphism to Scala. 

You can add additional functionality of a type without changing the class itself. without any changes to the original code. 

One could say that the same could be achieved by extending a simple trait. But with type classes,there is no need to predict such a demand beforehand.

###### Implicit classes 

```
package com.thor.utils

object StringUtils {

    implicit class StringImprovements(val s: String) {
        def increment = s.map(c => (c + 1).toChar)
	
	def hideAll: String = s.replaceAll(".", "*")
    }
}


```
How to use it. simply import it and it will add the functionality to the string.

**The import add the implicity in the scope**

```
import com.thor.utils.StringUtils._
println("HAL".increment)

``` 


Implicit classes are used to add  own behavior(s) to the T class passed as parameter to the constructor of the implict class.

implicit class ImplictCalssName(val extension : Type) where extension : Type is the type that will be exnteded to use new features.

“An implicit class must be defined in a scope where method definitions are allowed (not at the top level).” 
This means that the implicit class must be defined :
    A class
    An object
    A package object

A major benefit of this approach is that you don’t have to extend existing classes to add the new functionality.


```
3.chat
// error: value chat is not a member of Int

implicit class LoquaciousInt(x: Int) {
  def chat: Unit = for(i <- 1 to x) println("Hi!")
}

3.chat
// Hi!
// Hi!
// Hi!
```

**Here there is no import becasue the implicit class has been defined in the scop**

#### Type classes more complex 

In This example we are going to make chat make chat to some Person, Dog and String without:
1) Adding the chat method in Person, Dog and String. 
2) Extending trait

Just by adding an import ChattyAddons.  

**The import ChattyAddons cover all implicit class cases Person, Dog and String**

```

final case class Person(firstName: String, lastName: String)

final case class Dog(name: String)

trait CanChat[A] {
  def chat(x: A): String
}

object ChattyAddons {
  implicit object PersonCanChat extends CanChat[Person] {
    def chat(x: Person) = s"Hi, I'm ${x.firstName}"
  }
  implicit object DogCanChat extends CanChat[Dog] {
    def chat(x: Dog) = s"Woof, my name is ${x.name}"
  }
  
  implicit object StringCanChat extends CanChat[String] {
    def chat(x: String) = s"""I'm a string containing "${x}""""
  }
  
  implicit class ChatUtil[A](x: A) {
    def chat(implicit makesChatty: CanChat[A]) = {
      makesChatty.chat(x)
    }
  }
}

// in another package...

import ChattyAddons._

Person("John", "Smith").chat
Dog("Meg").chat
"Hello".chat 

```

#### Simple Type classes 

Using type class Show[A] we should be able to log anything.

```
// A type class to provide textual representation
trait Show[A] {
  def show(f: A): String
}

// A polymorphic function that works only when there is an implicit 
// instance of Show[A] available
def log[A](a: A)(implicit s: Show[A]) = println(s.show(a))

// An instance for String
implicit val stringShow = new Show[String] {
  def show(s: String) = s
}

// The parameter stringShow was inserted by the compiler.
scala> log("a string")
a string
```


