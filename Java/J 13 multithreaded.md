
## Chapter 11 : Multithreaded Programming

Key Skills & Concepts
●Understand multithreading fundamentals
●Know the Thread class and the Runnable interface
●Create a thread
●Create multiple threads
●Determine when a thread ends
●Use thread priorities
●Understand thread synchronization
●Use synchronized methods
●Use synchronized blocks
●Communicate between threads
●Suspend, resume, and stop threads

A multithreaded program contains two or more
parts that can run concurrently. Each part of such a program is called a thread, and each thread
defines a separate path of execution. Thus, multithreading is a specialized form of multitasking.

___

#### Multithreading Fundamentals

There are two distinct types of multitasking: process-based and thread-based.


A process is, in essence, a program that is executing. 
In process-based multitasking, a program is the smallest unit of code that can be dispatched by the scheduler.


Thus, process-based multitasking is the feature that allows your computer to run two or more
programs concurrently.  
For example, it is process-based multitasking that allows you to run the Java compiler at the same time you are using a text editor or browsing the Internet. 



In a thread-based multitasking environment, the thread is the smallest unit of dispatchable code. This means that a single program can perform two or more tasks at once. 

For instance, a text editor can be formatting text at the same time that it is printing, as long as these two
actions are being performed by two separate threads.

> Process-based multitasking is not under the control of Java. Multithreaded multitasking is.

By using multithreading, your program can execute another task during idle time. 

In a single-core system, two or more threads do not actually run at the same time, but idle CPU time is utilized by sharing CPU time.

In multiprocessor/multicore systems, it is possible for two or more threads to actually execute simultaneously.


___

A thread can be in one of several states. It can be running.

It can be ready to run as soon as it gets CPU time. 

A running thread can be suspended, which is a temporary halt to its execution.

It can later be resumed. 

A thread can be blocked when waiting for a resource. 

A thread can be terminated, in which case its execution ends and cannot be resumed.

Along with thread-based multitasking comes the need for a special type of feature called synchronization, which allows the execution of threads to be coordinated in certain well-defined ways. 

Java has a complete subsystem devoted to synchronization.

___

#### The Thread Class and Runnable Interface

Java’s multithreading system is built upon the Thread class and its companion interface, Runnable. Both are packaged in java.lang. 

Thread encapsulates a thread of execution. To create a new thread, your program will either extend Thread or implement the Runnable interface.

The Thread class defines several methods that help manage threads.

Common Thread Methods in Java

|**Method**|**Description**|
|---|---|
|`final String getName()`|Obtains a thread’s name.|
|`final int getPriority()`|Obtains a thread’s priority.|
|`final boolean isAlive()`|Determines whether a thread is still running.|
|`final void join()`|Waits for a thread to terminate.|
|`void run()`|Entry point for the thread.|
|`static void sleep(long milliseconds)`|Suspends a thread for a specified period of milliseconds.|
|`void start()`|Starts a thread by calling its `run()` method.|

All processes have at least one thread of execution, which is usually called the main thread. From the main thread, you can create other threads.

___

#### Creating a Thread

You create a thread by instantiating an object of type Thread. The Thread class encapsulates an object that is runnable. 

As mentioned, Java defines two ways in which you can create a runnable object:
●You can implement the Runnable interface.
●You can extend the Thread class.

Both approaches still use the Thread class to instantiate, access, and control the thread. The only difference is how a thread-enabled class is created.

The Runnable interface abstracts a unit of executable code. You can construct a thread on any object that implements the Runnable interface.

Runnable defines only one method called run( ), which is declared like this:
`public void run( )`

Inside run( ), you will define the code that constitutes the new thread. It is important to understand that run( ) can call other methods, use other classes, and declare variables just like the main thread. 

The only difference is that run( ) establishes the entry point for another, concurrent thread of execution within your program. This thread will end when run( ) returns. 

After you have created a class that implements Runnable, you will instantiate an object of type Thread on an object of that class. 

Thread defines several constructors. The one that we will use first is shown here:
`Thread(Runnable threadOb)`

