Before Learning volatile and Atomic keyword, first understand that What problems do we have in java memory model. Lets consider a simple class

```java
class Test {
    private int a;

    public int getValue() {
        return a;
    }

    public void increment() {
        a++;
    }
}
```

Now, this works perfectly fine in a single threaded environment, but in multi-threaded environment this implementation can go for a toss since there are multiple threads who are incrementing and reading the value of `a`. 

If one thread changes the value of `a` which is not visible to the other thread, it is called `Visibility` problem. 

Another problem is when 1 thread is increments the value of a, another threads also reads the old value before prev thread has written its value of a in memory, other thread reads the old value and might override the prev threads value. This is called `Synchronization` problem.

Visibility problem is linked to java memory model, so every threads has its own local thread cache and it's writes and reads the values from it's local cache first instead of main memory.

### Volatile Keyword
Volatile keyword solve the visibility problem. So instead of a thread writing to their local cache, it directly writes the value to the main memory making it visible for other threads.

```java
class Test {
    private volatile int a;

    public int getValue() {
        return a;
    }

    public void increment() {
        a++;
    }
}
```

### Atomic variables
Now the visibility problem is solved, but still we've synchronization issue and this can be solved by synchronized keyword but it can create a bottleneck and it's not the most elegant solution to this problem.

Atomic variable make the reading the variable values and writing it back atomic and therefore it is best suited to solve synchronization problems.

```java
class Test {
    private final AtomicInteger a = new AtomicInteger(0);

    public int getValue() {
        return a.get();
    }

    public void increment() {
        a.incrementAndGet();
    }
}
```

Atomic variable solves the problem related to both Visibility and Synchronization.