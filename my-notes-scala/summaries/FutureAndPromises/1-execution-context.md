An ExecutionContext is similar to a Java Executor. It executes  the computations in a new thread or  in a pooled thread.  

#### There are 3 ways to ways to use the global execution context:

* Passing explicitly the execution context 

```
val inverseFuture: Future[Matrix] = Future { fatMatrix.inverse()  }(executionContext)
``` 
* Using an implicit variable: 

```
implicit val ec = ExecutionContext.global
val inverseFuture : Future[Matrix] = Future { fatMatrix.inverse() } 
```

* Importing the global execution context: 


```
import ExecutionContext.Implicits.global
val inverseFuture : Future[Matrix] = Future { fatMatrix.inverse() } 
```

All code snippets delegate the execution of fatMatrix.inverse() to an ExecutionContext.


#### Scala.concurrent.ExecutionContext

The **scala.concurrent package** comes out of the box with an ExecutionContext implementation. **It is a global static thread pool.** 

**ExecutionContext.global is an ExecutionContext  supported  by java ForkJoinPool.** **It can execute a defined number of parallel threads.**


#### ForkJoinPool


The fork/join framework was presented in Java 7. It provides tools to help speed up parallel processing by attempting to use all available processor cores.

Fork/Join's logic: 
1) separate (fork) each large task into smaller tasks; 
2) process each task in a separate thread (separating those into even smaller tasks if necessary);
3) join the results. 

A ForkJoinPool manages a limited number of threads (the maximum number of threads being referred to as parallelism level).

By default the ExecutionContext.global sets the parallelism level of its underlying fork-join pool to the number of available processors (Runtime.availableProcessors). This configuration can be overridden by setting one (or more) of the VM attributes:

#### Other type of ExecutionContexts


1) CachedThreadPool: Many short lived/cheap tasks

For a lot of short lived actions(say database queries), you would go a with a cached thread pool.
Because each individual task is relatively cheap but spawning a new thread is expensive, you are better off with a CachedThreadPool.


2) FixedThreadPool: Long running/expensive tasks

In contrast with the above, for very expensive operations, you probably want to limit the amount of threads running at one time, 
for various reasons: memory, performance etc.

3) ForkJoinPool: Divide et impera
   
   This type of pool is useful when you need to perform a very large computation, but you can divide it into smaller bits individual workers can compute.

