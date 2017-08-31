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




###  Interface


```java

  // Creating an Interface

  public interface Payable{
    double getAmount(); // no need public keyword
  }

  // implementing Interface

  public class TestPay implements Payable {
    // Like Abstract class we need to Override the interface method

    @Override
    public double getAmount(){
      return 34.00; // any double value can return
    }
  }

  // implementing interface from a child method of an Abstract class which implement interface

  public abstract class Test implements Payable{
    // We will not Override the interface method in This Class
  }

  public class TestAbs extends Test{
    // We will Override The Interface method here

    @Override
    public double getAmount(){
      return 345.6;
    }
  }

```


### Here is Present For Chapter 10 Problem 8 Answer

#### BasePlusCommissionEmployee.java


```java

/*
 * The MIT License
 *
 * Copyright 2017 aungkhantmin.
 *
 * Permission is hereby granted, free of charge, to any person obtaining a copy
 * of this software and associated documentation files (the "Software"), to deal
 * in the Software without restriction, including without limitation the rights
 * to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
 * copies of the Software, and to permit persons to whom the Software is
 * furnished to do so, subject to the following conditions:
 *
 * The above copyright notice and this permission notice shall be included in
 * all copies or substantial portions of the Software.
 *
 * THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
 * IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
 * FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
 * AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
 * LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
 * OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
 * THE SOFTWARE.
 */
package problem10_8;

/**
 *
 * @author aungkhantmin
 */
public class BasePlusCommissionEmployee extends CommissionEmployee {

    private double salary;

    public BasePlusCommissionEmployee(String fN, String lN, String sSN, EmpDate bD,
            double gS, double cR, double sy) {
        super(fN, lN, sSN, bD, gS, cR);
        setSalary(sy);
    }



    public void setSalary(double sy){
        if (sy >= 0.0 ){
            salary =sy;
        }
        else{
            throw new IllegalArgumentException(
            "Basesalary must be >= 0.0 ");
        }
    }

    public double getSalary(){
        return salary;
    }

    @Override
    public double earnings(){
        return getSalary() * super.earnings();
    }

    @Override
    public String toString(){
        return String.format("%s %s; %s: %,.2f",
                "base-salaried",super.toString(),
                "base salary", getSalary());
    }

}


```

### CommissionEmployee.java

```java

/*
* The MIT License
*
* Copyright 2017 aungkhantmin.
*
* Permission is hereby granted, free of charge, to any person obtaining a copy
* of this software and associated documentation files (the "Software"), to deal
* in the Software without restriction, including without limitation the rights
* to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
* copies of the Software, and to permit persons to whom the Software is
* furnished to do so, subject to the following conditions:
*
* The above copyright notice and this permission notice shall be included in
* all copies or substantial portions of the Software.
*
* THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
* IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
* FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
* AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
* LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
* OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
* THE SOFTWARE.
*/
package problem10_8;

/**
*
* @author aungkhantmin
*/
public class CommissionEmployee extends Employee{

  private double grossSale;
  private double commissionRate;

  public CommissionEmployee(String fN, String lN, String sSN, EmpDate bD,
          double gS, double cR) {
      super(fN, lN, sSN, bD);
      setGrossSale(gS);
      setCommissionRate(cR);
  }

  public void setGrossSale(double gS){
      if (gS >= 0.0){
          grossSale = gS;
      }
      else{
          throw new IllegalArgumentException(
                  "Gross Sale must be >= 0.0");
      }
  }

  public double getGrossSale(){
      return grossSale;
  }

  public void setCommissionRate(double cR){
      if (cR >= 0.0 && cR < 1.0){
          commissionRate = cR;
      }
  }

  public double getCommissionRate(){
      return commissionRate;
  }

  @Override
  public String toString(){
      return String.format("%s: %s\n%s: %,.2f; %s: %.2f ",
              "commission employee", super.toString(),
              "gross sales", getGrossSale(),
              "comission rate", getCommissionRate());
  }

  @Override
  public double earnings() {
      return getCommissionRate() * getGrossSale();
  }

}

```

### EmpDate.java


