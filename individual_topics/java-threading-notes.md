# Java Threading

### What are the states associated with the thread?  
* Ready
* Running
* Waiting
* Dead state


### What are the thread states?
Following are the different thread states:
* New: A thread which is just instantiated is in the new state. When a start() method is invoked, the thread becomes the ready state. Then it is moved to the runnable state by the thread scheduler.
* Runnable: A thread which is ready to run 
* Running: A thread which is executing is in running state.
* Blocked: A blocked thread is waiting for a monitor lock is in this state. This thing can also happen when a thread performs an I/O operation and moves to the next state.
* Waiting: It is a thread that is waiting for another thread to do the specific action.
* Timed_waiting: It is a thread that is waiting for another thread to perform.
* Terminated: A thread that has exited is in this state.

### What are the major differences between Thread and Process?
The thread is a subset of process. The process can contain multiple threads. The process can run on on different memory space, but all threads share the same memory space.


### What is deadlock
Deadlock is a situation when a thread is waiting for an object lock, that is acquired by another thread and second thread also waiting for an object lock that is acquired by the first thread. As both threads are waiting for each other to release this condition is called deadlock.

In some situations it is possible to prevent deadlocks. I'll describe three techniques in this text:
* Lock Ordering
* Lock Timeout
* Deadlock Detection



### What is LiveLock?
Livelock occurs when all threads are blocked and not able to execute because of the unavailability of required resources, and non-existence of any unblocked thread.  
Livelock can occur in the following conditions:
* When all the threads in a program executed on an object with zero parameters. The program is live-locked and never processed until one or more threads call  
Object.notify() or Object.notifyAll() on the relevant objects.
* Livelock also happens when all the threads in a program are stuck in infinite loops. 

### What is a monitor?
The monitor is a body of code that can be executed by only one thread at a time.   
If any other thread attempts to get access at the same time, it will be suspended until the current thread releases the Monitor.

 
### What do you mean by thread starvation?   
In the situation when a thread does not have sufficient CPU for its execution Thread starvation happens.  
However, it may happen in the following scenarios
* Low priority threads will get less CPU compared to high priority threads. Lower priority thread can starve away waiting to get more CPU space to perform calculations.
* The thread may be waiting indefinitely for a lock on object's monitor but notify() may repeatedly be awakening some other threads. In that case, also thread starves away. 

### What is the meaning of busy spin in multi-threading?  
Busy spin is a technique that concurrent programmers employ to make a thread wait on certain condition.   
This is quite different from traditional methods like wait() and sleep() which all involves relinquishing CPU control. This method does not require abandon CPU, instead it the just runs the empty loop.

### What is context-switching in multi-threading?
It is the process of storing and restoring of CPU state. This helps to resume thread execution from the same point at a later point in time. It is one of the essential features for multitasking operating system and support for the multi-threaded environment.

### What is Slipped Conditions?
Slipped conditions means, that from the time a thread has checked a certain condition until it acts upon it, the condition has been changed by another thread so that it is errornous for the first thread to act. Here is a simple example:

### What is the major difference between Thread.start() & Thread.run() method?
Thread.start() method (native method) of Thread class does the job of running the Thread A run() method in a thread. So, if we directly call Thread. The run() method also execute in the same thread. Thus it will never solve the purpose of creating a new thread. rnw 


### What is the meaning of Thread Priority?
Every thread has a priority. However, a higher priority also gets precedence in execution. However, it also depends on Thread Scheduler implementation which is OS dependent. It is possible to the change the priority of the thread, but it does not give assurance that higher priority thread will get executed first.

### What join() method does?
The join() method waits for a thread to die. It forces all the running threads to stop executing till the time the thread joins to complete its job.

### What is Java Shutdown Hook?
The Java shutdown hook is used to clean up resources when JVM shuts down. Clean resources mean closing log file, sending some alerts or something else. Shutdown hook needs to be used to execute code before JVM shuts down.

### What are the two main uses of volatile in Java?
Threads are allowed to hold the values of variables in local memory If a variable is marked as volatile, then every time the same variable is used, it must be read from the main memory.
In the same way, every time the variable is written, the value must be stored in main memory.