In this constructor, threadOb is an instance of a class that implements the Runnable interface. This defines where execution of the thread will begin.

Once created, the new thread will not start running until you call its start( ) method, which is declared within Thread. In essence, start( ) executes a call to run( ).

___

#### Creating a Thread in Java

To perform tasks concurrently in Java, you can create and run multiple threads. A thread is a separate path of execution. Java provides two main ways to create a thread:

**Note:** In both cases, you're still using the `Thread` class to manage and start the thread. The difference is only in how you _create_ the thread logic.

Don’t call `run()` directly — it will just run like a normal method. You must call `start()` to launch a new thread.

##### 1. Implementing the `Runnable` Interface

You can create a class that implements the `Runnable` interface. This interface requires you to define the `run()` method, which contains the code that will run in the new thread.

This is like saying: _“Hey, I’ll write a class that contains code I want the thread to run.”_

Your class implements `Runnable`, which means you must write the `run()` method inside it.

```java
class MyRunnable implements Runnable {
    public void run() {
        // code that runs in the new thread
    }
}
```

for starting a thread
```java
MyRunnable obj = new MyRunnable();
Thread t = new Thread(obj); // pass your runnable object to a new Thread
t.start(); // this begins execution

```

```java
class MyRunnable implements Runnable {
    public void run() {
        System.out.println("Thread is running using Runnable");
    }
}

public class Main {
    public static void main(String[] args) {
        MyRunnable myRunnable = new MyRunnable();
        Thread thread = new Thread(myRunnable);
        thread.start(); // Starts the thread and runs the run() method
    }
}
```

##### 2. Extending the `Thread` Class

Alternatively, you can create a class that extends the `Thread` class and override its `run()` method.

Here, your class **is** a thread. You extend the `Thread` class and override the `run()` method.
```java
class MyThread extends Thread {
    public void run() {
        // code that runs in the new thread
    }
}
```

Starting the thread
```java
MyThread obj = new MyThread();
obj.start(); // this begins execution
```


```java
class MyThread extends Thread {
    public void run() {
        System.out.println("Thread is running using Thread class");
    }
}

public class Main {
    public static void main(String[] args) {
        MyThread thread = new MyThread();
        thread.start(); // Starts the thread and runs the run() method
    }
}
```

#### Key Points

- The `run()` method contains the code that defines the behavior of the thread.
- The thread does not start running until you call the `start()` method.
- Calling `run()` directly does not start a new thread; it simply executes the method on the current thread.
- The `start()` method calls the `run()` method internally on a new thread of execution.

#### Thread Constructor (Runnable)

When using the `Runnable` interface, you typically create a thread like this:
```java
Thread thread = new Thread(runnableObject);
```
Here, `runnableObject` is an instance of a class that implements `Runnable`. The thread will execute the `run()` method of that object when started.

---


Objects of MyThread can be run in their own threads because MyThread implements Runnable.

```java
// Create a thread by implementing Runnable

class MyThread implements Runnable
{
	String threadName;
	
	MyThread(String name)
	{
		threadName = name;
	}
	
	// Entry Point of thread
	public void run()
	{
		System.out.println(threadName + "Starting.");
		
		try
		{
			for(int count=0; count<10; count++)
			{
				Thread.sleep(400);
				System.out.println("In " + threadName + ", count is " + count);
			}
		}
		
		catch(InterruptedException exc)
		{
			System.out.println(threadName + " interrupted.");
		}
		System.out.println(threadName + " terminating.");
	}
}


class UseThreads
{
	public static void main(String[] args) 
	{
		System.out.println("Main thread starting.");
	
		// First, construct a MyThread object.
		MyThread mt = new MyThread("Child #1");
		
		// Next, construct a thread from that object.
		Thread newThrd = new Thread(mt);

		// Finally, start execution of the thread.
		newThrd.start();


		for(int i=0; i<50; i++) 
		{
			System.out.print(".");
			try 
			{
				Thread.sleep(100);
			}
			catch(InterruptedException exc) 
			{
				System.out.println("Main thread interrupted.");
			}
		}
		System.out.println("Main thread ending.");
	}
}
```

