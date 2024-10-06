## Java

1.       Classes and Objects

2.       Method Overloading

3.       Method Overriding

4.       Single Inheritance

5.       Packages

6.       Arithmetic Operations

7.       Interfaces

8. Vowels Checking using Switch
```java
import java.io.*;  
  
public class VowelORNot {  
    public static void main(String[] args) throws IOException {  
        System.out.print("Enter an alphabet: ");  
        char c = (char) System.in.read();  
        switch (c) {  
            case 'a', 'A', 'e', 'E', 'i', 'I', 'o', 'O', 'u', 'U':  
                System.out.println("Vowel");  
                break;  
            default:  
                System.out.println("Not a vowel");  
        }  
    }  
}
```

```
Enter an alphabet: E
Vowel

Enter an alphabet: d
Not a vowel
```

9. Odd or Even till N
```java
public class OddOrEvenTillHundred {  
    public static void main(String[] args) {  
        int i = 0;  
        while (i++ < 100) {  
            System.out.println("i = " + i + ((i % 2 == 0) ? " Even" : " Odd"));  
        }  
    }  
}
```

```
i = 1 Odd
i = 2 Even
i = 3 Odd
i = 4 Even
...
i = 98 Even
i = 99 Odd
i = 100 Even
```

10.   Exception Handling
```java
import java.util.Random;  
  
public class HandleException {  
    public static void main(String[] args) {  
        Random random = new Random();  
        int c = 0;  
        for (int i = 0; i < 7; i++) {  
            try {  
                int a = random.nextInt();  
                int b = random.nextInt();  
                c = 12345 / (a/b);  
            } catch (ArithmeticException e) {  
                System.out.print("reset c = ");  
                c = 0;  
            } finally {  
                System.out.println(c);  
            }  
        }  
    }  
}
```

```
reset c = 0
-4115
reset c = 0
reset c = 0
12345
12345
reset c = 0
```

11.   Applet face emoji
```java
package face;

import java.awt.Graphics;
import java.applet.Applet;

public class Face extends Applet {
	public void paint(Graphics g) {
		g.drawOval(100, 100, 200, 200);
		g.drawArc(150, 200, 100, 50, 0, -180);
		g.fillOval(160, 150, 20, 20);
		g.fillOval(230, 150, 20, 20);
	}
}
```

```html
<applet code="face.Face.class" width="400" height="400"></applet>
```

![](attachments/Pasted%20image%2020241006203408.png)

12.   Applet flag
```java
package flag;

import java.awt.*;
import java.applet.Applet;

public class Flag extends Applet {
	public void paint(Graphics g) {
		int width=600, height=400;
		setSize(600, 400);

		g.setColor(new Color(255, 153, 51));
		g.fillRect(0, 0, width, height / 3);

		g.setColor(Color.WHITE);
		g.fillRect(0, height / 3, width, height / 3);

		g.setColor(new Color(19, 136, 8));
		g.fillRect(0, 2 * height / 3, width, height / 3);

		g.setColor(new Color(0, 0, 128));
		int centerX = width / 2;
		int centerY = height / 2;
		int radius = width / 10;
		g.drawOval(centerX - radius, centerY - radius, 2 * radius, 2 * radius);

		for (int i = 0; i < 24; i++) {
			double angle = i * 15 * Math.PI / 180;
			int x1 = (int) (centerX + radius * Math.cos(angle));
			int y1 = (int) (centerY + radius * Math.sin(angle));
			g.drawLine(x1, y1, centerX, centerY);
		}
	}
}
```

```html
<applet code="flag.Flag" width="600" height="400"></applet>
```

![](attachments/Pasted%20image%2020241006223646.png)

## Shell Scripting

1. Arithmetic operations:
```bash
#!/bin/bash
echo "Enter two numbers:"
read a b
echo "Sum: $((a + b))"
echo "Difference: $((a - b))"
echo "Product: $((a * b))"
echo "Quotient: $((a / b))"
```

```bash
➜  model-lab git:(main) ✗ sh arithmetic.sh
Enter two numbers:
6 3
Sum: 9
Difference: 3
Product: 18
Quotient: 2
```
2. Swapping of two variables:
```bash
#!/bin/bash
a=5
b=10
echo "Before swap: a=$a, b=$b"
temp=$a
a=$b
b=$temp
echo "After swap: a=$a, b=$b"
```

```bash
➜  model-lab git:(main) ✗ sh swapping_of_two.sh
Before swap: a=5, b=10
After swap: a=10, b=5
```
3. Check equality of two numbers:
```bash
#!/bin/bash
read -p "Enter two numbers: " a b
if [ $a -eq $b ]; then
    echo "Numbers are equal"
else
    echo "Numbers are not equal"
fi
```

```bash
➜  model-lab git:(main) ✗ bash equality_of_two.sh
Enter two numbers: 3 2
Numbers are not equal
➜  model-lab git:(main) ✗ bash equality_of_two.sh
Enter two numbers: 6 6
Numbers are equal
```
4. Greatest of three numbers:
```bash
#!/bin/bash
read -p "Enter three numbers: " a b c
if [ $a -gt $b ] && [ $a -gt $c ]; then
    echo "$a is the greatest"
elif [ $b -gt $a ] && [ $b -gt $c ]; then
    echo "$b is the greatest"
else
    echo "$c is the greatest"
fi
```

