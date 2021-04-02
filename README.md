# Java Projects
#### This is some of java projects that i have been faced while learning java programming language.

(1) - AverageArray
-------------------------------------------------------------------------------------------------------------------------------
<h4>

```

package com.company;

import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int length;
        System.out.print("Enter the length of the array : ");
        length = scanner.nextInt();
        double[] numbers = new double[length];
        System.out.print("Enter the elements of the array\n");
        for (int i = 0; i < numbers.length; i++) {
            System.out.printf("Enter element number %d : ", i + 1);
            numbers[i] = scanner.nextDouble();
        }
        System.out.printf("Average of the array is %.2f\n", averageArray(numbers));
    }

    public static double averageArray(double[] numbers) {
        double average;
        double sum = 0;
        for (int i = 0; i < numbers.length; i++)
            sum += numbers[i];
        average = sum / numbers.length;
        return average;
    }
}

```

<h4>

(2) - Book
-------------------------------------------------------------------------------------------------------------------------------

<h4>

```

package com.company;

class Book {
    private String name;
    private final String ISBN;
    private String author;
    private String publisher;

    public Book(String name, String ISBN, String author, String publisher) {
        this.name = name;
        this.ISBN = ISBN;
        this.author = author;
        this.publisher = publisher;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getISBN() {
        return ISBN;
    }

    public String getauthor() {
        return author;
    }

    public void setauthor(String author) {
        this.author = author;
    }

    public String getPublisher() {
        return publisher;
    }

    public void setPublisher(String publisher) {
        this.publisher = publisher;
    }

    public String getBookInfo() {
        return "Name : " + name + "\n" + "ISBN : " + ISBN + "\n" + "Author : " + author + "\n" + "Publisher : " + publisher + "\n";
    }
}

public class Main {

    public static void main(String[] args) {
        Book book = new Book("Java: An Introduction to Problem Solving and Programming",
                "0134462033", "Walter Savitch", "Pearson");
        System.out.print(book.getBookInfo());
    }
}

```

<h4>

(3) - Car
-------------------------------------------------------------------------------------------------------------------------------

<h4>

```

package com.company;

class Car {
    private int speed;
    private double regularPrice;
    private String color;

    Car(int speed, double regularPrice, String color) {
        this.speed = speed;
        this.regularPrice = regularPrice;
        this.color = color;
    }

    public double getSalePrice() {
        return regularPrice;
    }
}

class Truck extends Car {
    private int weight;

    Truck(int speed, double regularPrice, String color, int weight) {
        super(speed, regularPrice, color);
        this.weight = weight;
    }

    public double getSalePrice() {
        if (weight > 2000)
            return super.getSalePrice() - (super.getSalePrice() * 0.1);
        else
            return super.getSalePrice() - (super.getSalePrice() * 0.2);
    }
}

class Ford extends Car {
    private int year;
    private int manufacturerDiscount;

    Ford(int speed, double regularPrice, String color, int year, int manufacturerDiscount) {
        super(speed, regularPrice, color);
        this.year = year;
        this.manufacturerDiscount = manufacturerDiscount;
    }

    @Override
    public double getSalePrice() {
        return super.getSalePrice() - manufacturerDiscount;
    }
}

class Sedan extends Car {
    private int length;

    Sedan(int speed, double regularPrice, String color, int length) {
        super(speed, regularPrice, color);
        this.length = length;
    }

    @Override
    public double getSalePrice() {
        if (length > 20)
            return super.getSalePrice() - (super.getSalePrice() * 0.05);
        else
            return super.getSalePrice() - (super.getSalePrice() * 0.1);
    }
}

public class Main {

    public static void main(String[] args) {
        Ford ford = new Ford(300, 250000, "blue", 2017, 5000);
        Sedan sedan = new Sedan(250, 200000, "Red", 10);
        System.out.printf("Price : %.2f\n", ford.getSalePrice());
        System.out.printf("Price : %.2f\n", sedan.getSalePrice());
    }
}

```

<h4>

(4) - CelsiusFahrenheit
-------------------------------------------------------------------------------------------------------------------------------

<h4>

```

package com.company;

import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        double cels;
        double fahr;
        System.out.print("Enter the temperature in celsius : ");
        cels = scanner.nextDouble();
        System.out.printf("Temperature in fahrenheit is %.2f", celsToFahr(cels));
    }

    public static double celsToFahr(double cels) {
        double fahr;
        fahr = (9.0 / 5) * cels + 32;
        return fahr;
    }
}

```

<h4>

(5) - Circle2D
-------------------------------------------------------------------------------------------------------------------------------

<h4>

```

package com.company;

class Circle2D {
    private double x;
    private double y;
    private double radius;

    Circle2D() {
        this.x = 0;
        this.y = 0;
        this.radius = 1;
    }

    Circle2D(double x, double y, double radius) {
        this.x = x;
        this.y = y;
        this.radius = radius;
    }

    public double getArea() {
        return radius * radius * Math.PI;
    }

    public double getPerimetr() {
        return 2 * radius * Math.PI;
    }

    public boolean contains(double x1, double y1) {
        double distance;
        distance = Math.sqrt(Math.pow(Math.abs(this.x - x1), 2) + Math.pow(Math.abs(this.y - y1), 2));
        if (this.radius >= distance)
            return true;
        return false;
    }

    public boolean contains(Circle2D circle) {
        double distance;
        distance = Math.sqrt(Math.pow(Math.abs(this.x - circle.x), 2) + Math.pow(Math.abs(this.y - circle.y), 2));
        if (this.radius >= circle.radius + distance)
            return true;
        return false;
    }

    public boolean overlap(Circle2D circle) {
        double distance;
        distance = Math.sqrt(Math.pow(Math.abs(this.x - circle.x), 2) + Math.pow(Math.abs(this.y - circle.y), 2));
        if (this.radius + circle.radius > distance)
            return true;
        return false;
    }
}

public class Main {

    public static void main(String[] args) {
        Circle2D circle = new Circle2D(2, 2, 5);
        System.out.printf("The area of the circle is %.2f\n", circle.getArea());
        System.out.printf("The perimeter of the circle is %.2f\n", circle.getPerimetr());
        if (circle.contains(new Circle2D(4, 5, 10.5)))
            System.out.printf("Contains\n");
        else
            System.out.printf("Not contains\n");
        if (circle.contains(new Circle2D(5, 2, 6.5)))
            System.out.printf("Overlap\n");
        else
            System.out.printf("Not overlap\n");
    }
}

```