First, MyThread implements Runnable. 

This means that an object of type MyThread is suitable for use as a thread and can be passed to the Thread constructor.

Inside run( ), a loop is established that counts from 0 to 9. Notice the call to sleep( ). The sleep( ) method causes the thread from which it is called to suspend execution for the specified period of milliseconds.

The number of milliseconds to suspend is specified in milliseconds. This method can throw an
InterruptedException. Thus, calls to it must be wrapped in a try block.

Inside main( ), a new Thread object is created.

first an object of MyThread is created. This object is then used to
construct a Thread object. This is possible because MyThread implements Runnable. Finally,
execution of the new thread is started by calling start( ). This causes the child thread’s run( )
method to begin.

After calling start( ), execution returns to main( ), and it enters main( )’s for
loop. Notice that this loop iterates 50 times, pausing 100 milliseconds each time through the loop.
Both threads continue running, sharing the CPU in single-CPU systems, until their loops finish.


To illustrate the
fact that the main thread and mt execute concurrently, it is necessary to keep main( ) from
terminating until mt is finished.
Java
provides much better ways of waiting for a thread to end.

One other point: In a multithreaded program, you often will want the main thread to be
the last thread to finish running. As a general rule, a program continues to run until all of
its threads have ended. Thus, having the main thread finish last is not a requirement. It is,
however, often a good practice to follow—especially when you are first learning about threads.

____

```java
// MyThread variations. This version of MyThread
// creates a Thread when its constructor is called and
// stores it in an instance variable called thrd.
// It also sets the name of the thread and provides
// a factory method to create and start a thread.


class MyThread implements Runnable
{
	Thread thrd;
	
	MyThread(String name)
	{
		thrd = new Thread(this, name);
	}

	// A factory method that creates and starts a thread.
	public static MyThread createAndStart(String name) 
	{
		MyThread myThrd = new MyThread(name);
		myThrd.thrd.start(); // start the thread
		return myThrd;
}

	// Entry Point of thread
	public void run()
	{
		System.out.println(thrd.getName() + "Starting.");
		
		try
		{
			for(int count=0; count<10; count++)
			{
				Thread.sleep(400);
				System.out.println("In " + thrd.getName() + ", count is " + count);
			}
		}
		
		catch(InterruptedException exc)
		{
			System.out.println(thrd.getName() + " interrupted.");
		}
		System.out.println(thrd.getName() + " terminating.");
	}
}


class ThreadVariations
{
	public static void main(String[] args) 
	{
		System.out.println("Main thread starting.");
	
		// Create and start a thread
		MyThread mt = MyThread.createAndStart("Child #1");
		// now thread starts when it is created
		
		for(int i=0; i<50; i++) 
		{
			System.out.print(".");
			try 
			{
				Thread.sleep(100);
			}
			catch(InterruptedException exc) 
			{
				System.out.println("Main thread interrupted.");
			}
		}
		System.out.println("Main thread ending.");
	}
}
```

MyThread
no longer contains the name of the thread. Instead, it provides an instance variable called thrd
that holds a reference to the Thread object created by MyThread’s constructor, shown here:
```java
MyThread(String name) {
	thrd = new Thread(this, name);
}
```

after MyThread’s constructor executes, thrd will contain a reference to the newly created thread.

To start the thread, you will simply call start( ) on thrd.

```java
// A factory method that creates and starts a thread.
public static MyThread createAndStart(String name) {
	MyThread myThrd = new MyThread(name);
	myThrd.thrd.start(); // start the thread
	return myThrd;
}
```

When this method is called, it creates a new instance of MyThread called myThrd. It then
calls start( ) on myThrd’s copy of thrd. Finally, it returns a reference to the newly created
MyThread instance. Thus, once the call to createAndStart( ) returns, the thread will already
have been started. Therefore, in main( ), this line creates and begins the execution of a thread
in a single call:

