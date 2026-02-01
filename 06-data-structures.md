# 06 - Data Structures

[← Back to Go Guide](README.md)

Go provides slices (dynamic arrays) and maps (key-value). Slices are the most commonly used. Maps are built into the language.

---

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

## Strings

| Concept | Python | Go |
|---------|--------|-----|
| **Length** | `len(s)` | `len(s)` |
| **Contains** | `"x" in s` | `strings.Contains(s, "x")` |
| **Split** | `s.split(",")` | `strings.Split(s, ",")` |
| **Upper** | `s.upper()` | `strings.ToUpper(s)` |

```go
import "strings"

text := "Hello, World!"
fmt.Println(strings.Contains(text, "World"))
fmt.Println(strings.ToUpper(text))
```

---

[← Previous: Functions](05-functions.md) | [Next: I/O Streams →](07-io-streams.md)
