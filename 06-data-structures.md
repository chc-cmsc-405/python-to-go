# 06 - Data Structures

[← Back to Go Guide](README.md)

Go provides arrays (fixed-size), slices (dynamic), and maps (key-value). Slices are the most commonly used—arrays are rare in practice.

## Contents

- [Arrays](#arrays)
- [Slices](#slices)
- [Removing from Slices](#removing-from-slices)
- [Iterating Over Slices](#iterating-over-slices)
- [Maps](#maps)

---

## Arrays

Go arrays have a fixed size that's part of the type. `[5]int` and `[10]int` are different types.

```go
var numbers [5]int                    // Zero-initialized array of 5 ints
scores := [3]int{95, 87, 92}          // Array with values
names := [...]string{"Alice", "Bob"}  // Size inferred from values (2)

fmt.Println(len(scores))  // 3
fmt.Println(scores[0])    // 95
// scores = append(scores, 100)  // Error! Can't append to arrays
```

**When to use:** Arrays are rarely used directly in Go. Prefer slices for most cases.

## Slices

| Concept | Python | Go |
|---------|--------|-----|
| **Create** | `[1, 2, 3]` | `[]int{1, 2, 3}` |
| **Access** | `list[0]` | `s[0]` |
| **Length** | `len(list)` | `len(s)` |
| **Append** | `list.append(x)` | `s = append(s, x)` |
| **Slice** | `list[1:3]` | `s[1:3]` |

**Python:**
```python
numbers = [1, 2, 3]
numbers.append(4)
print(numbers[0])
```

**Go:**
```go
numbers := []int{1, 2, 3}
numbers = append(numbers, 4)  // Must reassign!
fmt.Println(numbers[0])
```

### Pre-allocation

```go
s := make([]int, 5)      // Length 5
s := make([]int, 0, 100) // Length 0, capacity 100
```

## Removing from Slices

Go has no built-in remove function. You combine slicing and `append` to remove elements.

**Python:**
```python
numbers = [10, 20, 30, 40, 50]
numbers.remove(30)       # Remove by value
del numbers[0]           # Remove by index
numbers.pop()            # Remove last
```

**Go:**
```go
numbers := []int{10, 20, 30, 40, 50}

// Remove by index — combine slices around the gap
i := 2
numbers = append(numbers[:i], numbers[i+1:]...)  // Removes 30

// Remove last element
numbers = numbers[:len(numbers)-1]
```

The `append(s[:i], s[i+1:]...)` pattern takes everything before index `i` and everything after, joining them together. The `...` unpacks the second slice into individual arguments.

| Concept | Python | Go |
|---------|--------|-----|
| **Remove by value** | `list.remove(val)` | No built-in — loop to find index, then remove |
| **Remove by index** | `del list[i]` | `s = append(s[:i], s[i+1:]...)` |
| **Remove last** | `list.pop()` | `s = s[:len(s)-1]` |

## Iterating Over Slices

**Python:**
```python
for num in numbers:
    print(num)

for i, num in enumerate(numbers):
    print(f"{i}: {num}")
```

**Go:**
```go
// Range-based loop
for _, num := range numbers {
    fmt.Println(num)
}

// With index
for i, num := range numbers {
    fmt.Printf("%d: %d\n", i, num)
}
```

## Maps

| Concept | Python | Go |
|---------|--------|-----|
| **Create** | `{}` | `make(map[string]int)` |
| **Set** | `d["a"] = 1` | `m["a"] = 1` |
| **Get** | `d["a"]` | `m["a"]` |
| **Check key** | `"a" in d` | `_, ok := m["a"]` |
| **Delete** | `del d["a"]` | `delete(m, "a")` |

**Go:**
```go
scores := map[string]int{"Alice": 95}
scores["Bob"] = 87

if score, ok := scores["Alice"]; ok {
    fmt.Println(score)
}

for name, score := range scores {
    fmt.Printf("%s: %d\n", name, score)
}
```

---

[← Previous: Functions](05-functions.md) | [Next: I/O Streams →](07-io-streams.md)
