<h1> Intro to Arrays </h1>

<h2> What are Arrays? </h2>

An array is a fixed-size container that holds multiple values of the same type. Arrays allow you to store and access collections of related data using a single variable.

<h2> Declaring and Creating Arrays </h2>

Array syntax:
```java
// Declare array variable
int[] numbers;

// Create array with size 5
numbers = new int[5];

// Declare and create in one line
double[] speeds = new double[4];

// Initialize with values
String[] names = {"Alice", "Bob", "Charlie"};
int[] motorIDs = {1, 2, 3, 4};
```

<h2> Accessing Array Elements </h2>

Use index notation (zero-based indexing):
```java
int[] values = {10, 20, 30, 40, 50};

int first = values[0];   // 10
int third = values[2];   // 30
values[1] = 25;          // Change second element

// Array length
int size = values.length;  // 5
```

<h2> Important Array Concepts </h2>

Key points about arrays:
- **Fixed size**: Cannot change size after creation
- **Zero-indexed**: First element is at index 0
- **Type-safe**: Can only hold declared type
- **Length property**: `array.length` gives size
- **Bounds checking**: Accessing invalid index throws `ArrayIndexOutOfBoundsException`

<h2> Multi-dimensional Arrays </h2>

Arrays can have multiple dimensions:
```java
// 2D array (matrix)
int[][] grid = new int[3][4];  // 3 rows, 4 columns
grid[0][0] = 1;

// Initialize 2D array
int[][] matrix = {
    {1, 2, 3},
    {4, 5, 6}
};
```