<h4>

(6) - Date
-------------------------------------------------------------------------------------------------------------------------------

<h4>

```

package com.company;

enum Month {
    January, February, March,
    April, May, June, July, August,
    September, October, November, December;
}

class Date {
    private int year;
    private Month month;
    private int day;

    public Date(int year, Month month, int day) {
        this.year = year;
        this.month = month;
        this.day = day;
    }

    public int getYear() {
        return year;
    }

    public void setYear(int year) {
        this.year = year;
    }

    public Month getMonth() {
        return month;
    }

    public void setMonth(Month month) {
        this.month = month;
    }

    public int getDay() {
        return day;
    }

    public void setDay(int day) {
        this.day = day;
    }

    public void displayDate() {
        System.out.printf("%d/%s/%d\n", day, month, year);
    }
}

public class Main {

    public static void main(String[] args) {
        Date date = new Date(2017, Month.December, 31);
        date.displayDate();
    }
}

```

<h4>

(7) - Employee
-------------------------------------------------------------------------------------------------------------------------------

<h4>

```

package com.company;

class Employee {
    private String name;
    private String number;
    private String address;

    Employee(String name, String number, String address) {
        this.name = name;
        this.number = number;
        this.address = address;
    }

    public void print() {
        System.out.printf("Name : %s\nNumber : %s\nAddress : %s\n", name, number, address);
    }
}

class HourlyEmployee extends Employee {
    private double paymentRate;
    private int hourlyRate;

    HourlyEmployee(String name, String number, String address, double paymentRate, int hourlyRate) {
        super(name, number, address);
        this.paymentRate = paymentRate;
        this.hourlyRate = hourlyRate;
    }

    public double computeWage() {
        return paymentRate * hourlyRate;
    }

    public void print() {
        super.print();
        System.out.printf("Payment Rate : %.2f\nHourly Rate : %d\n\n", paymentRate, hourlyRate);
    }
}

class SalariedEmployee extends Employee {
    private double monthlySalary;

    SalariedEmployee(String name, String number, String address, double monthlySalary) {
        super(name, number, address);
        this.monthlySalary = monthlySalary;
    }

    public void print() {
        super.print();
        System.out.printf("Monthly Salary : %.2f\n\n", monthlySalary);
    }
}

public class Main {

    public static void main(String[] args) {
        Employee hourlyEmployee = new HourlyEmployee("Mohamed", "01248575470", "Cairo", 50.0, 5);
        Employee salariedEmployee = new SalariedEmployee("Mahmoud", "0101484352", "Suez", 2000.0);
        hourlyEmployee.print();
        salariedEmployee.print();
    }
}

```

<h4>

(8) - Fibonacci
-------------------------------------------------------------------------------------------------------------------------------

<h4>

```

package com.company;

import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int n;
        System.out.print("Enter the index to get it's fibonacci number : ");
        n = scanner.nextInt();
        System.out.printf("Fibonacci number of index %d is %d\n", n, fib(n));
    }

    public static int fib(int n) {
        if (n == 0)
            return 0;
        else if (n == 1)
            return 1;
        return fib(n - 2) + fib(n - 1);
    }
}

```

<h4>

(9) - GeometricObjects
-------------------------------------------------------------------------------------------------------------------------------

<h4>

```

package com.company;

abstract class GeometricObjects {
    public abstract void displayGeometricObject();

    public static void equalArea(double area1, double area2) {
        if (area1 == area2)
            System.out.printf("The two objects have the same area\n");
        else
            System.out.printf("The two objects doesn't have the same area\n");
    }
}

class Circle extends GeometricObjects {
    private double radius;

    Circle(double radius) {
        this.radius = radius;
    }

    public double area() {
        return radius * radius * Math.PI;
    }

    @Override
    public void displayGeometricObject() {
        System.out.print("Circle\n");
    }
}

class Rectangle extends GeometricObjects {
    private double width;
    private double length;

    Rectangle(double width, double length) {
        this.width = width;
        this.length = length;
    }

    public double area() {
        return width * length;
    }

    @Override
    public void displayGeometricObject() {
        System.out.print("Rectangle\n");
    }
}

public class Main {

    public static void main(String[] args) {
        Circle circle = new Circle(3);
        Rectangle rectangle = new Rectangle(3, 4);
        circle.displayGeometricObject();
        rectangle.displayGeometricObject();
        GeometricObjects.equalArea(circle.area(), rectangle.area());
    }
}

```

<h4>

(10) - Invoice
-------------------------------------------------------------------------------------------------------------------------------

<h4>

```

package com.company;

class Invoice {
    private String partNumber;
    private String description;
    private int quantity;
    private double price;

    Invoice(String partNumber, String description, int quantity, double price) {
        this.partNumber = partNumber;
        this.description = description;
        if (quantity < 0)
            this.quantity = 0;
        else
            this.quantity = quantity;
        if (price < 0)
            this.price = 0.0;
        else
            this.price = price;
    }

    public String getPartNumber() {
        return partNumber;
    }

    public void setPartNumber(String partNumber) {
        this.partNumber = partNumber;
    }

    public String getDescription() {
        return description;
    }

    public void setDescription(String description) {
        this.description = description;
    }

    public int getQuantity() {
        return quantity;
    }

    public void setQuantity(int quantity) {
        if (quantity < 0)
            this.quantity = 0;
        else
            this.quantity = quantity;
    }

    public double getPrice() {
        return price;
    }

    public void setPrice(double price) {
        if (price < 0)
            this.price = 0.0;
        else
            this.price = price;
    }

    public double getInvoiceAmount() {
        return quantity * price;
    }
}

public class Main {

    public static void main(String[] args) {
        Invoice ram = new Invoice("0x147", "Random Access Memory", 5, 150.24);
        System.out.println(ram.getPartNumber());
        System.out.println(ram.getDescription());
        System.out.println(ram.getPrice());
        System.out.println(ram.getQuantity());
        System.out.println(ram.getInvoiceAmount());
    }
}

```

