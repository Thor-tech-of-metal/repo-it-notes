#### Self-types

Self-types are a way to declare that a trait must be mixed into another trait, even though it does not directly extend it.
*That makes the members of the dependency available without imports, because all trait should be in the same  file.

A self-type is a way to narrow the type of this or another identifier that aliases this. 
The syntax looks like normal function syntax but means something entirely different.

```
trait A{ ...some defs and vals }

class B{

    this: A =>
    .....rest of the class
    .....here we can use def and vals of A too

}

new B //gives error: class B cannot be instantiated because it does not conform to its self-type B with A
```

* It needs A to be mixed in to be instantiated: 
```
val b = new B with A
```

#### Self-types more complex example. 

```
trait ReadWrite{

    def read: String = "data from file"

    def write: String = "data written to file"

}

trait ReadWriteDB extends ReadWrite {

    def read: String = "data from DB"

    def write: String = "data written to DB"

}

class Service{

    this: ReaderWriter =>

    def reading: String = read()

    def writing : String = write()

}

val service = new Service with ReadWrite


val service = new Service with ReadWriteDB

```

#### Self-types more complex example. 

```
trait User {
  def username: String
}

trait Tweeter {
  this: User =>  // reassign this
        def tweet(tweetText: String) = println(s"$username: $tweetText")
}
///// Here the idea is that Tweeter is not related with User but it can access to User.username

class VerifiedTweeter(val username_ : String) extends Tweeter with User {  // We mixin User because Tweeter required it
  def username = s"real $username_"
}

val realBeyonce = new VerifiedTweeter("Beyoncé")
realBeyoncé.tweet("Just spilled my glass of lemonade")  // prints "real Beyoncé: Just spilled my glass of lemonade"

```

* Because we said this: User => in trait Tweeter, now the variable username is in scope for the tweet method. T

* This also means that since VerifiedTweeter extends Tweeter, it must also mix-in User (using with User).
