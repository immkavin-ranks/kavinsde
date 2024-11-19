1. Temperature Conversion (Fahrenheit to Celsius):
```python
def fahrenheit_to_celsius():
    fahrenheit = float(input("Enter temperature in Fahrenheit: "))
    celsius = (fahrenheit - 32) * 5/9
    print(f"{fahrenheit}°F is equal to {celsius:.2f}°C")

fahrenheit_to_celsius()
```

2. Arithmetic Operations:
```python
def arithmetic_operations():
    num1 = float(input("Enter first number: "))
    num2 = float(input("Enter second number: "))
    
    print(f"Addition: {num1 + num2}")
    print(f"Subtraction: {num1 - num2}")
    print(f"Multiplication: {num1 * num2}")
    print(f"Division: {num1 / num2}")
    print(f"Floor Division: {num1 // num2}")
    print(f"Modulus: {num1 % num2}")
    print(f"Exponentiation: {num1 ** num2}")

arithmetic_operations()
```

3. Student Grade Calculator:
```python
def calculate_grades():
    subjects = ['Math', 'Science', 'English', 'History', 'Computer']
    total_marks = 0
    
    for subject in subjects:
        marks = float(input(f"Enter marks for {subject} (out of 100): "))
        total_marks += marks
    
    percentage = total_marks / len(subjects)
    
    if percentage >= 90:
        grade = 'A+'
    elif percentage >= 80:
        grade = 'A'
    elif percentage >= 70:
        grade = 'B'
    elif percentage >= 60:
        grade = 'C'
    else:
        grade = 'F'
    
    print(f"\nTotal Marks: {total_marks}")
    print(f"Average: {percentage:.2f}%")
    print(f"Grade: {grade}")

calculate_grades()
```

4. Find Smallest of Three Numbers:
```python
def find_smallest():
    num1 = float(input("Enter first number: "))
    num2 = float(input("Enter second number: "))
    num3 = float(input("Enter third number: "))
    
    smallest = min(num1, num2, num3)
    print(f"The smallest number is: {smallest}")

find_smallest()
```

5. Area of Square and Circle:
```python
import math

def calculate_areas():
    # Square
    side = float(input("Enter the side length of square: "))
    square_area = side ** 2
    print(f"Area of square: {square_area}")
    
    # Circle
    radius = float(input("Enter the radius of circle: "))
    circle_area = math.pi * radius ** 2
    print(f"Area of circle: {circle_area:.2f}")

calculate_areas()
```

6. Triangle Pattern:
```python
def print_triangle():
    rows = int(input("Enter number of rows: "))
    for i in range(rows):
        print('*' * (i + 1))

print_triangle()
```

7. Copy File Contents:
```python
def copy_file():
    source = input("Enter source file name: ")
    destination = input("Enter destination file name: ")
    
    try:
        with open(source, 'r') as src, open(destination, 'w') as dst:
            dst.write(src.read())
        print("File copied successfully!")
    except FileNotFoundError:
        print("Source file not found!")

copy_file()
```

8. Swap Two Numbers:
```python
def swap_numbers():
    a = float(input("Enter first number: "))
    b = float(input("Enter second number: "))
    
    print(f"Before swap: a = {a}, b = {b}")
    a, b = b, a
    print(f"After swap: a = {a}, b = {b}")

swap_numbers()
```

9. GUI Temperature Converter:
```python
import tkinter as tk

def convert_temp():
    try:
        f = float(fahrenheit_entry.get())
        c = (f - 32) * 5/9
        celsius_label.config(text=f"{c:.2f}°C")
    except ValueError:
        celsius_label.config(text="Invalid input!")

window = tk.Tk()
window.title("Temperature Converter")

tk.Label(window, text="Fahrenheit:").pack()
fahrenheit_entry = tk.Entry(window)
fahrenheit_entry.pack()

tk.Button(window, text="Convert", command=convert_temp).pack()
celsius_label = tk.Label(window, text="")
celsius_label.pack()

window.mainloop()
```

10. Slice Lists:
```python
def slice_list():
    my_list = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
    print(f"Original list: {my_list}")
    print(f"First three elements: {my_list[:3]}")
    print(f"Last three elements: {my_list[-3:]}")
    print(f"Elements from index 2 to 5: {my_list[2:6]}")
    print(f"Every second element: {my_list[::2]}")

slice_list()
```

11. Count List Items in a Tuple:
```python
def count_items_in_tuple():
    my_tuple = (1, 2, 3, 4, 5, 1, 2, 1)
    item_to_count = int(input("Enter the item to count in the tuple: "))
    count = my_tuple.count(item_to_count)
    print(f"Item {item_to_count} appears {count} times in the tuple.")

count_items_in_tuple()
```

12. Convert Kilometers to Miles:
```python
def km_to_miles():
    kilometers = float(input("Enter kilometers: "))
    miles = kilometers * 0.621371
    print(f"{kilometers} km is equal to {miles:.2f} miles")

km_to_miles()
```

13. Copy Lines from a File:
```python
def copy_lines():
    source_file = input("Enter source file name: ")
    destination_file = input("Enter destination file name: ")
    
    try:
        with open(source_file, 'r') as src, open(destination_file, 'w') as dst:
            dst.write(src.read())
        print("File copied successfully!")
    except FileNotFoundError:
        print("Source file not found!")

copy_lines()
```

14. Find Largest of Three Numbers:
```python
def find_largest():
    num1 = float(input("Enter first number: "))
    num2 = float(input("Enter second number: "))
    num3 = float(input("Enter third number: "))
    
    largest = max(num1, num2, num3)
    print(f"The largest number is: {largest}")

find_largest()
```