```bash
➜  model-lab git:(main) ✗ sh greatest_of_three.sh
Enter three numbers: 3 536 32
536 is the greatest
```
5. Display a string n times using for loop:
```bash
#!/bin/bash
read -p "Enter a string: " str
read -p "Enter number of times to repeat: " n
for ((i=1; i<=n; i++)); do
    echo "$str"
done
```

```bash
➜  model-lab git:(main) ✗ bash for_loop.sh
Enter a string: kavin
Enter number of times to repeat: 4
kavin
kavin
kavin
kavin
```

6. Counter using while loop:
```bash
#!/bin/bash
counter=1
while [ $counter -le 5 ]; do
    echo $counter
    ((counter++))
done
```

```bash
➜  model-lab git:(main) ✗ bash counter_while.sh
1
2
3
4
5
```
7. Print numbers using until loop:
```bash
#!/bin/bash
i=1
until [ $i -gt 5 ]; do
    echo $i
    ((i++))
done
```

```bash
➜  model-lab git:(main) ✗ bash until.sh
1
2
3
4
5
```
8. Terminate the loop using break statement:
```bash
#!/bin/bash
for i in {1..10}; do
    if [ $i -eq 5 ]; then
        break
    fi
    echo $i
done
```

```bash
➜  model-lab git:(main) ✗ bash break.sh
1
2
3
4
```
9. Factorial of a given number:
```bash
#!/bin/bash
read -p "Enter a number: " n
fact=1
for ((i=1; i<=n; i++)); do
    fact=$((fact * i))
done
echo "Factorial of $n is $fact"
```

```bash
➜  model-lab git:(main) ✗ bash factorial.sh
Enter a number: 5
Factorial of 5 is 120
```
10. Odd or even until N:
```bash
#!/bin/bash
read -p "Enter N: " N
for ((i=1; i<=N; i++)); do
    if [ $((i % 2)) -eq 0 ]; then
        echo "$i is even"
    else
        echo "$i is odd"
    fi
done
```

```bash
➜  model-lab git:(main) ✗ bash odd_or_even_till_n.sh
Enter N: 10
1 is odd
2 is even
3 is odd
4 is even
5 is odd
6 is even
7 is odd
8 is even
9 is odd
10 is even
```
11. Multiplication table:
```bash
#!/bin/bash
read -p "Enter a number: " n
for i in {1..10}; do
    echo "$n x $i = $((n * i))"
done
```

```bash
➜  model-lab git:(main) ✗ bash multiplication_table.sh
Enter a number: 5
5 x 1 = 5
5 x 2 = 10
5 x 3 = 15
5 x 4 = 20
5 x 5 = 25
5 x 6 = 30
5 x 7 = 35
5 x 8 = 40
5 x 9 = 45
5 x 10 = 50
```
12. Triangle pattern using nested loops:
```bash
#!/bin/bash
read -p "Enter number of rows: " rows
for ((i=1; i<=rows; i++)); do
    for ((j=1; j<=i; j++)); do
        echo -n "* "
    done
    echo
done
```

```bash
➜  model-lab git:(main) ✗ bash triangle_pattern.sh
Enter number of rows: 5
*
* *
* * *
* * * *
* * * * *
```
13. Sum of digits:
```bash
#!/bin/bash
read -p "Enter a number: " num
sum=0
while [ $num -gt 0 ]; do
    sum=$((sum + num % 10))
    num=$((num / 10))
done
echo "Sum of digits: $sum"
```

```bash
➜  model-lab git:(main) ✗ sh sum_of_digits.sh
Enter a number: 12345
Sum of digits: 15
```
14. Sum of N numbers:
```bash
#!/bin/bash
read -p "Enter N: " N
sum=0
for ((i=1; i<=N; i++)); do
    sum=$((sum + i))
done
echo "Sum of numbers from 1 to $N is $sum"
```

```bash
➜  model-lab git:(main) ✗ bash sum_of_real_numbers.sh
Enter N: 10
Sum of numbers from 1 to 10 is 55
```
15. Length of the string:
```bash
#!/bin/bash
read -p "Enter a string: " str
echo "Length of the string is ${#str}"
```

```bash
➜  model-lab git:(main) ✗ sh string_length.sh
Enter a string: kavin
Length of the string is 5
```
16. String comparison:
```bash
#!/bin/bash
read -p "Enter first string: " str1
read -p "Enter second string: " str2
if [ "$str1" = "$str2" ]; then
    echo "Strings are equal"
else
    echo "Strings are not equal"
fi
```

```bash
➜  model-lab git:(main) ✗ sh string_compare.sh
Enter first string: kavin
Enter second string: Kavin
Strings are not equal
➜  model-lab git:(main) ✗ sh string_compare.sh
Enter first string: kavin
Enter second string: kavin
Strings are equal
```
17. Creating and calling functions:
```bash
#!/bin/bash
greet() {
    echo "Hello, $1!"
}

read -p "Enter your name: " name
greet "$name"
```

```bash
➜  model-lab git:(main) ✗ sh function.sh
Enter your name: kavin
Hello, kavin!
```
18. Nested functions:
```bash
#!/bin/bash
outer_function() {
    echo "This is the outer function"
    inner_function() {
        echo "This is the inner function"
    }
    inner_function
}

outer_function
```

```bash
➜  model-lab git:(main) ✗ bash nested_functions.sh
This is the outer function
This is the inner function
```