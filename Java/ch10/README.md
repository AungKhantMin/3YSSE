# Polymorphism in Java

### Abstract Class And Abstract Method

```java

  // Declaring Abstract Class

  public abstract class Test{
    // Your Code Here

    // Declaring Abstract Method
    public abstract double test();

    // Overriding A Method
    @Override
    public String toString(){
      return "test";
    }


  }


  // Extending The Parent Class

  public class TestExtends extends Test {
    super('Variable For Parent Constructor');

    // We Must Override the abstract method of a abstract class if we extends the abstract class
    @Override
    public double test(){
      return 0.3;
    }
  }

```
