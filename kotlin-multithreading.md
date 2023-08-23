# Kotlin - Multithreading

```kotlin
class SimpleThread: Thread() {
    public override fun run() {
        println("${Thread.currentThread()} has run.")
    }
}

class SimpleRunnable: Runnable {
    public override fun run() {
        println("${Thread.currentThread()} has run.")
    }
}

fun main(args: Array<String>) {
    val thread = SimpleThread()
    thread.start() // Will output: Thread[Thread-0,5,main] has run.
    val runnable = SimpleRunnable()
    val thread1 = Thread(runnable)
    thread1.start() // Will output: Thread[Thread-1,5,main] has run
}
```

<figure><img src=".gitbook/assets/image.png" alt=""><figcaption><p>Font: YouTube</p></figcaption></figure>
