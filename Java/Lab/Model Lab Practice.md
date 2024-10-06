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
