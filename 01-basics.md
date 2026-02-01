# 01 - Basics

[← Back to Go Guide](README.md)

Every Go program needs a `main` function in a `main` package as its entry point. Go enforces simplicity—there's only one way to format code (`go fmt`), and unused imports or variables cause compilation errors. The syntax is cleaner than C++/Java: no semicolons needed (auto-inserted), no parentheses around conditions, and type declarations come after variable names.

---

## Comments

| Python | Go |
|--------|-----|
| `# Single line comment` | `// Single line comment` |
| `""" Multi-line comment """` | `/* Multi-line comment */` |

## Hello World

**Python:**
```python
print("Hello, World!")
```

**Go:**
```go
package main

import "fmt"

func main() {
    fmt.Println("Hello, World!")
}
```

**Key points:**
- `package main` is required for executable programs
- `import "fmt"` brings in the formatting package
- `func main()` is the entry point
- No semicolons needed

## Console Output

| Python | Go |
|--------|-----|
| `print(value)` | `fmt.Println(value)` |
| `print(a, b, c)` | `fmt.Println(a, b, c)` |
| `print(f"Value: {x}")` | `fmt.Printf("Value: %v\n", x)` |
| `print("hi", end="")` | `fmt.Print("hi")` |

**Format verbs:**
```go
fmt.Printf("String: %s\n", name)     // String
fmt.Printf("Integer: %d\n", num)     // Integer
fmt.Printf("Float: %.2f\n", pi)      // Float with 2 decimals
fmt.Printf("Any type: %v\n", x)      // Default format
```

## Console Input

Go uses `fmt.Scan` for console input:

**Python:**
```python
name = input("Enter name: ")
age = int(input("Enter age: "))
```

**Go:**
```go
package main

import "fmt"

func main() {
    var name string
    var age int

    fmt.Print("Enter name: ")
    fmt.Scan(&name)  // & passes address

    fmt.Print("Enter age: ")
    fmt.Scan(&age)
}
```

## Variables

**Python:**
```python
x = 10
name = "Alice"
```

**Go:**
```go
// Short declaration (most common)
x := 10
name := "Alice"

// Explicit declaration
var x int = 10
var name string = "Alice"

// Zero value initialization
var count int    // count = 0
```

**Key:** Unused variables cause compile errors in Go!

## Constants

| Python | Go |
|--------|-----|
| `PI = 3.14159` (convention) | `const PI = 3.14159` |

```go
const PI = 3.14159
const MaxSize = 100

// Multiple constants
const (
    StatusOK    = 200
    StatusError = 500
)
```

---

[Next: Data Types →](02-data-types.md)
