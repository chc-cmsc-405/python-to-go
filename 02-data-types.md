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

## Strings

```go
s := "Hello"       // String
c := 'a'           // Rune (character)
raw := `C:\path`   // Raw string (backticks)
```

## Nil

Go uses `nil` instead of `None`:

```go
var s []int           // nil slice
if s == nil { }       // Check for nil
```

**Note:** Basic types (int, string, bool) cannot be nil.

## Type Conversion

| Python | Go |
|--------|-----|
| `int("42")` | `strconv.Atoi("42")` |
| `str(42)` | `strconv.Itoa(42)` |
| `int(3.7)` | `int(3.7)` |

```go
import "strconv"

num, err := strconv.Atoi("42")  // Returns value AND error
text := strconv.Itoa(100)
truncated := int(3.7)  // 3
```

---

[← Previous: Basics](01-basics.md) | [Next: Operators →](03-operators.md)
