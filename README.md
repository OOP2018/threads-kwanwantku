## Threads and Synchronization

This lab illustrates the problem of synchronization when many threads are operating on a shared object.  The general issue is called "thread safety", and it is a major cause of errors in computer software.

## Assignment

To the problems on the lab sheet and record your answers here.

1. Record average run times.
2. Write your explanation of the results.  Use good English and proper grammar.  Also use good Markdown formatting.

## ThreadCount run times

These are the average runtime using 3 or more runs of the application.
The Counter class is the object being shared by the threads.
The threads use the counter to add and subtract values.

| Counter class           | Limit              | Runtime (sec)   |
|:------------------------|:-------------------|-----------------|
| Unsynchronized counter  |  10,000,000        |  0.02178767     |
| Using ReentrantLock     |  10,000,000        |  2.35430067     |
| Syncronized method      |  10,000,000        |  0.89897267     |
| AtomicLong for total    |  10,000,000        |  0.48312433     |

## 1. Using unsynchronized counter object
	1.1. The total not always same but the total should be zero Because They using the same counter and also running parallel each other together. The two thread aren’t exactly inter-leaved. 
	Sometimes, the second thread seems to jump ahead of the 1st thread. So, this is why counter is not zero and not same each time.
	limit -> 1000
	--------------------------------------
	first running time ->  0.000625 sec. 
	total -> 9808
	second running time -> 0.000783 sec. 
	total -> 78902
	third running time -> 0.001381 sec.
	total -> -24658
	fourth running time ->  0.001864 sec.
	total -> 0
	fifth running time -> 0.022830 sec. 
	total -> 0
	running time average -> 0.001072 sec.
	
	1.2. limit -> 10,000,000
	first running time ->  0.023360 sec.
	second running time -> 0.019173 sec.
	third running time -> 0.022830 sec.
	running time average -> 0.02178767 sec.

## 2. Implications for Multi-threaded Applications
	It effect to getting the correct amount, when they do any transaction likes
	deposit, withdraw or transfer. They using same thread to deposit or withdraw. 
	It can occur to get the minus amount likes -100 baht from withdraw but real is 
	0 baht and deposit money 100 baht but show amount 100 baht because from sharing
	thread together (using same counter) and running same time. It’s called race condition. 

## 3. Counter with ReentrantLock

	3.1. It's always zero.
	limit -> 10,000,000
	first running time -> 1.968739 sec.
	second running time -> 2.393264 sec.
	third running time -> 2.700899 sec.
	running time average -> 2.35430067 sec.
	
	3.2. Because using lock doesn't have jump a head for each thread. 
	They running first task until finish, The second task can run after that. 
	It's not like unsynchronized counter that do first task and second task go 
	to use the same resource when first task doesn't finish.
	
	3.3. ReentrantLock can choose threat to using resource by order and manipulated
	the task that already using resource or do something by protected the another
	task to not using resource on the same time. It using it when the task using
	resource to protect the another task.
	
	3.4. Because to make the task using resource or do something finish 
	before called the next task to use it for run thread.
## 4. Counter with synchronized method
	4.1. The total always zero
		first running time ->   0.836344 sec.
		second running time -> 0.932210 sec.
		third running time -> 0.928364 sec.
		running time average -> 0.89897267 sec.
	4.2 Becaues the synchronus are allow only one thread and opposite to asynchronus that do first thread finish and next thread can do it.
	4.3 Synchronized mean the task cannot be executed by two times at the same time. Use it when have the same task and using same resource to avoid race condition.

## 5. Counter with AtomicLong
	5.1. Because AtomicCounter already have lock and unlock in their own. So, It can use not synchronized method.
	5.2. When you have a lot of thread to using resource.
## 6. Analysis of Results
	6.1. AtomicLong > not Synchronized > ReentrantLock 
	6.2. Synchronized method because it's using not too much time but if you have a lot of thread I recommend to use ReentrantLock because it's suitable for a lot of thread.

## 7. Using Many Threads (optional)

