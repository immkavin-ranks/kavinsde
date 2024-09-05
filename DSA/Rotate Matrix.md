Rotate Matrix

Given an image represented by an `NxN` matrix write a method to rotate the image by 90 degrees.

You have to rotate the image **in-place**, which means you have to modify the input 2D matrix directly.

**DO NOT** allocate another 2D matrix and do the rotation.

![](https://img-c.udemycdn.com/redactor/raw/coding_exercise_instructions/2023-11-27_03-37-40-a8dee11b74cf290ea42a7526e4d340c5.png)

```java
for (int i = 0; i < arr.length; i++) {
	
}
```

	a00 a01 a02
	a10 a11 a12
	a20 a21 a22

	a20 a10 a00
	a21 a11 a01
	a22 a12 a02


```java
public void rotate(int[][] matrix) {
    int n = matrix.length;
    
    // Step 1: Transpose the matrix
    for (int i = 0; i < n; i++) {
        for (int j = i; j < n; j++) {
            int temp = matrix[i][j];
            matrix[i][j] = matrix[j][i];
            matrix[j][i] = temp;
        }
    }
    
    // Step 2: Reverse each row
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n / 2; j++) {
            int temp = matrix[i][j];
            matrix[i][j] = matrix[i][n - 1 - j];
            matrix[i][n - 1 - j] = temp;
        }
    }
}
```