<h4>

(11) - LoanAmount
-------------------------------------------------------------------------------------------------------------------------------

<h4>

```

package com.company;

import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        double annnualInterestRate = 5.00;
        double loanAmount;
        double interestRate;
        int numberOfYears;
        System.out.print("Enter the amount of loan : ");
        loanAmount = scanner.nextDouble();
        System.out.print("Enter number of years : ");
        numberOfYears = scanner.nextInt();
        System.out.printf("%-1s%20s%20s\n", "Interest Rate", "Monthly Payment", "Total Payment");
        for (; annnualInterestRate <= 8.00; annnualInterestRate += .125) {
            double monthlyInterestRate = annnualInterestRate / 1200;
            double monthlyPayment = loanAmount * monthlyInterestRate / (1 - 1 / Math.pow(1 + monthlyInterestRate, numberOfYears * 12));
            double totalPayment = monthlyPayment * numberOfYears * 12;
            String str = "%";
            System.out.printf("%-1.3f%s%17.2f%24.2f\n", annnualInterestRate, str, ((int) (monthlyPayment * 100) / 100.0), ((int) (totalPayment * 100) / 100.0));
        }
    }
}

```

<h4>

(12) - LongestPalindrome
-------------------------------------------------------------------------------------------------------------------------------

<h4>

```

package com.company;

import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String word;
        System.out.print("Enter the string : ");
        word = scanner.nextLine();
        System.out.printf("The longest palindrome in the string %s is %s\n", word, findLongestPalindrome(word));
    }

    public static String findLongestPalindrome(String word) {
        String substring = "";
        String longestPalindrome = "";
        for (int i = 0; i < word.length(); i++) {
            for (int j = i; j < word.length(); j++) {
                substring += word.charAt(j);
                if (isPalindrome(substring) && longestPalindrome.length() < substring.length())
                    longestPalindrome = substring;
            }
            substring = "";
        }
        return longestPalindrome;
    }

    public static boolean isPalindrome(String word) {
        String inversedWord = "";
        for (int i = word.length() - 1; i >= 0; i--)
            inversedWord += word.charAt(i);
        if (word.equals(inversedWord))
            return true;
        return false;
    }
}

```

<h4>

(13) - Matrix
-------------------------------------------------------------------------------------------------------------------------------

<h4>

```

package com.company;

class Matrix {
    private final int length = 2;
    private double[][] matrix = new double[length][length];
    ;

    Matrix(double[][] matrix) {
        for (int i = 0; i < length; i++)
            for (int j = 0; j < length; j++)
                this.matrix[i][j] = matrix[i][j];
    }

    public double det() {
        return matrix[0][0] * matrix[1][1] - matrix[0][1] * matrix[1][0];
    }

    public int isSingular() {
        return (det() == 0) ? 1 : 0;
    }

    public Matrix inverse() {
        Matrix inverse = new Matrix(new double[][]{{0, 0}, {0, 0}});
        for (int i = 0; i < matrix.length; i++) {
            for (int j = 0; j < matrix[i].length; j++) {
                if (i == j)
                    inverse.matrix[i][j] = (1 / det()) * matrix[(i + 1) % 2][(j + 1) % 2];
                else
                    inverse.matrix[i][j] = (1 / det()) * matrix[i][j] * -1;
            }
        }
        return inverse;
    }

    public void print() {
        for (int i = 0; i < matrix.length; i++) {
            for (int j = 0; j < matrix[i].length; j++)
                System.out.printf("%.2f  ", matrix[i][j]);
            System.out.print("\n");
        }
    }
}

public class Main {

    public static void main(String[] args) {
        double[][] numbers = {{1, 5}, {8, 4}};
        Matrix matrix = new Matrix(numbers);
        Matrix inverse = matrix.inverse();
        matrix.print();
        System.out.print("\n");
        inverse.print();
    }
}

```

<h4>

(14) - MultipleChoiceTest
-------------------------------------------------------------------------------------------------------------------------------

<h4>

```

package com.company;

import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        char[][] answers = new char[2][10];
        char[] keys = {'A', 'B', 'D', 'A', 'C', 'B', 'D', 'A', 'B', 'D'};
        int correctAnswers = 0;
        System.out.print("Enter the answers of the students\n");
        for (int i = 0; i < answers.length; i++) {
            System.out.printf("Enter the answers of the student number %d\n", i + 1);
            for (int j = 0; j < answers[i].length; j++) {
                System.out.printf("Enter answer for question number %d : ", j + 1);
                answers[i][j] = scanner.next().charAt(0);
            }
            System.out.println();
        }
        for (int i = 0; i < answers.length; i++) {
            for (int j = 0; j < answers[i].length; j++) {
                if (answers[i][j] == keys[j])
                    correctAnswers++;
            }
            System.out.printf("Student number %d answered %d question correctly\n", i + 1, correctAnswers);
            correctAnswers = 0;
        }
    }
}

```

<h4>

(15) - MyPoint
-------------------------------------------------------------------------------------------------------------------------------

<h4>

```

package com.company;

class MyPoint {
    private double x;
    private double y;

    MyPoint() {
        this.x = 0;
        this.y = 0;
    }

    MyPoint(double x, double y) {
        this.x = x;
        this.y = y;
    }

    public double getX() {
        return x;
    }

    public double getY() {
        return y;
    }

    public double distance(MyPoint point) {
        double distance;
        distance = Math.sqrt(Math.pow(Math.abs(this.x - point.x), 2) + Math.pow(Math.abs(this.y - point.y), 2));
        return distance;
    }

    public double distance(double x, double y) {
        double distance;
        distance = Math.sqrt(Math.pow(Math.abs(this.x - x), 2) + Math.pow(Math.abs(this.y - y), 2));
        return distance;
    }
}

public class Main {

    public static void main(String[] args) {
        MyPoint point1 = new MyPoint();
        MyPoint point2 = new MyPoint(10, 30.5);
        System.out.printf("The distance between (%.2f,%.2f),(%.2f,%.2f) is %.2f\n"
                , point1.getX(), point1.getY(), point2.getX(), point2.getY(), point1.distance(point2));
    }
}

```