```java

/*
* The MIT License
*
* Copyright 2017 aungkhantmin.
*
* Permission is hereby granted, free of charge, to any person obtaining a copy
* of this software and associated documentation files (the "Software"), to deal
* in the Software without restriction, including without limitation the rights
* to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
* copies of the Software, and to permit persons to whom the Software is
* furnished to do so, subject to the following conditions:
*
* The above copyright notice and this permission notice shall be included in
* all copies or substantial portions of the Software.
*
* THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
* IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
* FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
* AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
* LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
* OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
* THE SOFTWARE.
*/
package problem10_8;

import static javafx.application.Platform.exit;

/**
*
* @author aungkhantmin
*/
public class EmpDate {

  private int year;
  private int month;
  private int day;
  private static final int[] DayPerMonth =
  {0,31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31};


  public EmpDate(int dy, int mh, int yr){
      year = yr;
      month = setMonth(mh);
      day = setDay(dy);
  }



  public int setMonth(int mh){
      if(mh > 0 && mh <= 12){
          return mh ;
      }
      else{
          throw new IllegalArgumentException(
                  "Month must be > 0 and <= 12");
      }
  }

  public int setDay(int dy){
      if (dy > 0 && dy < DayPerMonth[month]){
          return dy;
      }

      if ( month == 2 && dy == 29 && (year%400 == 0 ||
              (year % 4 == 0 && year % 100 != 0)) ){
          return dy;
      }

      throw new IllegalArgumentException(
      "day out-of-range for the specified month and year");        
  }


  public void setYear(int yr){
      year = yr;
  }

  public int getYear(){
      return year;
  }

  public int getMonth(){
      return month;
  }

  public int getDay(){
      return day;
  }

  public String getBathDate(){
      return String.format("%02d/%02d/%d",getDay(),getMonth(),getYear());
  }
}

```

### Employee.java

```java

/*
* The MIT License
*
* Copyright 2017 aungkhantmin.
*
* Permission is hereby granted, free of charge, to any person obtaining a copy
* of this software and associated documentation files (the "Software"), to deal
* in the Software without restriction, including without limitation the rights
* to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
* copies of the Software, and to permit persons to whom the Software is
* furnished to do so, subject to the following conditions:
*
* The above copyright notice and this permission notice shall be included in
* all copies or substantial portions of the Software.
*
* THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
* IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
* FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
* AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
* LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
* OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
* THE SOFTWARE.
*/
package problem10_8;

/**
*
* @author aungkhantmin
*/
public abstract class Employee{

  private String firstName;
  private String lastName;
  private String socialSecurityNumber;
  private EmpDate birthDate;

  public Employee(String fN, String lN, String sSN, EmpDate bD) {
      firstName = fN;
      lastName = lN;
      socialSecurityNumber = sSN;
      birthDate = bD;
  }

  public void setFirstName(String fN){
      firstName = fN;
  }

  public String getFirstName(){
      return firstName;
  }

  public void setLastName(String lN){
      lastName = lN;
  }

  public String getLastName(){
      return lastName;
  }

  public void setSSN(String sSN){
      socialSecurityNumber = sSN;
  }

  public String getSSN(){
      return socialSecurityNumber;
  }

  public void setBirthDate(EmpDate bD){
      birthDate = bD;
  }

  public EmpDate getBirthDate(){
      return birthDate;
  }

  @Override
  public String toString(){
      return String.format("%s %s\nsocial security number: %s\nbirth date: %s",
              getFirstName(),getLastName(),getSSN(),birthDate.getBathDate());
  }

  public abstract double earnings();
}

```

### HourlyEmployee.java

```java

/*
* The MIT License
*
* Copyright 2017 aungkhantmin.
*
* Permission is hereby granted, free of charge, to any person obtaining a copy
* of this software and associated documentation files (the "Software"), to deal
* in the Software without restriction, including without limitation the rights
* to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
* copies of the Software, and to permit persons to whom the Software is
* furnished to do so, subject to the following conditions:
*
* The above copyright notice and this permission notice shall be included in
* all copies or substantial portions of the Software.
*
* THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
* IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
* FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
* AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
* LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
* OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
* THE SOFTWARE.
*/
package problem10_8;

/**
*
* @author aungkhantmin
*/
public class HourlyEmployee extends Employee{

  private double wage;
  private double hours;

  public HourlyEmployee(String fN, String lN, String sSN, EmpDate bD,
          double wg, double hr) {
      super(fN, lN, sSN, bD);
      setWage(wg);
      setHours(hr);
  }




  public void setWage(double wg){
      if(wg >= 0.0){
          wage = wg;
      }
      else{
          throw new IllegalArgumentException("Hourly wage must be >=0.0");
      }
  }

  public double getWage(){
      return wage;
  }

  public void setHours(double hr){
      if (hr >= 0.0 && hr <= 744.0){
          hours = hr;
      }
      else{
          throw new IllegalArgumentException(
                  "Hour worked must be >= 0.0 and <= 168.0");
      }

  }

  public double getHours(){
      return hours;
  }

  @Override
  public String toString(){
      return String.format("hourly employee: %s\n%s: $%,.2f; %s: %,.2f",
          super.toString(), "hourly wage", getWage(), "hours worked",
          getHours());
  }

  @Override
  public double earnings(){
      if(getHours() <= 40){
          return getWage() * getHours();
      }
      else{
          return 40 * getWage() + ( getHours() - 40 ) * getWage() * 1.5;
      }
  }
}

```