```java
MyThread mt = MyThread.createAndStart("Child #1");
```

_____

#### Extending Thread

```java
class MyThread extends Thread
{
	MyThread(String name)
	{
		super(name);  
	}
	
	public void run()
	{
		System.out.println(getName() + " starting.");
		
		try
		{
			for(int count=0; count<10; count++)
			{
				Thread.sleep(400);
				System.out.println("In " + getName() + ", count is " + count);
			}
		}
		System.out.println(getName() + " terminating.");
	}
}

class ExtendedThread
{
	public static void main(String[] args) 
	{
		System.out.println("Main thread starting.");
		
		MyThread mt = new MyThread("Child #1");
		mt.start();
		
		for(int i=0; i<50; i++)
		{
			System.out.print(".");
			try
			{
				Thread.sleep(100);
			}
			catch(InterruptedException exc)
			{
				System.out.println("Main thread interrupted.");
			}
		}
		System.out.println("Main thread ending.");
	}
}
```

___

#### Creating Multiple Threads



```java
// Create multiple threads.

class MyThread implements Runnable 
{
	Thread thrd;

	// Construct a new thread.
	MyThread(String name) 
	{
		thrd = new Thread(this, name);
	}

	// A factory method that creates and starts a thread.
	public static MyThread createAndStart(String name) 
	{
		MyThread myThrd = new MyThread(name);
		myThrd.thrd.start(); // start the thread
		return myThrd;
	}
	
	// Entry point of thread.
	public void run() 
	{
		System.out.println(thrd.getName() + " starting.");
		try 
		{
			for(int count=0; count < 10; count++) 
			{
				Thread.sleep(400);
				System.out.println("In " + thrd.getName() + ", count is " + count);
			}
		}
		catch(InterruptedException exc) 
		{
			System.out.println(thrd.getName() + " interrupted.");
		}
		System.out.println(thrd.getName() + " terminating.");
	}
}


class MoreThreads 
{
	public static void main(String[] args) 
	{
		System.out.println("Main thread starting.");
		MyThread mt1 = MyThread.createAndStart("Child #1");
		MyThread mt2 = MyThread.createAndStart("Child #2");
		MyThread mt3 = MyThread.createAndStart("Child #3");
		
		for(int i=0; i < 50; i++) 
		{
			System.out.print(".");
			try 
			{
				Thread.sleep(100);
			}
			catch(InterruptedException exc) 
			{
				System.out.println("Main thread interrupted.");
			}
		}
		System.out.println("Main thread ending.");
	}
}
```


___

#### Determining When a Thread Ends

Thread provides two means by which you can determine if a thread has ended. First, you can call isAlive( ) on the thread. Its general form is shown here:
`final boolean isAlive( )`

The isAlive( ) method returns true if the thread upon which it is called is still running. It returns false otherwise.

```java
class MoreThreads 
{
	public static void main(String[] args) 
	{
		System.out.println("Main thread starting.");
		MyThread mt1 = MyThread.createAndStart("Child #1");
		MyThread mt2 = MyThread.createAndStart("Child #2");
		MyThread mt3 = MyThread.createAndStart("Child #3");
		
		do 
		{
			System.out.print(".");
			try 
			{
				Thread.sleep(100);
			}
			catch(InterruptedException exc) 
			{
				System.out.println("Main thread interrupted.");
			}
		}
		while(mt1.thrd.isAlive() || 
			mt2.thrd.isAlive() ||
			mt3.thrd.isAlive() );
		
		System.out.println("Main thread ending.");
	}
}
```

```
while(mt1.thrd.isAlive() || 
			mt2.thrd.isAlive() ||
			mt3.thrd.isAlive() );
```
will keep running till all become false which is when all threads terminate and only after that the main thread will terminate.

___


Another way to wait for a thread to finish is to call join( ), shown here:

`final void join( ) throws InterruptedException`


