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

Go strings are immutable. Most operations are in the `strings` package.

### String Basics

| Concept | Python | Go |
|---------|--------|-----|
| **Length** | `len(s)` | `len(s)` |
| **Concatenate** | `s1 + s2` | `s1 + s2` |
| **Access char** | `s[0]` | `s[0]` (returns byte) |
| **Uppercase** | `s.upper()` | `strings.ToUpper(s)` |
| **Lowercase** | `s.lower()` | `strings.ToLower(s)` |
| **Strip whitespace** | `s.strip()` | `strings.TrimSpace(s)` |
| **Split** | `s.split(",")` | `strings.Split(s, ",")` |
| **Join** | `",".join(list)` | `strings.Join(slice, ",")` |

### String Operations (Finding & Extracting)

| Concept | Python | Go |
|---------|--------|-----|
| **Find** | `s.find("ell")` | `strings.Index(s, "ell")` |
| **Find from end** | `s.rfind("l")` | `strings.LastIndex(s, "l")` |
| **Substring** | `s[1:4]` | `s[1:4]` |
| **Contains** | `"x" in s` | `strings.Contains(s, "x")` |
| **Starts with** | `s.startswith("He")` | `strings.HasPrefix(s, "He")` |
| **Ends with** | `s.endswith("!")` | `strings.HasSuffix(s, "!")` |

### String Modifiers

| Concept | Python | Go |
|---------|--------|-----|
| **Replace all** | `s.replace("o", "0")` | `strings.ReplaceAll(s, "o", "0")` |
| **Replace n times** | N/A | `strings.Replace(s, "o", "0", n)` |

```go
import "strings"

text := "Hello, World!"
fmt.Println(strings.Index(text, "World"))       // 7
fmt.Println(strings.Contains(text, "World"))    // true
fmt.Println(strings.HasPrefix(text, "Hello"))   // true
fmt.Println(strings.ReplaceAll(text, "o", "0")) // Hell0, W0rld!
fmt.Println(text[0:5])                          // Hello
```

## Character Functions

Go provides character functions in the `unicode` package. In Python, these are methods on strings. In Go, they're functions that take a `rune` (Go's character type).

| Task | Python | Go |
|------|--------|-----|
| **Is letter?** | `c.isalpha()` | `unicode.IsLetter(c)` |
| **Is digit?** | `c.isdigit()` | `unicode.IsDigit(c)` |
| **Is whitespace?** | `c.isspace()` | `unicode.IsSpace(c)` |
| **Is uppercase?** | `c.isupper()` | `unicode.IsUpper(c)` |
| **Is lowercase?** | `c.islower()` | `unicode.IsLower(c)` |
| **To uppercase** | `c.upper()` | `unicode.ToUpper(c)` |
| **To lowercase** | `c.lower()` | `unicode.ToLower(c)` |

**Python:**
```python
text = "Hello123"
for c in text:
    if c.isalpha():
        print(c.upper())
    elif c.isdigit():
        print(c)
```

**Go:**
```go
import (
    "fmt"
    "unicode"
)

text := "Hello123"
for _, c := range text {
    if unicode.IsLetter(c) {
        fmt.Print(string(unicode.ToUpper(c)))
    } else if unicode.IsDigit(c) {
        fmt.Print(string(c))
    }
}
```

**Note:** Iterating over a string with `range` gives you `rune` values (Unicode code points), which is what the `unicode` functions expect.

---

[← Previous: Functions](05-functions.md) | [Next: I/O Streams →](07-io-streams.md)
