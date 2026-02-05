<h1> Iterating through Arrays </h1>

<h2> Why Iterate Through Arrays? </h2>

Iterating (looping) through arrays allows you to:
- Process each element
- Find specific values
- Calculate totals or averages
- Modify all elements
- Search for conditions

<h2> For Loop with Index </h2>

Traditional indexed loop:
```java
int[] motorSpeeds = {0.5, 0.7, 0.3, 0.9};

for (int i = 0; i < motorSpeeds.length; i++) {
    System.out.println("Motor " + i + ": " + motorSpeeds[i]);
    motorSpeeds[i] *= 2;  // Modify element
}
```

<h2> Enhanced For Loop (For-Each) </h2>

Simplified syntax when you don't need the index:
```java
int[] scores = {95, 87, 92, 88, 90};
int total = 0;

for (int score : scores) {
    total += score;
}

double average = total / (double) scores.length;
```

**Note**: For-each loops are read-only - you cannot modify array elements through the loop variable.

<h2> While Loop </h2>

Alternative iteration approach:
```java
int[] values = {1, 2, 3, 4, 5};
int index = 0;

while (index < values.length) {
    System.out.println(values[index]);
    index++;
}
```

<h2> Common Patterns </h2>

Find maximum value:
```java
int[] numbers = {23, 67, 12, 89, 45};
int max = numbers[0];

for (int num : numbers) {
    if (num > max) {
        max = num;
    }
}
```

Count elements meeting condition:
```java
double[] temperatures = {72.5, 85.3, 68.9, 91.2};
int hotDays = 0;

for (double temp : temperatures) {
    if (temp > 80) {
        hotDays++;
    }
}
```