This method waits until the thread on which it is called terminates. Its name comes from the
concept of the calling thread waiting until the specified thread joins it. Additional forms of
join( ) allow you to specify a maximum amount of time that you want to wait for the specified
thread to terminate.

```java
class JoinThreads 
{
	public static void main(String[] args) 
	{
		System.out.println("Main thread starting.");
		
		MyThread mt1 = MyThread.createAndStart("Child #1");
		MyThread mt2 = MyThread.createAndStart("Child #2");
		MyThread mt3 = MyThread.createAndStart("Child #3");

		try 
		{
			mt1.thrd.join();
			System.out.println("Child #1 joined.");
			
			mt2.thrd.join();
			System.out.println("Child #2 joined.");
			
			mt3.thrd.join();
			System.out.println("Child #3 joined.");
		}
		catch(InterruptedException exc) 
		{
			System.out.println("Main thread interrupted.");
		}
		System.out.println("Main thread ending.");
	}
}
```

```
.
.
.
.
In Child #2, count is 8
In Child #1, count is 8
In Child #3, count is 9
Child #3 terminating.
In Child #2, count is 9
Child #2 terminating.
In Child #1, count is 9
Child #1 terminating.
Child #1 joined.
Child #2 joined.
Child #3 joined.
Main thread ending.
```

after the calls to join( ) return, the threads have stopped executing.

___

#### Thread Priorities

Each thread has associated with it a priority setting. A thread’s priority determines, in part,
how much CPU time a thread receives relative to the other active threads.

When a child thread is started, its priority setting is equal to that of its parent thread. You can change a thread’s priority by calling setPriority( ), which is a member of Thread.

`final void setPriority(int level)`

You can obtain the current priority setting by calling the getPriority( ) method of Thread.

`final int getPriority( )`

___

#### Synchronization

When using multiple threads, it is sometimes necessary to coordinate the activities of two
or more. The process by which this is achieved is called synchronization. The most common
reason for synchronization is when two or more threads need access to a shared resource
that can be used by only one thread at a time.

Key to synchronization in Java is the concept of the monitor, which controls access to an
object. A monitor works by implementing the concept of a lock. When an object is locked by
one thread, no other thread can gain access to the object. When the thread exits, the object is
unlocked and is available for use by another thread.

All objects in Java have a monitor. This feature is built into the Java language itself. Thus,
all objects can be synchronized. Synchronization is supported by the keyword synchronized
and a few well-defined methods that all objects have.

There are two ways that you can synchronize your code. Both involve the use of the
synchronized keyword

#### Using Synchronized Methods

You can synchronize access to a method by modifying it with the synchronized keyword.
When that method is called, the calling thread enters the object’s monitor, which then locks
the object. While locked, no other thread can enter the method, or enter any other synchronized
method defined by the object’s class.

When the thread returns from the method, the monitor
unlocks the object, allowing it to be used by the next thread. Thus, synchronization is achieved
with virtually no programming effort on your part.

```java
class SumArray 
{
	private int sum;

	synchronized int sumArray(int[] nums) 
	{
		sum = 0; // reset sum
		
		for(int i=0; i<nums.length; i++) 
		{
			sum += nums[i];
			System.out.println("Running total for " +
			Thread.currentThread().getName() +
			" is " + sum);
			try {
```


#### The synchronized Statement

you might want
to synchronize access to some method that is not modified by synchronized. This can occur
because you want to use a class that was not created by you but by a third party, and you do
not have access to the source code. Thus, it is not possible for you to add synchronized to the
appropriate methods within the class.

You simply put calls to the methods defined
by this class inside a synchronized block.
```
synchronized(objref) {
	// statements to be synchronized
}
```

objref is a reference to the object being synchronized. Once a synchronized block has
been entered, no other thread can call a synchronized method on the object referred to by
objref until the block has been exited.

```
// synchronize calls to sumArray()

synchronized(sa) 
{
	answer = sa.sumArray(a);
}
```

___

#### Thread Communication Using notify( ), wait( ), and notifyAll( )





#### Suspending, Resuming, and Stopping Threads





____