### volatile is Not Always Enough
The situation where multiple threads are incrementing the same counter is exactly such a situation where a volatile variable is not enough. The following sections explain this case in more detail.   
Imagine if Thread 1 reads a shared counter variable with the value 0 into its CPU cache, increment it to 1 and not write the changed value back into main memory. Thread 2 could then read the same counter variable from main memory where the value of the variable is still 0, into its own CPU cache. Thread 2 could then also increment the counter to 1, and also not write it back to main memory.   
As an alternative to a synchronized block you could also use one of the many atomic data types found in the java.util.concurrent package. For instance, the AtomicLong or AtomicReference or one of the others


### How can you share data between two thread in Java?
We can get data between threads by using a shared object, or concurrent data structure like BlockingQueue. It implements a producer-consumer pattern using wait and notifies methods. It also involves sharing objects between two threads.

### How can multiple threads be controlled simultaneously
Multiple threads can be simultaneously controlled if are created in a ThreadGroup object.


### What is a blocking method in Java?
In Java blocking method is a method which blocks until the task is done. For example, accept () method of ServerSocket blocks until the time a client is connected. Here, blocking refers anything that control will not return to the caller until the task is over.

### What is the main difference between wait () and sleep () method?
* Wait() This method is defined in the Object class. This method releases the lock
* Sleep() The method is defined in Thread class This method never releases the lock.

### What is an immutable object? How can it help in writing a concurrent application?
Any object can be considered unchallengeable if its state does not change after it is constructed. Immutable Objects are used in creating simple, reliable, and concurrent applications.

###  What are the main differences between notify and notifyAll in Java?
Notify () method doesn't provide any way to choose a particular thread, that's why it's only useful when a single While notifyAll() sends a notification to all threads. It also allows them to compete for locks. It also ensures that at least one thread will proceed further.

### Which JVM parameter is used to control the stack size of a thread?
To control the stack size of Thread in Java Xss parameter is used.

### Can you start a thread twice in Java?
No, once a thread is started, it can't be started the second time.

### What is the purpose of using the yield method of thread clas
Yield method is the simplest way to request current thread to relinquish CPU so that other thread. It is a static method and only guarantees that the current thread will relinquish the CPU but doesn't tell anything about which other thread also impacts the CPU.

### What is transient variable?
A transient variable is a variable that can't be serialized during serialization. It is initialized to its default value during the serialization.

### Thread Memory Model

![img](imgs/thread_mem.PNG)

### Thread Signaling wait(), notify() and notifyAll()
Java has a builtin wait mechanism that enable threads to become inactive while waiting for signals. The class java.lang.Object defines three methods, wait(), notify(), and notifyAll(), to facilitate this.    

A thread that calls wait() on any object becomes inactive until another thread calls notify() on that object. In order to call either wait() or notify the calling thread must first obtain the lock on that object. In other words, the calling thread must call wait() or notify() from inside a synchronized block. 

### CountDownLatch
CountDownLatch in Java Concurrency is a type of synchronizer which allows one Thread to wait for one or more Threads before it starts processing.
You can implement the same functionality using wait() & Notify() mechanism but it requires lot of code and getting it write in first attempt is tricky,  With CountDownLatch it can  be done in just few lines.

```text
  final CountDownLatch latch = new CountDownLatch(4);
Thread->
  try
      {
            // carDriver thread is waiting on CountDownLatch to finish
            latch.await();  
            System.out.println("All employees have taken their seat, Driver started the car");
       }
       catch(InterruptedException ie){
           ie.printStackTrace();
       }

```

### CyclicBarrier
There are scenarios in concurrent programming when you want set of threads to wait for each other at a common point until all threads in the set have reached that common point. 
The java.util.concurrent.CyclicBarrier class is a barrier that all threads must wait at, until all threads reach it, before any of the threads can continue.