<h4>

(16) - Number
-------------------------------------------------------------------------------------------------------------------------------

<h4>

```

package com.company;

class Number {
    private double number;

    Number(double number) {
        this.number = number;
    }

    public boolean isZero() {
        return (number == 0) ? true : false;
    }

    public boolean isPositive() {
        return (number > 0) ? true : false;
    }

    public boolean isNegative() {
        return (number < 0) ? true : false;
    }

    public boolean isOdd() {
        return (number % 2 != 0) ? true : false;
    }

    public boolean isEven() {
        return (number % 2 == 0) ? true : false;
    }

    public boolean isPrime() {
        for (int i = 2; i < number; i++)
            if (number % i == 0)
                return false;
        return true;
    }

    public boolean isArmstrong() {
        double digit;
        double reminder;
        double armstrongNumber = 0;
        digit = number;
        while (digit != 0) {
            reminder = digit % 10;
            armstrongNumber += Math.pow(reminder, 3);
            digit /= 10;
        }
        if (armstrongNumber == number)
            return true;
        return false;
    }

    public double getFactorial() {
        double factorial = 1;
        for (int i = 1; i <= number; i++)
            factorial *= i;
        return factorial;
    }

    public double getSqrt() {
        return Math.sqrt(number);
    }

    public double getSqr() {
        return Math.pow(number, 2);
    }

    public double sumDigits() {
        double sumDigits = 0;
        double digit;
        double reminder;
        digit = number;
        while (digit != 0) {
            reminder = digit % 10;
            sumDigits += reminder;
            digit /= 10;
        }
        return sumDigits;
    }

    public double getReverse() {
        String reverseNumber = "";
        String digits;
        digits = Double.toString(number);
        for (int i = digits.length() - 1; i >= 0; i--)
            reverseNumber += digits.charAt(i);
        return Double.parseDouble(reverseNumber);
    }

    public void listFactor() {
        double digit = number;
        int i = 2;
        System.out.printf("Factors of number %.2f is : ", number);
        while (digit != 0 && digit >= i) {
            if (digit % i == 0) {
                System.out.print(i + "  ");
                digit /= i;
            } else
                i++;
        }
        System.out.println();
    }

    public void dispBinary() {
        int decimal = (int) number;
        System.out.printf("Binary number of number %.2f is : ", number);
        while (decimal != 0) {
            System.out.print((decimal % 2) + "  ");
            decimal /= 2;
        }
        System.out.println();
    }
}

public class Main {

    public static void main(String[] args) {
        Number number = new Number(5);
        number.listFactor();
        number.dispBinary();
    }
}

```

<h4>

(17) - NumberBetween
-------------------------------------------------------------------------------------------------------------------------------

<h4>

```

package com.company;

import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        double number;
        System.out.print("Enter the number : ");
        number = scanner.nextDouble();
        if (number >= 1 && number <= 1000)
            System.out.printf("The number %.0f between 1 and 1000 is true\n", number);
        else
            System.out.printf("The number %.0f between 1 and 1000 is not true\n", number);
    }
}

```

<h4>

(18) - Person
-------------------------------------------------------------------------------------------------------------------------------

<h4>

```

package com.company;

class Person {
    protected String name;
    protected String address;
    protected String number;
    protected String email;

    Person(String name, String address, String number, String email) {
        this.name = name;
        this.address = address;
        this.number = number;
        this.email = email;
    }

    public void print() {
        System.out.printf("Name : %s\nAddress : %s\nNumber : %s\nEmail : %s\n", name, address, number, email);
    }

    @Override
    public String toString() {
        return "Person{" +
                "name='" + name + '\'' +
                '}';
    }
}

class Student extends Person {

    Student(String name, String address, String number, String email) {
        super(name, address, number, email);
    }

    private class Level {
        @Override
        public String toString() {
            return "Level{}";
        }
    }

    public void print() {
        super.print();
    }

    public String toString() {
        return "Student{" +
                "name='" + name + '\'' +
                '}';
    }
}

class Employee extends Person {

    public Employee(String name, String address, String number, String email) {
        super(name, address, number, email);
    }

    private class Office {
        @Override
        public String toString() {
            return "Office{}";
        }
    }

    private class Salary {
        @Override
        public String toString() {
            return "Salary{}";
        }
    }

    private class DateHired {
        @Override
        public String toString() {
            return "DateHired{}";
        }
    }

    public void print() {
        super.print();
    }

    @Override
    public String toString() {
        return "Employee{" +
                "name='" + name + '\'' +
                '}';
    }
}

class Faculty extends Employee {
    private int officeHours;
    private String rank;

    public Faculty(String name, String address, String number, String email, int officeHours, String rank) {
        super(name, address, number, email);
        this.officeHours = officeHours;
        this.rank = rank;
    }

    public void print() {
        super.print();
        System.out.printf("Office hours : %s\rank : %s\n", officeHours, rank);
    }

    @Override
    public String toString() {
        return "Faculty{" +
                "name='" + name + '\'' +
                '}';
    }
}

class Staff extends Employee {
    private String title;

    public Staff(String name, String address, String number, String email, String title) {
        super(name, address, number, email);
        this.title = title;
    }

    public void print() {
        super.print();
        System.out.printf("title : %s\n", title);
    }

    @Override
    public String toString() {
        return "Staff{" +
                "name='" + name + '\'' +
                '}';
    }
}

class MyDate {
    private int year;
    private int month;
    private int day;

    MyDate(int year, int month, int day) {
        this.year = year;
        this.month = month;
        this.day = day;
    }

    public void print() {
        System.out.printf("Year : %d\nMonth : %d\nDay : %d\n", year, month, day);
    }

    @Override
    public String toString() {
        return "MyDate{}";
    }
}

public class Main {

    public static void main(String[] args) {
        Person[] persons = new Person[5];

        Person person = new Person("Jack", "Cairo", "0110145148", "Jack@yahoo.com");
        Person student = new Student("Mark", "Liverpool", "0110514748", "Mark@gmail.com");
        Person employee = new Employee("Jimmy", "London", "0124157456", "Jimmy@outlook.com");
        Person faculty = new Faculty("Cambridge", "Orlando", "012646548", "Cambridge@yahoo.com", 35, "Professor");
        Person staff = new Staff("Tim", "Orlando", "013415525", "Tim@yahoo.com", "English");
        persons[0] = person;
        persons[1] = student;
        persons[2] = employee;
        persons[3] = staff;
        persons[4] = person;
        System.out.println(person.toString());
        System.out.println();
        System.out.println(student.toString());
        System.out.println();
        System.out.println(employee.toString());
        System.out.println();
        System.out.println(faculty.toString());
        System.out.println();
        System.out.println(staff.toString());
    }
}

```

