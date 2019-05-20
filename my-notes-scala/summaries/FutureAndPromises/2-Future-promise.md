

#### Promise  and Future


Promise is a companion type that allows you to complete a Future by putting a value into it using success() method.
Once a Promise has been completed, it’s not possible to change it any more.

A Promise instance is always linked to exactly one instance of Future. 

Promise --> have a -->Future. Promise is a wrapper for the Future.

The Scala implementation is in fact asynchronous without blocking, while in Java you can’t get the future value without blocking.

#### Compete the Future using promise.success()

To complete a Promise with a success, you call its success()  method. 

Once you call the promise.success(TaxCut(20)) that the Promise instance is no longer writable, 
and future attempts to do so will lead to an exception.

Usually, the completion of the Promise and the processing of the completed Future will not happen in the same thread. 
It’s more likely that you create your Promise, start computing its value in another thread 
and immediately return the uncompleted Future to the caller.

Calling the future method of a Promise multiple times will definitely always return the same Future object. 


```scala

case class TaxCut(reduction: Int)

val taxcut: Promise[TaxCut] = Promise[TaxCut]()
val taxcutFuture: Future[TaxCut] = taxcut.future
taxcut.success(TaxCut(20))

``` 

#### Breaking a promise calling promise.failure()
```scala
val p = Promise[TaxCut]()
p.failure(LameExcuse("global economy crisis"))

```

#### Once you create a Future in REPL it will return a DefaultPromise

```scala
val f: Future[String] = Future { "Hello world!" }
```
REPL output: 
f: scala.concurrent.Future[String] = scala.concurrent.impl.Promise$DefaultPromise@793e6657


### Example
```scala

object Government {
  
  def redeemCampaignPledge(): Future[TaxCut] = {
    val promise = Promise[TaxCut]()
    Future {
      println("Starting the new legislative period.")
      Thread.sleep(2000)
      // finsih a future by setting the future value in using the  p.success()
      promise.success(TaxCut(20))
      println("We reduced the taxes! You must reelect us!!!!1111")
    }
    promise.future
  }
}

val taxCutF: Future[TaxCut] = Government.redeemCampaignPledge()

println("Now that they're elected, let's see if they remember their promises...")
  
  taxCutF.onComplete {
  
    case Success(TaxCut(reduction)) =>
      println(s"A miracle! They really cut our taxes by $reduction percentage points!")
    
    case Failure(ex) =>
      println(s"They broke their promises! Again! Because of a ${ex.getMessage}")
  }

```


#### Block statement future 
```scala

import scala.concurrent.Future
import scala.concurrent.blocking

def startTask(number: Int): Future[Unit] = Future {
  blocking {
    debug(s"Starting task#$number")
    Thread.sleep(2000) // wait 2secs
    debug(s"Finished task#$number")
  }
}
```
