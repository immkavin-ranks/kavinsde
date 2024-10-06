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

11.   Applet face emoji

12.   Applet flag