<h4>

(19) - PISeries
-------------------------------------------------------------------------------------------------------------------------------

<h4>

```

package com.company;

import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        double userPI;
        double n = 1;
        double seriesPI = 1 / n;
        String PI = "";
        String estimatedPI = "";
        int term = 1;
        boolean equal = false;
        System.out.print("Enter PI : ");
        userPI = scanner.nextDouble();
        while (!equal) {
            term++;
            if (term % 2 != 0) {
                n += 2;
                seriesPI += 1 / n;
            } else {
                n += 2;
                seriesPI -= 1 / n;
            }
            estimatedPI = Double.toString(seriesPI * 4);
            PI = Double.toString(userPI);
            for (int i = 0; i < PI.length(); i++) {
                if (PI.charAt(i) == estimatedPI.charAt(i))
                    equal = true;
                else {
                    equal = false;
                    break;
                }
            }
        }
        System.out.printf("You need %d terms before using PI=%s\n", term, PI);
    }
}

```

<h4>

(20) - Point
-------------------------------------------------------------------------------------------------------------------------------

<h4>

```

package com.company;

class Point {
    private double x;
    private double y;
    private double z;

    Point(double x, double y, double z) {
        this.x = x;
        this.y = y;
        this.z = z;
    }

    public void negate() {
        x *= -1;
        y *= -1;
        z *= -1;
    }

    public double norm() {
        double distance;
        distance = Math.sqrt(Math.pow(Math.abs(this.x - 0), 2) + Math.pow(Math.abs(this.y - 0), 2) + Math.pow(Math.abs(this.z - 0), 2));
        return distance;
    }

    public void print() {
        System.out.printf("The point is (%.2f,%.2f,%.2f)\n", x, y, z);
    }
}

public class Main {

    public static void main(String[] args) {
        Point point = new Point(10, 25, 30.5);
        point.print();
        point.negate();
        point.print();
        System.out.printf("The distance from the origin is %.2f\n", point.norm());
    }
}

```

<h4>

(21) - PoundKilogram
-------------------------------------------------------------------------------------------------------------------------------

<h4>

```

package com.company;

import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        double numberInPounds;
        double numberInKilogram;
        System.out.print("Enter the number in pounds : ");
        numberInPounds = scanner.nextDouble();
        numberInKilogram = numberInPounds * .454;
        System.out.printf("%.2f pound is %.3f kilogram\n", numberInPounds, numberInKilogram);
    }
}

```

<h4>

(22) - Publishing
-------------------------------------------------------------------------------------------------------------------------------

<h4>

```

package com.company;

class Publishing {
    private String title;
    private double price;

    Publishing(String title, double price) {
        this.title = title;
        this.price = price;
    }

    public void print() {
        System.out.printf("Title : %s\nPrice : %.2f\n", title, price);
    }
}

class Book extends Publishing {
    private int pagecount;

    Book(String title, double price, int pagecount) {
        super(title, price);
        this.pagecount = pagecount;
    }

    public void print() {
        super.print();
        System.out.printf("Page Count : %d\n\n", pagecount);
    }
}

class Tape extends Publishing {
    private int playtime;

    Tape(String title, double price, int playtime) {
        super(title, price);
        this.playtime = playtime;
    }

    public void print() {
        super.print();
        System.out.printf("Play Time : %d\n\n", playtime);
    }
}

public class Main {

    public static void main(String[] args) {
        Publishing[] publishing = new Publishing[2];
        Publishing book = new Book("The Journy", 50.0, 200);
        Publishing tape = new Tape("Geostorm", 30, 120);
        publishing[0] = book;
        publishing[1] = tape;
        publishing[0].print();
        publishing[1].print();
    }
}

```

<h4>

(23) - Rational
-------------------------------------------------------------------------------------------------------------------------------

<h4>

```

package com.company;

import java.util.Scanner;

class Rational {
    int a;
    int b;

    Rational(int a, int b) {
        this.a = a;
        this.b = b;
    }

    public int gcd() {
        int gcd = 0;
        for (int i = 1; i <= a && i <= b; i++) {
            if (a % i == 0 && b % i == 0)
                gcd = i;
        }
        return gcd;
    }

    public void reduce() {
        int gcd = gcd();
        a /= gcd;
        b /= gcd;
    }

    public Rational add(Rational rational) {
        Rational add = new Rational(1, 1);
        add.a = (rational.b * a) + (rational.a * b);
        add.b = rational.b * b;
        return add;
    }

    public Rational subtract(Rational rational) {
        Rational subtract = new Rational(1, 1);
        subtract.a = (rational.b * a) - (rational.a * b);
        subtract.b = rational.b * b;
        return subtract;
    }

    public Rational multiply(Rational rational) {
        Rational multiply = new Rational(1, 1);
        multiply.a = rational.a * a;
        multiply.b = rational.b * b;
        return multiply;
    }

    public Rational divide(Rational rational) {
        Rational divide = new Rational(1, 1);
        divide.a = rational.b * a;
        divide.b = rational.a * b;
        return divide;
    }
}

public class Main {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int n;
        Rational seriesSum = new Rational(1, 1);
        System.out.print("Enter n : ");
        n = scanner.nextInt();
        for (int i = 1; i <= n; i++)
            seriesSum = seriesSum.add(new Rational(1, i));
        System.out.printf("The summation of the series is %d/%d\n", seriesSum.a, seriesSum.b);
    }
}

```

<h4>

(24) - SavingAccount
-------------------------------------------------------------------------------------------------------------------------------