### SalariedEmployee.java

```java

/*
* The MIT License
*
* Copyright 2017 aungkhantmin.
*
* Permission is hereby granted, free of charge, to any person obtaining a copy
* of this software and associated documentation files (the "Software"), to deal
* in the Software without restriction, including without limitation the rights
* to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
* copies of the Software, and to permit persons to whom the Software is
* furnished to do so, subject to the following conditions:
*
* The above copyright notice and this permission notice shall be included in
* all copies or substantial portions of the Software.
*
* THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
* IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
* FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
* AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
* LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
* OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
* THE SOFTWARE.
*/
package problem10_8;

/**
*
* @author aungkhantmin
*/
public class HourlyEmployee extends Employee{

  private double wage;
  private double hours;

  public HourlyEmployee(String fN, String lN, String sSN, EmpDate bD,
          double wg, double hr) {
      super(fN, lN, sSN, bD);
      setWage(wg);
      setHours(hr);
  }




  public void setWage(double wg){
      if(wg >= 0.0){
          wage = wg;
      }
      else{
          throw new IllegalArgumentException("Hourly wage must be >=0.0");
      }
  }

  public double getWage(){
      return wage;
  }

  public void setHours(double hr){
      if (hr >= 0.0 && hr <= 744.0){
          hours = hr;
      }
      else{
          throw new IllegalArgumentException(
                  "Hour worked must be >= 0.0 and <= 168.0");
      }

  }

  public double getHours(){
      return hours;
  }

  @Override
  public String toString(){
      return String.format("hourly employee: %s\n%s: $%,.2f; %s: %,.2f",
          super.toString(), "hourly wage", getWage(), "hours worked",
          getHours());
  }

  @Override
  public double earnings(){
      if(getHours() <= 40){
          return getWage() * getHours();
      }
      else{
          return 40 * getWage() + ( getHours() - 40 ) * getWage() * 1.5;
      }
  }
}

```

### Problem10_8.java

```java

/*
* The MIT License
*
* Copyright 2017 aungkhantmin.
*
* Permission is hereby granted, free of charge, to any person obtaining a copy
* of this software and associated documentation files (the "Software"), to deal
* in the Software without restriction, including without limitation the rights
* to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
* copies of the Software, and to permit persons to whom the Software is
* furnished to do so, subject to the following conditions:
*
* The above copyright notice and this permission notice shall be included in
* all copies or substantial portions of the Software.
*
* THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
* IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
* FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
* AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
* LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
* OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
* THE SOFTWARE.
*/
package problem10_8;
import java.util.Date;
/**
*
* @author aungkhantmin
*/
public class Problem10_8 {

  /**
   * @param args the command line arguments
   */
  public static void main(String[] args) {
      Date currentDate = new Date();
      @SuppressWarnings("deprecation")
      int currentMonth = currentDate.getMonth()+1;

      EmpDate bD1 = new EmpDate(24,5,1998);
      EmpDate bD2 = new EmpDate(5,8,1988);
      EmpDate bD3 = new EmpDate(4,5,1980);
      EmpDate bD4 = new EmpDate(29,2,2016);

      BasePlusCommissionEmployee bPCE = new BasePlusCommissionEmployee(
      "Jhon", "Nathen", "444-444-444", bD1, 100,0.5,300);

      CommissionEmployee cE = new CommissionEmployee(
      "Mary", "Lame", "333-333-333", bD2, 1000,0.5);

      HourlyEmployee hE = new HourlyEmployee(
      "Kame", "J. Nathen", "222-222-222", bD3,10,650);

      SalariedEmployee sE = new SalariedEmployee(
      "Kame", "J. Nathen", "111-111-111", bD4,100000.0);        

      Employee[] employee = new Employee [4];

      employee [0] = bPCE;
      employee [1] = cE;
      employee [2] = hE;
      employee [3] = sE;

      System.out.println( "Employees processed polymorphically:\n" );

      for( Employee currentEmp : employee){
          System.out.println(currentEmp);
          if(currentMonth == currentEmp.getBirthDate().getMonth()){
              double newEarning = currentEmp.earnings() + 100;
              System.out.printf("earned $%,.2f\n\n",currentEmp.earnings());
              System.out.print("You get Happy Birthday bonus $100");
              System.out.printf("\nNew earning: $%,.2f\n\n", newEarning);
          }
          else{
              System.out.printf("earned $%,.2f\n\n",currentEmp.earnings());
          }
      }




  }

}

```
