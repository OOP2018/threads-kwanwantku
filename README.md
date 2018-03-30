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
| Syncronized method      |                    |                 |
| AtomicLong for total    |                    |                 |

## 1. Using unsynchronized counter object
1.1. The total not always same but the total should be zero Because They using the same counter and also running parallel each other together. The two thread aren’t exactly inter-leaved. Sometimes, the second thread seems to jump ahead of the 1st thread. So, this is why counter is not zero and not same each time.\n\n
 limit = 1000\n
first running time =  0.000625 sec. total = 9808\n
second running time =  0.000783 sec. total = 78902\n
third running time = 0.001381 sec. total = -24658 \n
fourth running time =  0.001864 sec. total = 0\n
fifth running time = 0.022830 sec. total = 0\n
running time average = 0.001072 sec.\n\n
1.2. limit = 10,000,000\n
first running time =  0.023360 sec.\n
second running time = 0.019173 sec.\n
third running time = 0.022830 sec.\n
running time average = 0.02178767 sec.\n

## 2. Implications for Multi-threaded Applications
It effect to getting the correct amount, when they do any transaction likes deposit, withdraw or transfer. They using same thread to deposit or withdraw. It can occur to get the minus amount likes -100 baht from withdraw but real is 0 baht and deposit money 100 baht but show amount 100 baht because from sharing thread together (using same counter) and running same time. It’s called race condition. 

## 3. Counter with ReentrantLock

3.1. It's always zero.\n
limit = 10,000,000 \n
first running time = 1.968739 sec.\n
second running time = 2.393264 sec.\n
third running time = 2.700899 sec. \n
running time average = 2.35430067 sec. \n\n
3.2. Because using lock doesn't have jump a head for each thread. They running first task until finish, The second task can run after that. It's not like unsynchronized counter that do first task and second task go to use the same resource when first task doesn't finish. \n\n
3.3. ReentrantLock can choose threat to using resource by order and manipulated the task that already using resource or do something by protected the another task to not using resource on the same time. It using it when the task using resource to protect the another task.\n\n
3.4. Because to make the task using resource or do something finish before called the next task to use it for run thread.\n
## 4. Counter with synchronized method
4.1.It's total equals to zero.

## 5. Counter with AtomicLong

answer question 5

## 6. Analysis of Results

answer question 6

## 7. Using Many Threads (optional)