<h4>

```

package com.company;

class SavingAccount {
    private static double annualInterestRate;
    private double savingsBalance;

    public SavingAccount(double savingsBalance) {
        this.savingsBalance = savingsBalance;
    }

    public double getSavingsBalance() {
        return savingsBalance;
    }

    public void setSavingsBalance(double savingsBalance) {
        this.savingsBalance = savingsBalance;
    }

    public double calculateMonthlyInterest() {
        double interestRate;
        interestRate = savingsBalance * annualInterestRate / 12;
        savingsBalance += interestRate;
        return interestRate;
    }

    public static void modifyInterestRate(double newAnnualInterestRate) {
        annualInterestRate = newAnnualInterestRate;
    }
}

public class Main {

    public static void main(String[] args) {
        SavingAccount saver1 = new SavingAccount(2000.0);
        SavingAccount saver2 = new SavingAccount(3000.0);
        SavingAccount.modifyInterestRate(0.04);
        saver1.calculateMonthlyInterest();
        System.out.printf("Balance : %.2f\n", saver1.getSavingsBalance());
        saver2.calculateMonthlyInterest();
        System.out.printf("Balance : %.2f\n", saver2.getSavingsBalance());
        SavingAccount.modifyInterestRate(0.05);
        saver1.calculateMonthlyInterest();
        System.out.printf("Balance : %.2f\n", saver1.getSavingsBalance());
        saver2.calculateMonthlyInterest();
        System.out.printf("Balance : %.2f\n", saver2.getSavingsBalance());
    }
}

```

<h4>

(25) - Shape
-------------------------------------------------------------------------------------------------------------------------------

<h4>

```

package com.company;

abstract class Shape {
    abstract public void print();

    abstract public double area();
}

abstract class TwoDimensional extends Shape {
    abstract public double perimeter();
}

abstract class ThreeDimensional extends Shape {
    abstract public double volume();
}

class Rectangle extends TwoDimensional {
    private double width;
    private double length;

    Rectangle(double width, double length) {
        this.width = width;
        this.length = length;
    }

    @Override
    public void print() {
        System.out.printf("Rectangle\nPerimeter is : %.2f\nArea is : %.2f\n\n", perimeter(), area());
    }

    @Override
    public double area() {
        return width * length;
    }

    @Override
    public double perimeter() {
        return (width + length) * 2;
    }
}

class Circle extends TwoDimensional {
    private double radius;

    Circle(double radius) {
        this.radius = radius;
    }

    @Override
    public void print() {
        System.out.printf("Circle\nPerimeter is : %.2f\nArea is : %.2f\n\n", perimeter(), area());
    }

    @Override
    public double area() {
        return radius * radius * Math.PI;
    }

    @Override
    public double perimeter() {
        return 2 * radius * Math.PI;
    }
}

class Cube extends ThreeDimensional {
    private double length;

    Cube(double length) {
        this.length = length;
    }

    @Override
    public void print() {
        System.out.printf("Cube\nVolume is : %.2f\nArea is : %.2f\n\n", volume(), area());
    }

    @Override
    public double area() {
        return 6 * length * length;
    }

    @Override
    public double volume() {
        return length * length * length;
    }
}

class Sphere extends ThreeDimensional {
    private double radius;

    Sphere(double radius) {
        this.radius = radius;
    }

    @Override
    public void print() {
        System.out.printf("Sphere\nVolume is : %.2f\nArea is : %.2f\n\n", volume(), area());
    }

    @Override
    public double area() {
        return 4 * radius * radius * Math.PI;
    }

    @Override
    public double volume() {
        return (4.0 / 3) * radius * radius * radius * Math.PI;
    }
}

public class Main {

    public static void main(String[] args) {
        Rectangle rectangle = new Rectangle(3, 4);
        Circle circle = new Circle(3);
        Cube cube = new Cube(2);
        Sphere sphere = new Sphere(5);
        rectangle.print();
        circle.print();
        cube.print();
        sphere.print();
    }
}

```

<h4>

(26) - SmallestFactors
-------------------------------------------------------------------------------------------------------------------------------

<h4>

```

package com.company;

import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int number;
        int n = 2;
        String output = "";
        System.out.print("Enter the number : ");
        number = scanner.nextInt();
        while (number / n != 0) {
            if (number % n == 0) {
                output = output + n + ",";
                number /= n;
            } else
                n++;
        }
        output = output.substring(0, output.length() - 1);
        System.out.println(output);
    }
}

```

<h4>

(27) - SmallestIntegerN
-------------------------------------------------------------------------------------------------------------------------------

<h4>

```

package com.company;

public class Main {

    public static void main(String[] args) {
        int n = 1;
        while (n * n < 12000) {
            if (n * n > 12000)
                break;
            else
                n++;
        }
        System.out.printf("%d is the smallest integer n that square of n is greater than 12000\n", n);
    }
}

```

<h4>

(28) - SortThreeIntegers
-------------------------------------------------------------------------------------------------------------------------------

<h4>

```

package com.company;

import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int num1, num2, num3;
        int temp;
        System.out.print("Enter integer number 1 : ");
        num1 = scanner.nextInt();
        System.out.print("Enter integer number 2 : ");
        num2 = scanner.nextInt();
        System.out.print("Enter integer number 3 : ");
        num3 = scanner.nextInt();
        if (num1 > num2) {
            temp = num1;
            num1 = num2;
            num2 = temp;
        }
        if (num1 > num3) {
            temp = num1;
            num1 = num3;
            num3 = temp;
        }
        if (num2 > num3) {
            temp = num2;
            num2 = num3;
            num3 = temp;
        }
        System.out.printf("Numbers after sort\n%d  %d  %d\n", num1, num2, num3);
    }
}

```

<h4>

(29) - Stack
-------------------------------------------------------------------------------------------------------------------------------

<h4>

