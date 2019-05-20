

#### Streams

The biggest problem is that Scala Streams can be infinite, but your memory isn’t. 

One common guideline, is not to assign a stream (head) to a val, but instead, make it a def.

####Patter matching

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
            
             method is designed for diagnostic purposes