# DSA with Kotlin

### For Loops

**Forward:**  
```kotlin
for (i in 0 until 10) {
    println(i) // prints 0 to 9
}
```

**Reverse:**  
```kotlin
for (i in 9 downTo 0) {
    println(i)
}
```

---

### Arrays

- Kotlin uses `.size` for collections and arrays.  
- `.length` is used for `String` only.

**Array<Int>:**  
- Internally stores **objects** (`Integer` in JVM).  
- More **memory usage** due to boxing.  
- Use when you need nullable values (`Array<Int?>`).  
```kotlin
val arr: Array<Int> = arrayOf(10, 20, 30)
```

**IntArray:**  
- Stores **primitive `int` values** directly.  
- **Better performance** and **less memory**.  
- Cannot hold `null`.  
```kotlin
val arr = intArrayOf(1, 2, 3) // Creates IntArray (not boxed Array<Int>)
```

---

### Strings

- Properties (`.length`) represent **state**.  
- Functions/methods (`.isEmpty()`) represent **behavior**.  
- **Strings in Kotlin (like Java)** are **immutable**.  
- Any method like `replace()`, `uppercase()`, `trim()`, etc., returns a **new string**.

---

### Stack

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