#### Option-Some-None
The most idiomatic way to use an scala.Option instance is to treat it as a collection
or monad and use map, flatMap, filter, or foreach […] and getElse().

A less-idiomatic way to use scala.Option values is via decomposition pattern matching

1) Option 1 very bad. Null pointer risk.

```
val glazedDonutTaste: Option[String] = Some("Very Tasty")
println(s"Glazed Donut taste = ${glazedDonutTaste.get}")
```

2) Option 2: get or else quite nice 
```
val glazedDonutName: Option[String] = None
println(s"Glazed Donut name = ${glazedDonutName.getOrElse("Glazed Donut")}")
```

3) Option 4: Pattern matching: safe but less-idiomatic way too much code 

```
val glazedDonutName: Option[String] = Some("Very Tasty")
glazedDonutName match {
    case Some(name) => println(s"Received donut name = $name")
    case None       => println(s"No donut name was found!")
}
```


5) Option 5: Map it without getOrElse. **I will ignore None**

```
val glazedDonutName: Option[String] = Some("Very Tasty")
val glazedDonutTaste: Option[String] = None

glazedDonutTaste.map(taste => println(s"glazedDonutTaste = $taste"))
glazedDonutName.map(name => println(s"glazedDonutName = $name"))
```




6) Option 6: Map it with getOrElse for None cases. **The most idiomatic**

```
val opt = Option(1)
val b = opt map (_ + 1) getOrElse "a"
```
7) FlatMap does not include None in the results but Map does

```
def toInt(s: String): Option[Int] = {
    try { Some(Integer.parseInt(s.trim))} 
    catch { case e: Exception => None }
}

scala> val strings = Seq("1", "2", "foo", "3", "bar")
scala> strings.map(toInt)
res0: Seq[Option[Int]] = List(Some(1), Some(2), None, Some(3), None)

scala> strings.flatMap(toInt)
res1: Seq[Int] = List(1, 2, 3)
```



8) Flatten will eliminate nested Options:

```
scala> Some(Some(1)).flatten
Option[Int] = Some(1)
scala> Some(None).flatten
Option[Nothing] = None
scala> None.flatten
Option[Nothing] = None

```
8) Option is normally used to return a found value or not 
‘Option’ is a Scala generic type that can either be ‘some’ generic value or none.  

```
def findPerson(key: Int): Option[Person]  
```
The method will return Some[Person] if the record is found
but None if the record is not found.

#### Either-Right-Left


*) What is the main use of Option and Either in Scala? 
Either: is used to indicate an error one option or the another.
we don’t need to deal with ‘null’ checks, No need to handle NullPointerException and other exceptions.

```
def divideXByY(x: Int, y: Int): Either[String, Int] = {
    if (y == 0) Left("Dude, can't divide by 0")
    else Right(x / y)
```

#### Try

Try is  simple result wrapper which encapsulate a result or an exception.  Failure [exception] Success [result] .
we can assing the execution of a method which could thorw an exception to a Try[].

```
val result: Try[URL] = Try( new URL("xxx") )
Try[URL] = Try( SOME_THING_THAT_RETURN_AN_EXCEPTIO )
```



####  Map a Try 


Map: mapping a result of a Try will only map the successful result.
it will only consider Success result and decompose it.
Failure will be ignored.

Example 1
```
val input= "xxx" 
TryExample.parseURL(input) map {
      element => element.getProtocol
      println(s"the result is ${element}")
}

////It will no print anything because Failure is ignored. It will need a getOrElse{ }.

TryExample.parseURL(input) map {
      element => element.getProtocol
      println(s"the result is ${element}")
} getOrElse{ println(s"the result is a failure ") }

```



#### FlatMap can remove a nested chain of Try[Try[Try[....]]]

```
import java.io.InputStream
def inputStreamForURL(url: String): Try[Try[Try[InputStream]]] = parseURL(url).map { u =>
  Try(u.openConnection()).map(conn => Try(conn.getInputStream))
}

///// it can be re-writen like this //

def inputStreamForURL(url: String): Try[InputStream] = parseURL(url).flatMap { u =>
  Try(u.openConnection()).flatMap(conn => Try(conn.getInputStream))
}

```


#### For comprehensions

The support for flatMap, map and filter means that you can also use for comprehensions in order to chain
operations on Try instances.

```
def getURLContent(url: String): Try[Iterator[String]] = {
  for {
    url <- parseURL(url)
    connection <- Try(url.openConnection())
    is <- Try(connection.getInputStream)
    source = Source.fromInputStream(is)

  } yield source.getLines()
}
```

#### Try recover

Due to the fact that a Try[T] can return an exception it can be recover{} . Any method that return a Try[] or throw an exception can be recover.

```
val content = getURLContent("garbage") recover {
  case e: FileNotFoundException => Iterator("Requested page does not exist")
  case _ => Iterator("An unexpected error has occurred. We are so sorry!")
}
```




