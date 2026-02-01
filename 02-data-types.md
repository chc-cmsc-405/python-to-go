# 02 - Data Types

[← Back to Go Guide](README.md)

Go is statically typed—every variable has a fixed type. However, Go has excellent type inference with `:=`. Every type has a "zero value" that variables default to if not initialized.

---

## Basic Types

| Concept | Python | Go |
|---------|--------|-----|
| **Integer** | `x = 42` | `x := 42` (int) |
| **Float** | `x = 3.14` | `x := 3.14` (float64) |
| **Boolean** | `True`, `False` | `true`, `false` |
| **String** | `"hello"` or `'hello'` | `"hello"` (double quotes only) |
| **Character** | `'a'` (string) | `'a'` (rune, int32) |

## Zero Values

Uninitialized variables get a zero value:

| Type | Zero Value |
|------|------------|
| `int`, `float64` | `0` |
| `bool` | `false` |
| `string` | `""` |
| `pointer`, `slice`, `map` | `nil` |

```go
var count int      // 0
var name string    // ""
var active bool    // false
```

---

## Strings

Go strings are immutable. Most operations are in the `strings` package.

### String Basics

| Concept | Python | Go |
|---------|--------|-----|
| **Create** | `s = "hello"` | `s := "hello"` |
| **Length** | `len(s)` | `len(s)` |
| **Concatenate** | `s1 + s2` | `s1 + s2` |
| **Access char** | `s[0]` | `s[0]` (returns byte) |
| **Uppercase** | `s.upper()` | `strings.ToUpper(s)` |
| **Lowercase** | `s.lower()` | `strings.ToLower(s)` |
| **Strip whitespace** | `s.strip()` | `strings.TrimSpace(s)` |
| **Split** | `s.split(",")` | `strings.Split(s, ",")` |
| **Join** | `",".join(list)` | `strings.Join(slice, ",")` |

```go
s := "Hello"       // String
c := 'a'           // Rune (character)
raw := `C:\path`   // Raw string (backticks, no escaping)
```

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

---

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

## Type Conversions

| Python | Go |
|--------|-----|
| `int("42")` | `strconv.Atoi("42")` |
| `float("3.14")` | `strconv.ParseFloat("3.14", 64)` |
| `str(42)` | `strconv.Itoa(42)` |
| `int(3.7)` | `int(3.7)` |

```go
import "strconv"

num, err := strconv.Atoi("42")       // Returns value AND error
if err != nil {
    // Handle error
}
text := strconv.Itoa(100)            // Int to string
truncated := int(3.7)                // 3 (explicit conversion)
```

### All Conversion Functions

| Function | Converts |
|----------|----------|
| `strconv.Atoi(s)` | string → int |
| `strconv.Itoa(n)` | int → string |
| `strconv.ParseFloat(s, 64)` | string → float64 |
| `strconv.ParseBool(s)` | string → bool |
| `strconv.FormatFloat(f, 'f', -1, 64)` | float64 → string |

---

## Nil

Go uses `nil` instead of `None`:

```go
var s []int           // nil slice
if s == nil { }       // Check for nil
```

**Note:** Basic types (int, string, bool) cannot be nil. Only pointers, slices, maps, channels, and interfaces can be nil.

---

[← Previous: Basics](01-basics.md) | [Next: Operators →](03-operators.md)
