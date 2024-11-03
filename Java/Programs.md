## Thread Synchronization

```java
public class Counter {

  private int c = 0;
  
  public int getCount() {

    return this.c;

  };

  public void setCount(int c) {

    this.c = c;

  };
  public synchronized void increment() {

    this.setCount(this.getCount() + 1);

  }

  public static void main(String[] args) throws InterruptedException {

    Counter c = new Counter();

    Thread a = new Thread(() -> {

      for (int i = 0; i < 100; i++) {

        c.increment();

        try {

          Thread.sleep(10);

        } catch (InterruptedException e) {

          System.out.println(e);

        }

      }

    });

    Thread b = new Thread(() -> {

      for (int i = 0; i < 100; i++) {

        c.increment();

        try {

          Thread.sleep(10);

        } catch (InterruptedException e) {

          System.out.println(e);

        }

      }

    });

    // Start both threads here

    a.start();

    b.start();

    // Join both threads here

    a.join();

    b.join();  

    System.out.println("Counter: " + c.getCount());

  }

}
```