```

package com.company;

import java.util.Scanner;

class Stack {
    final int maxSize;
    int[] stackArray;
    int top;

    Stack(int maxSize) {
        this.maxSize = maxSize;
        stackArray = new int[maxSize];
        top = -1;
    }

    public int count() {
        return top + 1;
    }

    public void push(int element) {
        stackArray[++top] = element;
    }

    public int pop() {
        return stackArray[top--];
    }

    public boolean isEmpty() {
        return (top == -1) ? true : false;
    }

    public boolean isFull() {
        return (top == maxSize - 1) ? true : false;
    }

    public void print() {
        for (int element : stackArray) {
            System.out.printf("%d ", element);
        }
        System.out.println();
    }
}

public class Main {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String expression;
        char operator;
        int digit;
        System.out.print("Enter the expression in postfix notation : ");
        expression = scanner.nextLine();
        Stack stack = new Stack(expression.length());
        try {
            for (int i = 0; i < expression.length(); i++) {
                operator = expression.charAt(i);
                if (Character.isDigit(operator)) {
                    digit = Character.getNumericValue(operator);
                    stack.push(digit);
                } else {
                    int value2 = stack.pop();
                    if (!stack.isEmpty()) {
                        int value1 = stack.pop();
                        int result = 0;
                        switch (operator) {
                            case '+':
                                result = value2 + value1;
                                break;
                            case '-':
                                result = value2 - value1;
                                break;
                            case '*':
                                result = value2 * value1;
                                break;
                            case '/':
                                result = value2 / value1;
                                break;
                            default:
                                System.out.print("Invalid operator!\n");
                        }
                        stack.push(result);
                    } else
                        throw new ArrayIndexOutOfBoundsException();
                }
            }
            stack.pop();
        } catch (Exception e) {
            System.out.print("Stack is empty!\n");
        } finally {
            stack.print();
        }
    }
}

```

<h4>

(30) - SumDigits
-------------------------------------------------------------------------------------------------------------------------------

<h4>

```

package com.company;

import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        long n;
        System.out.print("Enter the number to get sum of digits : ");
        n = scanner.nextLong();
        System.out.printf("Sum of digits of number %d is %d\n", n, sumDigits(n));
    }

    public static int sumDigits(long n) {
        int sum = 0;
        while (n != 0) {
            long reminder = n % 10;
            sum += (int) reminder;
            n /= 10;
        }
        return sum;
    }
}

```

<h4>

(31) - SumMatrix
-------------------------------------------------------------------------------------------------------------------------------

<h4>

```

package com.company;

import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int length;
        System.out.print("Enter the length of the matrix : ");
        length = scanner.nextInt();
        int[][] matrix = new int[length][length];
        System.out.print("Enter the elements of the matrix\n");
        for (int i = 0; i < matrix.length; i++) {
            for (int j = 0; j < matrix[i].length; j++) {
                System.out.printf("Enter element [%d][%d] : ", i, j);
                matrix[i][j] = scanner.nextInt();
            }
        }
        System.out.printf("Sum of the matrix is %d\n", sumMatrix(matrix));
    }

    public static int sumMatrix(int[][] matrix) {
        int sum = 0;
        for (int i = 0; i < matrix.length; i++)
            for (int j = 0; j < matrix[i].length; j++)
                sum += matrix[i][j];
        return sum;
    }
}

```

<h4>

(32) - ThreeDPoint
-------------------------------------------------------------------------------------------------------------------------------

<h4>

```

package com.company;

class MyPoint {
    private double x;
    private double y;

    MyPoint() {
        this.x = 0;
        this.y = 0;
    }

    MyPoint(double x, double y) {
        this.x = x;
        this.y = y;
    }

    void settX(double x) {
        this.x = x;
    }

    void setY(double y) {
        this.y = y;
    }

    double getX() {
        return x;
    }

    double getY() {
        return y;
    }

    public double distance(MyPoint point) {
        double distance;
        distance = Math.sqrt(Math.pow(Math.abs(this.x - point.x), 2) + Math.pow(Math.abs(this.y - point.y), 2));
        return distance;
    }

    public double distance(double x, double y) {
        double distance;
        distance = Math.sqrt(Math.pow(Math.abs(this.x - x), 2) + Math.pow(Math.abs(this.y - y), 2));
        return distance;
    }
}

class ThreeDPoint extends MyPoint {
    private double z;

    ThreeDPoint() {
        super();
        this.z = 0;
    }

    ThreeDPoint(double x, double y, double z) {
        super(x, y);
        this.z = z;
    }

    public double getZ() {
        return z;
    }

    public double distance(ThreeDPoint point) {
        double distance;
        distance = Math.sqrt(Math.pow(Math.abs(super.getX() - point.getX()), 2) + Math.pow(Math.abs(super.getY() - point.getY()), 2) + Math.pow(Math.abs(this.z - point.getZ()), 2));
        return distance;
    }

    public double distance(double x, double y, double z) {
        double distance;
        distance = Math.sqrt(Math.pow(Math.abs(super.getX() - x), 2) + Math.pow(Math.abs(super.getY() - y), 2) + Math.pow(Math.abs(this.z - z), 2));
        return distance;
    }
}

public class Main {

    public static void main(String[] args) {
        ThreeDPoint point1 = new ThreeDPoint();
        ThreeDPoint point2 = new ThreeDPoint(10, 30, 25.5);
        System.out.printf("The distance between (%.2f,%.2f,%.2f),(%.2f,%.2f,%.2f) is %.2f\n"
                , point1.getX(), point1.getY(), point1.getZ(), point2.getX(), point2.getY(), point2.getZ(), point1.distance(point2));
    }
}

```

<h4>

(33) - Time
-------------------------------------------------------------------------------------------------------------------------------

<h4>

```

package com.company;

class Time {
    int hours;
    int minutes;
    int seconds;

    Time(int hours, int minutes, int seconds) {
        this.hours = hours;
        this.minutes = minutes;
        this.seconds = seconds;
    }

    public void normalize() {
        while (hours < 0 || hours > 24) {
            if (hours < 0)
                hours *= -1;
            else
                hours -= 24;
        }
        while (minutes < 0 || minutes > 60) {
            if (minutes < 0)
                minutes *= -1;
            else
                minutes -= 60;
        }
        while (seconds < 0 || seconds > 60) {
            if (seconds < 0)
                seconds *= -1;
            else
                seconds -= 60;
        }
    }

    public void advance(int h, int m, int s) {
        hours += h;
        minutes += m;
        seconds += s;
    }

    public void reset(int h, int m, int s) {
        hours = h;
        minutes = m;
        seconds = s;
    }

    public void print() {
        System.out.printf("%d:%d:%d\n", hours, minutes, seconds);
    }
}

public class Main {

    public static void main(String[] args) {
        Time time = new Time(4, 25, 3);
        time.print();
        time.advance(25, 60, 59);
        time.print();
        time.normalize();
        time.print();
        time.reset(2, 5, 20);
        time.print();
    }
}

```

