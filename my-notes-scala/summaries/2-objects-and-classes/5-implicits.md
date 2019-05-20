### Implicits 

The order that the compiler will look up for implicits is : 

* implicits declared locally
* imported implicits
* outer scope (implicits declared in the class are considered outer scope in a class method for instance)
* inheritance
* package object
* implicit scope like companion objects


### For example 

```scala
trait CanFoo[A] {
  def foos(x: A): String
}
 
object Def {
  implicit val importIntFoo = new CanFoo[Int] {
    def foos(x: Int) = "importIntFoo:" + x.toString
  }
}
 
object Main {
  def test(): String = {
    implicit val localIntFoo = new CanFoo[Int] {
      def foos(x: Int) = "localIntFoo:" + x.toString
    }
    import Def.importIntFoo
 
    foo(1)
  }
 
  def foo[A:CanFoo](x: A): String = implicitly[CanFoo[A]].foos(x)
}
 
println(Main.test)
```
```concept
$ scala test.scala
```

**Result--> localIntFoo:1**

**implicits declared locally always goes first** 

