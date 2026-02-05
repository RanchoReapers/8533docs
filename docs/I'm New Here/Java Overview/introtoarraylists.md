<h1> Intro to ArrayLists </h1>

<h2> What are ArrayLists? </h2>

ArrayList is a resizable array implementation in Java. Unlike regular arrays, ArrayLists can grow and shrink dynamically, making them more flexible for many use cases.

<h2> Creating ArrayLists </h2>

ArrayList syntax:
```java
import java.util.ArrayList;

// Create empty ArrayList of Integers
ArrayList<Integer> numbers = new ArrayList<>();

// Create ArrayList of Strings
ArrayList<String> names = new ArrayList<>();

// Create with initial values
ArrayList<Double> speeds = new ArrayList<>();
speeds.add(0.5);
speeds.add(0.7);
speeds.add(0.9);
```

**Note**: ArrayLists use wrapper classes for primitives:
- `Integer` instead of `int`
- `Double` instead of `double`
- `Boolean` instead of `boolean`

<h2> Common ArrayList Operations </h2>

**Adding elements**:
```java
ArrayList<String> teams = new ArrayList<>();
teams.add("Rancho Reapers");        // Add to end
teams.add(0, "First Team");         // Add at index
```

**Accessing elements**:
```java
String first = teams.get(0);        // Get element at index
int size = teams.size();            // Get number of elements
```

**Removing elements**:
```java
teams.remove(0);                    // Remove by index
teams.remove("Rancho Reapers");     // Remove by value
teams.clear();                      // Remove all elements
```

**Checking contents**:
```java
boolean hasTeam = teams.contains("Rancho Reapers");
boolean isEmpty = teams.isEmpty();
```

<h2> Iterating Through ArrayLists </h2>

```java
ArrayList<Integer> motorIDs = new ArrayList<>();
motorIDs.add(1);
motorIDs.add(2);
motorIDs.add(3);

// For-each loop
for (int id : motorIDs) {
    System.out.println("Motor ID: " + id);
}

// Indexed loop
for (int i = 0; i < motorIDs.size(); i++) {
    System.out.println("Motor " + i + ": " + motorIDs.get(i));
}
```

<h2> ArrayList vs Array </h2>

**Use ArrayList when**:
- Size changes frequently
- Need to insert/remove elements
- Want built-in utility methods

**Use Array when**:
- Size is fixed and known
- Need maximum performance
- Working with primitive types directly
