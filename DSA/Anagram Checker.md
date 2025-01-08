Problem in hackerrank: https://www.hackerrank.com/challenges/java-anagrams/problem

```java
import java.io.*;
import java.util.*;

public class Solution {

    public static void main(String[] args) {
        /* Enter your code here. Read input from STDIN. Print output to STDOUT. Your class should be named Solution. */
        Scanner scanner = new Scanner(System.in);
        
        String a = scanner.nextLine();
        String b = scanner.nextLine();
        
        scanner.close();
        boolean ret = isAnagram(a, b);
        System.out.println( (ret) ? "Anagrams" : "Not Anagrams" );
    }
    
    private static boolean isAnagram(String a , String b) {
        HashMap<Character, Integer> countOfA = new HashMap<>();
        HashMap<Character, Integer> countOfB = new HashMap<>();
        
        for (char c : a.toLowerCase().toCharArray()) {
            if (countOfA.containsKey(c)) {
                countOfA.put(c, countOfA.get(c) + 1);
            } else {
                countOfA.put(c, 1);
            }
        }   
        for (char c : b.toLowerCase().toCharArray()) {
            if (countOfB.containsKey(c)) {
                countOfB.put(c, countOfB.get(c) + 1);
            } else {
                countOfB.put(c, 1);
            }
        }   
        
        return countOfA.equals(countOfB);
    }
}

```

```java

    static boolean isAnagram(String a, String b) {
        // Complete the function
        char [] A = a.toLowerCase().toCharArray();
        char [] B = b.toLowerCase().toCharArray();
        java.util.Arrays.sort(A);
        java.util.Arrays.sort(B);
        return java.util.Arrays.equals(A, B);
    }


```