```
final CyclicBarrier checkPoint = new CyclicBarrier(4, new Runnable(){
            @Override
            public void run(){
                //This task will be executed once all biker threads will reach barrier
                System.out.println("\nAll bikers have arrived to checkpoint. Lets refill the petrol\n");
            }
        });

```
### Difference between CyclicBarrier and CountdownLatch
We have seen how CountDownLatch can be used to implement multiple threads waiting for each other. If you look at CyclicBarrier it also does the same thing but there is a difference: you can not reuse CountDownLatch once the count reaches zero while you can reuse CyclicBarrier by calling reset() method which resets Barrier to its initial State.  
What it implies is that CountDownLatch is good for one-time events like application start-up time and CyclicBarrier can be used in case of the recurrent event e.g. concurrently calculating a solution of the big problem etc.   

Also, the CyclicBarrier uses an all-or-none breakage model for failed synchronization attempts: If a thread leaves a barrier point prematurely because of interruption, failure, or timeout, all other threads waiting at that barrier point will also leave abnormally via BrokenBarrierException (or InterruptedException if they too were interrupted at about the same time). Hence CyclicBarrier can be used for exiting multiple threads if one thread fails


### Semaphores
A Semaphore is a thread synchronization construct that can be used either to send signals between threads to avoid missed signals, or to guard a critical section like you would with a lock. 

* Using Semaphores for Signaling
```
Semaphore semaphore = new Semaphore();

Thread 1 -> //do something, then signal
            semaphore.take()
Thread 2 -> 
        semaphore.release()
         //receive signal, then do something...
```

* Using Semaphores for Locks
```
semaphore.take();
 
try{
  //critical section
} finally {
  semaphore.release();
}
```


### Blocking Queue
A blocking queue is a queue that blocks when you try to dequeue from it and the queue is empty, or if you try to enqueue items to it and the queue is already full. A thread trying to dequeue from an empty queue is blocked until some other thread inserts an item into the queue. A thread trying to enqueue an item in a full queue is blocked until some other thread makes space in the queue, either by dequeuing one or more items or clearing the queue completely.


### Is Java a compiled or an interpreted language?

The answer to this question lies in the fact that the Java Virtual Machine (JVM) converts Java code to platform-independent bytecode, which is then converted to machine code in binary form with the help of the Just-in-Time (JIT) compiler. We can say that Java uses both approaches to run its programs. The JIT compiler is a part of the JVM that improves performance by compiling bytecode to native code for repeated method calls. This shows the close relationship between the JVM and JIT compiler. Let us briefly explain what JVM and JIT are and then move on to see the differences between them.


#### JVM
The Java Virtual Machine is an abstract computing and virtual machine interface that drives the java code. It is a part of the Java Runtime Environment (JRE) that compiles bytecode into machine code for program execution by the CPU. Bytecode entering the JVM undergoes three phases after which it is compiled to machine code.
* Loading: The referenced classes or methods are loaded using the class loader.
 * Verifying: The bytecode verifier checks the bytecode for instructions that may cause any harm for the present or future executions.
 * Initialisation and conversion: All static variables are assigned their values defined in the code or static block. Finally, the JIT plays its role by compiling the bytecode to machine code.

#### JIT
As mentioned before, the JIT compiler compiles bytecode to machine code “just-in-time” for it to run. By default, the JIT compiler is enabled and is activated on the calling of a Java method. It can be disabled to check and diagnose Java compilation problems. For other reasons, it is not recommended as it may slow down your code by running it in interpreter-only mode. The JIT compiler helps optimise and maximise the performance of complex Java programs without consuming processor time and memory space. It also keeps track of operational data during runtime, which can be used to improve future recompilations.

#### How does it work with the JVM?
The differences between the JVM and JIT can be highlighted while discussing the coordination between them during Java program execution.

The first time a method is called, it’s not compiled. For every method, JVM maintains a count to keep track of the number of times that method is called. It interprets the method until the count reaches a JIT compilation threshold. 

After the method is compiled, subsequent calls to the method are counted and upon reaching the JIT compilation threshold, JIT compiles the method a second time implementing more optimisations to increase performance. This is repeated until maximum optimisation level is attained

#### How does the JRE play a role in executing a java program?

The Java Runtime Environment provides a platform to run and execute the source code. It contains the JVM and provides the libraries to execute the program. The JVM, in turn, contains the JIT compiler. The JRE is a minimum requirement to run Java applications on any computer. It is platform-dependent.
