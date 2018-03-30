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
| Using ReentrantLock     |                    |                 |
| Syncronized method      |                    |                 |
| AtomicLong for total    |                    |                 |

## 1. Using unsynchronized counter object
1.1. The total not always same but the total should be zero because each thread are running parallel to return the total.
1.2. limit = 10,000,000 running time = 0.02178767.

## 2. Implications for Multi-threaded Applications
It effect to getting the correct amount, when they do any transaction likes deposit, withdraw or transfer. They using same thread to deposit or withdraw. It can occur to get the minus amount likes -100 because from sharing thread together. It can occur this. It’s called race condition. I suggested to separate thread to reduce this problem.

## 3. Counter with ReentrantLock

answer questions 3.1 - 3.4

## 4. Counter with synchronized method

answer question 4

## 5. Counter with AtomicLong

answer question 5

## 6. Analysis of Results

answer question 6

## 7. Using Many Threads (optional)

