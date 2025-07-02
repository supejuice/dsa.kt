# DSA with Kotlin

---

## Loops

### Forward Loop  
```kotlin
for (i in 0 until 10) {
    println(i) // prints 0 to 9
}
```

### Reverse Loop  
```kotlin
for (i in 9 downTo 0) {
    println(i) // prints 9 to 0
}
```

---

## Arrays

### Types of Arrays  

#### `Array<Int>`  
- Stores **objects** (`Integer` in JVM).  
- **Higher memory usage** due to boxing.  
- Use when nullable values are needed (`Array<Int?>`).  
```kotlin
val arr: Array<Int> = arrayOf(10, 20, 30)
```

#### `IntArray`  
- Stores **primitive `int` values** directly.  
- **Better performance** and **less memory usage**.  
- Cannot hold `null`.  
```kotlin
val arr = intArrayOf(1, 2, 3) // Creates IntArray (not boxed Array<Int>)
```

### Common Methods  

```kotlin
val arr = intArrayOf(5, 2, 9, 1, 7, 2)

// Size and Indices
println("Size: ${arr.size}")
println("Indices: ${arr.indices}")

// Accessing Elements Safely
println("Element at 10: ${arr.getOrNull(10)}")  // null-safe access

// First and Last Elements
println("First: ${arr.first()}")
println("Last: ${arr.last()}")

// Min and Max
println("Min: ${arr.minOrNull()}")
println("Max: ${arr.maxOrNull()}")

// Sum and Average
println("Sum: ${arr.sum()}")
println("Average: ${arr.average()}")

// Sorting
println("Sorted: ${arr.sorted()}")
println("Sorted Desc: ${arr.sortedDescending()}")

// Distinct Elements
println("Distinct: ${arr.distinct()}")

// Counting Elements
println("Count of 2s: ${arr.count { it == 2 }}")

// Mapping and Filtering
val doubled = arr.map { it * 2 }
val evens = arr.filter { it % 2 == 0 }
println("Doubled: $doubled")
println("Evens: $evens")

// Checking Conditions
println("Any > 8? ${arr.any { it > 8 }}")
println("All > 0? ${arr.all { it > 0 }}")

// Index Operations
println("First index of 2: ${arr.indexOf(2)}")
println("Last index of 2: ${arr.lastIndexOf(2)}")

// Contains
println("Contains 9? ${arr.contains(9)}")

// Iterating
print("Elements: ")
arr.forEach { print("$it ") }
println()

// Reduce and Fold
val product = arr.reduce { acc, i -> acc * i }
val sumFold = arr.fold(10) { acc, i -> acc + i }  // 10 as initial
println("Product (reduce): $product")
println("Sum +10 (fold): $sumFold")

// Taking and Dropping
println("Take 3: ${arr.take(3)}")
println("Drop 3: ${arr.drop(3)}")

// Reversing
println("Reversed: ${arr.reversed()}")

// Indexed Iteration
for ((i, v) in arr.withIndex()) {
    println("Index $i → $v")
}

// Conversions
val asSet = arr.toSet()
val asList = arr.toList()
println("As Set: $asSet")
println("As List: $asList")

// Copying
val copy = arr.copyOf()
val clone = arr.clone()
println("Copied: ${copy.toList()}")
println("Cloned: ${clone.toList()}")

// Equality Check
println("Equals copy? ${arr.contentEquals(copy)}")
```

---

## Strings

### Properties and Behavior  
- **Immutable**: Methods like `replace()`, `uppercase()`, `trim()`, etc., return a **new string**.  
- **Properties** (`.length`) represent **state**.  
- **Functions** (`.isEmpty()`) represent **behavior**.  

### Common Methods  
```kotlin
val input = "  A man, a plan, a canal: Panama  "

// Trim and Case Conversion
val trimmed = input.trim()
val lower = trimmed.lowercase()

// Filtering and Palindrome Check
val cleaned = lower.filter { it.isLetterOrDigit() }
val isPalindrome = cleaned == cleaned.reversed()
println("Is palindrome: $isPalindrome")

// Contains, StartsWith, EndsWith
println("Contains 'canal'? -> ${input.contains("canal")}")
println("Starts with '  A'? -> ${input.startsWith("  A")}")
println("Ends with 'Panama  '? -> ${input.endsWith("Panama  ")}")

// Index Operations
println("First index of 'a': ${input.indexOf('a')}")
println("Last index of 'a': ${input.lastIndexOf('a')}")

// Safe Access
println("Char at index 100 (safe): ${input.getOrNull(100)}")

// Replace
val noColon = input.replace(":", "")
println("Removed colon: $noColon")
val digitsOnly = "a1b2c3".replace(Regex("[^0-9]"), "")
println("Digits only: $digitsOnly") // 123

// Mapping and Counting
val upperMapped = input.map { it.uppercaseChar() }.joinToString("")
val countA = input.count { it.lowercaseChar() == 'a' }
println("Uppercased: $upperMapped")
println("Count of 'a': $countA")

// Splitting and Joining
val words = input.split(" ")
val wordParts = input.split(Regex("[^A-Za-z]+"))
println("Split by space: $words")
println("Split by non-letters: $wordParts")
val joined = wordParts.filter { it.isNotEmpty() }.joinToString("-")
println("Joined parts: $joined")

// Substring and Windowed
println("Substring(2, 6): ${input.substring(2, 6)}")
val substrings = cleaned.windowed(5, 1)
println("Windowed substrings of size 5: $substrings")

// ZipWithNext
val diffs = cleaned.zipWithNext { a, b -> "$a->$b" }
println("Adjacent pairs: $diffs")
```

---

## Stack

### Example Usage  
```kotlin
val stack = mutableListOf<Int>()

// Push
stack.add(10)
stack.add(20)

// Pop
val top = stack.removeLast()
println(top) // 20

// Peek
val peek = stack.last()
println(peek) // 10
```

---

## Null-Safety

### Example Usage  
```kotlin
val len = userName?.length ?: 0
```

---

## Comparisons  

### Find Minimum  
```kotlin
val result = minOf(10, 20) // 10
```

### Find Maximum  
```kotlin
val result = maxOf(10, 20) // 20
```

### Constants  
```kotlin
val intMax = Int.MAX_VALUE
val intMin = Int.MIN_VALUE
val floatMax = Float.MAX_VALUE
val floatMin = -Float.MAX_VALUE
val charMin = Char.MIN_VALUE
```

---

## Filtering String or Array

### Example Usage  
```kotlin
val clean = s.filter { it is LetterOrDigit() }

val arr = intArrayOf(1, 2, 3, 4, 5)
val evens = arr.filter { it % 2 == 0 }  // List<Int>: [2, 4]
```

---

## Char Extensions  

### Methods  
- `isLetterOrDigit()`
- `isLetter()`
- `isDigit()`
- `isUpperCase()`
- `isLowerCase()`
