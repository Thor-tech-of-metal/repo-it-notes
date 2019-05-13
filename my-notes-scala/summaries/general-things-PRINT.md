Option-Some-None
=================

The most idiomatic way to use an scala.Option instance is to treat it as a collection or monad and use map, flatMap, filter, or foreach […] 
A less-idiomatic way to use scala.Option values is via pattern matching

1) Option 1 very bad. Null pointer risk.

val glazedDonutTaste: Option[String] = Some("Very Tasty")
println(s"Glazed Donut taste = ${glazedDonutTaste.get}")

2) Option 2: get or else quite nice 
val glazedDonutName: Option[String] = None
println(s"Glazed Donut name = ${glazedDonutName.getOrElse("Glazed Donut")}")

3) Option 4: Pattern matching: safe but to much code 

val glazedDonutName: Option[String] = Some("Very Tasty")
glazedDonutName match {
    case Some(name) => println(s"Received donut name = $name")
    case None       => println(s"No donut name was found!")
}

5) Option 5: Map it without getOrElse. I will ignore None 
val glazedDonutName: Option[String] = Some("Very Tasty")
val glazedDonutTaste: Option[String] = None

glazedDonutTaste.map(taste => println(s"glazedDonutTaste = $taste"))
glazedDonutName.map(name => println(s"glazedDonutName = $name"))

6) Option 6: Map it with getOrElse for None cases.
val opt = Option(1)
val b = opt map (_ + 1) getOrElse "a"

Patter matching
===============
* use _ to cover all cases and avoid runtime error.


```
case list: List[_] => s"thanks for the List: $list"
case m: Map[_, _] => m.toString

could have been written as this instead:

case m: Map[a, b] => m.toString
case list: List[x] => s"thanks for the List: $list"
```

*  type erasure:  the method’s type parameter is not stored but rather converted to its parent type Object 
if it’s unbound or it’s first bound class when it’s bound.

```
case l: List[Int] => "List"
```
If you’re familiar with type erasure on the Java platform, you may know that this won’t work. 
The Scala compiler kindly lets you know about this problem with this warning message:

Test1.scala:7: warning: non-variable type argument Int in type pattern ↵
List[Int] is unchecked since it is eliminated by erasure
    case l: List[Int] => "List[Int]"
            ^