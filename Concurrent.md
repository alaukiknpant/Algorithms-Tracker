### Concurrency Problems


- [Print In Order](https://leetcode.com/problems/print-in-order/submissions/)
  ```java
  class Foo {

      private AtomicInteger firstDone = new AtomicInteger(0);
      private AtomicInteger secondDone = new AtomicInteger(0);


      public Foo() {

      }

      public void first(Runnable printFirst) throws InterruptedException {

          // printFirst.run() outputs "first". Do not change or remove this line.
          printFirst.run();
          firstDone.incrementAndGet();
      }

      public void second(Runnable printSecond) throws InterruptedException {
          while (firstDone.get() != 1) {

          }

          // printSecond.run() outputs "second". Do not change or remove this line.
          printSecond.run();
          secondDone.incrementAndGet();
      }

      public void third(Runnable printThird) throws InterruptedException {
           while (secondDone.get() != 1) {

          }
          // printThird.run() outputs "third". Do not change or remove this line.
          printThird.run();
      }
  }
  ```
  
  
  