15. Reverse a String Word by Word:
```python
def reverse_string():
    sentence = input("Enter a sentence: ")
    reversed_sentence = ' '.join(sentence.split()[::-1])
    print(f"Reversed sentence: {reversed_sentence}")

reverse_string()
```

16. Fibonacci Series:
```python
def fibonacci_series():
    n = int(input("Enter the number of terms: "))
    a, b = 0, 1
    for _ in range(n):
        print(a, end=' ')
        a, b = b, a + b

fibonacci_series()
```

17. Area of Triangle and Rectangle:
```python
def calculate_area():
    # Triangle
    base = float(input("Enter base of triangle: "))
    height = float(input("Enter height of triangle: "))
    triangle_area = 0.5 * base * height
    print(f"Area of triangle: {triangle_area}")

    # Rectangle
    length = float(input("Enter length of rectangle: "))
    width = float(input("Enter width of rectangle: "))
    rectangle_area = length * width
    print(f"Area of rectangle: {rectangle_area}")

calculate_area()
```

18. Generate a Random Number:
```python
import random

def generate_random_number():
    random_number = random.randint(1, 100)
    print(f"Random number: {random_number}")

generate_random_number()
```

19. Display Labels in a Window:
```python
import tkinter as tk

def display_labels():
    window = tk.Tk()
    window.title("Labels Display")

    labels = ["Label 1", "Label 2", "Label 3"]
    for text in labels:
        tk.Label(window, text=text).pack()

    window.mainloop()

display_labels()
```

20. Check Prime Number:
```python
def is_prime():
    num = int(input("Enter a number: "))
    if num > 1:
        for i in range(2, int(num ** 0.5) + 1):
            if num % i == 0:
                print(f"{num} is not a prime number")
                break
        else:
            print(f"{num} is a prime number")
    else:
        print(f"{num} is not a prime number")

is_prime()
```

21. String Operations:
```python
def string_operations():
    string = input("Enter a string: ")
    substring = string[1:5]
    concatenated_string = string + " - Concatenated"
    
    print(f"Original String: {string}")
    print(f"Substring (2nd to 5th character): {substring}")
    print(f"Concatenated String: {concatenated_string}")

string_operations()
```

22. Multiplication Table:
```python
def multiplication_table():
    num = int(input("Enter a number: "))
    for i in range(1, 11):
        print(f"{num} x {i} = {num * i}")

multiplication_table()
```

23. Copy Odd Lines to a New File:
```python
def copy_odd_lines():
    source_file = input("Enter source file name: ")
    destination_file = input("Enter destination file name: ")
    
    try:
        with open(source_file, 'r') as src, open(destination_file, 'w') as dst:
            lines = src.readlines()
            for i in range(0, len(lines), 2):
                dst.write(lines[i])
        print("Odd lines copied successfully!")
    except FileNotFoundError:
        print("Source file not found!")

copy_odd_lines()
```

24. Check Leap Year:
```python
def check_leap_year():
    year = int(input("Enter a year: "))
    if (year % 4 == 0 and year % 100 != 0) or (year % 400 == 0):
        print(f"{year} is a leap year")
    else:
        print(f"{year} is not a leap year")

check_leap_year()
```

25. Temperature Conversion (Celsius to Fahrenheit):
```python
def celsius_to_fahrenheit():
    celsius = float(input("Enter temperature in Celsius: "))
    fahrenheit = (celsius * 9/5) + 32
    print(f"{celsius}°C is equal to {fahrenheit:.2f}°F")

celsius_to_fahrenheit()
```

26. Check if Number is Odd or Even:
```python
def check_odd_even():
    num = int(input("Enter a number: "))
    if num % 2 == 0:
        print(f"{num} is even")
    else:
        print(f"{num} is odd")

check_odd_even()
```

27. List Methods:
```python
def list_methods():
    my_list = [1, 2, 3, 4, 5]
    print(f"Original list: {my_list}")
    
    my_list.insert(2, 10)
    print(f"After insert: {my_list}")
    
    my_list.remove(10)
    print(f"After remove: {my_list}")
    
    my_list.append(6)
    print(f"After append: {my_list}")
    
    my_list.pop()
    print(f"After pop: {my_list}")
    
    my_list.clear()
    print(f"After clear: {my_list}")

list_methods()
```

28. Check Positive or Negative:
```python
def check_positive_negative():
    num = float(input("Enter a number: "))
    if num > 0:
        print(f"{num} is positive")
    elif num < 0:
        print(f"{num} is negative")
    else:
        print(f"{num} is zero")

check_positive_negative()
```

29. Tuple Methods:
```python
def tuple_methods():
    my_tuple = (1, 2, 3, 4, 5)
    print(f"Original tuple: {my_tuple}")
    
    # Access items
    print(f"First item: {my_tuple[0]}")
    
    # Length
    print(f"Length of tuple: {len(my_tuple)}")
    
    # Check for item
    item = 3
    print(f"Is {item} in tuple? {'Yes' if item in my_tuple else 'No'}")
    
    # Add item (convert to list first)
    my_list = list(my_tuple)
    my_list.append(6)
    my_tuple = tuple(my_list)
    print(f"Tuple after adding item: {my_tuple}")

tuple_methods()
```

30. Precedence of Operators:
```python
def operator_precedence():
    v = 5
    w = 10
    x = 15
    y = 20
    z = (v + w) * x / y
    print(f"Result of expression (v+w) * x / y: {z}")

operator_precedence()
```