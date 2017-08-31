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


  // throwing exception

  if (salary < 0) {
    throw new IllegalArgumentException('Blah Blah Here');
  }

```


### Polymorphic Processing And operator instanceof

```java

  // Processing Polymorphism
  // Create Employee data type array
  Employee[] employees = new Employee[4];
  // Add employee object to employees array
  employees[0] = em1;
  employees[1] = em2;
  employees[2] = em3;

  for (Employee currentEmp : employee ) {  
    // Code Here

    //invoking toString Function of java
    System.out.println(currentEmp); // This will call the toString Function

    // Using instanceof
    if (currentEmp instanceof BasePlusCommissionEmployee) {
      BasePlusCommissionEmployee employee = (BasePlusCommissionEmployee) currentEmp;
      // The Original Data Type of currentEmp is Employee and we Downcast it to
      // the child data type BasePlusCommissionEmployee
    }
  }

  // getting a name of Class object

  em1.getClass().getName(); // This will return the name of class


```
