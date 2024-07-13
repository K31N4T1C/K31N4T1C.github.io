---
title: "Mortgage Calculator"
description: Simple mortgage calculator in Java, exploring fundamental programming concepts and practical financial calculations.
date: 2024-07-14 00:00:00 +0800
categories: [Java]
tags: [java basics, programming]     # TAG names should always be lowercase
---
This mortgage calculator project is based on the Java Tutorial for Beginners by Programming with Mosh. It's a practical way to learn Java programming, helping you understand how to handle user input, perform calculations, and format output in a useful application.

## Sample Output
```
Principal: 100000
Annual Interest Rate: 3.92
Period (Years): 30
Mortgage: $472.81
```


## Formula
![Formula|300](https://www.wikihow.com/images/thumb/8/88/Calculate-Mortgage-Payments-Step-6-Version-3.jpg/v4-460px-Calculate-Mortgage-Payments-Step-6-Version-3.jpg.webp)

Source: [WikiHow](https://www.wikihow.com/Calculate-Mortgage-Payments)


### Constants and Scanner Initialization
```java
Scanner scanner = new Scanner(System.in);
final int YEAR = 12;
final int PERCENT = 100;
```

- **Scanner Initialization:** This line initializes a `Scanner` object named `scanner` to read input from the console (`System.in`).
- **Constants (YEAR and PERCENT):** These are declared as `final int`, making them constants in Java.
	 - `YEAR` is set to 12, representing the number of months in a year.
	 - `PERCENT` is set to 100, used for converting percentage values to decimal form.


### User Input and Calculation Initialization
```java
System.out.print("Principal: ");
int principal = scanner.nextInt();

System.out.print("Annual Interest Rate: ");
double annualInterest = scanner.nextDouble();
double monthlyInterest = annualInterest / PERCENT / YEAR;

System.out.print("Period (Years): ");
int period = scanner.nextInt();
int numPayment = period * YEAR;
```

- **User Input:**
	- `principal`: Reads and stores the principal amount borrowed from the user.
	- `annualInterest`: Reads and stores the annual interest rate provided by the user.
	- `monthlyInterest`: Calculates the monthly interest rate by dividing the annual interest rate by 12 (number of months in a year) and by 100 to convert it from percentage to decimal.
	- `period`: Reads and stores the number of years over which the loan will be repaid.
	- `numPayment`: Calculates the total number of monthly payments by multiplying `period` (years) by `YEAR` (months in a year).

### Mortgage Calculation
```java
double mortgage = principal
            * (monthlyInterest * Math.pow(1 + monthlyInterest, numPayment))
            / (Math.pow(1 + monthlyInterest, numPayment) - 1);
```

Calculates the monthly mortgage payment using the formula:

$`M = P \times \frac{r \times (1 + r)^n}{(1 + r)^n - 1}`$

where:
- $M$ is `mortgage`, the monthly payment.
- $P$ is ``principal``, the loan amount.
- $r$ is ``monthlyInterest``, the monthly interest rate.
- $n$ is ``numPayment``, the total number of monthly payments.

> `Math.pow()` is a Java method used to raise a number to a specified power, returning the result as a double.

### Output Formatting and Display
```java
String mortgageFormat = NumberFormat.getCurrencyInstance(Locale.US).format(mortgage);
System.out.print("Mortgage: " + mortgageFormat);
```

Uses `NumberFormat.getCurrencyInstance(Locale.US)` to format the `mortgage` amount into a currency format suitable for the US locale.

## Complete Code
```java
import java.text.NumberFormat;
import java.util.Locale;
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        final int YEAR = 12;
        final int PERCENT = 100;

        System.out.print("Principal: ");
        int principal = scanner.nextInt();

        System.out.print("Annual Interest Rate: ");
        double annualInterest = scanner.nextDouble();
        double monthlyInterest = annualInterest / PERCENT / YEAR;
        
        System.out.print("Period (Years): ");
        int period = scanner.nextInt();
        int numPayment = period * YEAR;

        double mortgage = principal 
                        * (monthlyInterest * Math.pow(1 + monthlyInterest, numPayment))
                        / (Math.pow(1 + monthlyInterest, numPayment) - 1);
        
        String mortgageFormat = NumberFormat.getCurrencyInstance(Locale.US).format(mortgage);
        System.out.print("Mortgage: " + mortgageFormat);

        scanner.close();
    }
}
```