<h4>

(34) - TriangleSquare
-------------------------------------------------------------------------------------------------------------------------------

<h4>

```

package com.company;

import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int row, rows, n, a, i, space;
        System.out.print("Enter number of the rows : ");
        rows = scanner.nextInt();
        for (row = 0; row < rows; row++) {
            n = 0;
            for (space = 4 * (rows - row); space >= 0; space--)
                System.out.print(" ");
            for (i = 0; i <= row; i++) {
                a = power(2, n);
                System.out.printf("%4d", a);
                n++;
            }
            n--;
            n--;
            for (i = 0; i < row; i++) {
                a = power(2, n);
                System.out.printf("%4d", a);
                n--;
            }
            System.out.println();
        }
    }

    public static int power(int n, int m) {
        int power = 1;
        for (int i = 1; i <= m; i++) {
            power *= n;
        }
        return power;
    }
}

```

<h4>

(35) - TriangularSolitaire
-------------------------------------------------------------------------------------------------------------------------------

<h4>

```

package com.company;

import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int rows;
        int j = 1;
        System.out.print("Enter number of rows : ");
        rows = scanner.nextInt();
        for (int row = 1; row <= rows; row++) {
            for (int space = 2 * (rows - row); space > 0; space--)
                System.out.print(" ");
            for (int i = 1; i <= row; i++) {
                System.out.printf("%4d", j);
                j++;
            }
            System.out.println();
        }
    }
}

```

<h4>

(36) - UnspecifiedNumber
-------------------------------------------------------------------------------------------------------------------------------

<h4>

```

package com.company;

import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int unspecifiedNumber;
        int positiveCounter = 0;
        int negativeCounter = 0;
        System.out.print("Enter the number : ");
        unspecifiedNumber = scanner.nextInt();
        while (unspecifiedNumber != 0) {
            if (unspecifiedNumber > 0)
                positiveCounter++;
            else
                negativeCounter++;
            System.out.print("Enter the number : ");
            unspecifiedNumber = scanner.nextInt();
        }
        System.out.printf("You entered %d positive integer and %d negative integer\n", positiveCounter, negativeCounter);
    }
}

```

<h4>

(37) - UppercaseToLowercase
-------------------------------------------------------------------------------------------------------------------------------

<h4>

```

package com.company;

import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        char upperCase;
        char lowerCase;
        System.out.print("Enter the character in uppercase : ");
        upperCase = scanner.next().charAt(0);
        lowerCase = toLowerCase(upperCase);
        System.out.printf("%c\n", lowerCase);
    }

    public static char toLowerCase(char userUpperCase) {
        char lowerCase[] = new char[]{'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k'
                , 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w', 'x', 'y', 'z'};
        char upperCase[] = new char[]{'A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K'
                , 'L', 'M', 'N', 'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z'};
        for (int i = 0; i < upperCase.length; i++) {
            if (upperCase[i] == userUpperCase)
                return lowerCase[i];
        }
        return 0;
    }
}

```

<h4>

(38) - VolumeCylinder
-------------------------------------------------------------------------------------------------------------------------------

<h4>

```

package com.company;

import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        double length;
        double radius;
        double area;
        double volume;
        System.out.print("Enter the length of the cylinder : ");
        length = scanner.nextDouble();
        System.out.print("Enter the radius of the cylinder : ");
        radius = scanner.nextDouble();
        area = radius * radius * Math.PI;
        volume = area * length;
        System.out.printf("The volume of the cylinder is %.2f\n", volume);
    }
}

```

<h4>

(39) - WeeklyHours
-------------------------------------------------------------------------------------------------------------------------------

<h4>

```

package com.company;

import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int length;
        System.out.print("Enter the number of employees : ");
        length = scanner.nextInt();
        int[][] employeeHours = new int[length][7];
        int[] weeklyHours = new int[length];
        for (int i = 0; i < employeeHours.length; i++) {
            System.out.printf("Enter the number of hours of the week for employee number %d\n", i + 1);
            for (int j = 0; j < employeeHours[i].length; j++) {
                System.out.printf("Enter the number of hours of day %d : ", j + 1);
                employeeHours[i][j] = scanner.nextInt();
            }
            System.out.println();
        }
        for (int i = 0; i < employeeHours.length; i++) {
            for (int j = 0; j < employeeHours[i].length; j++) {
                weeklyHours[i] += employeeHours[i][j];
            }
            System.out.printf("Weekly hours for employee number %d is %d\n", i + 1, weeklyHours[i]);
        }
    }
}

```

<h4>

(40) - PersonInformation
-------------------------------------------------------------------------------------------------------------------------------

<h4>

```

package com.company;

class Person {
    private String name;
    private String address;

    Person(String name, String address) {
        this.name = name;
        this.address = address;
    }

    public void print() {
        System.out.printf("Name : %s\nAdress : %s\n", name, address);
    }
}

class Student extends Person {
    private double gpa;

    public Student(String name, String address, double gpa) {
        super(name, address);
        this.gpa = gpa;
    }

    public void print() {
        super.print();
        System.out.printf("GPA : %.2f\n", gpa);
    }
}

class Professor extends Person {
    private int publs;

    public Professor(String name, String address, int publs) {
        super(name, address);
        this.publs = publs;
    }

    public void print() {
        super.print();
        System.out.printf("Publs : %d\n", publs);
    }
}

public class Main {

    public static void main(String[] args) {
        Person person[] = new Person[2];

        person[0] = new Student("Paulo", "Cairo", 2.6);
        person[1] = new Professor("Mark", "Manchester", 5);

        person[0].print();
        System.out.println();
        person[1].print();
    }
}

```

<h4>
