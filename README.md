# Go For Python Programmers

You already know Python. This guide helps you learn Go by showing side-by-side comparisons with familiar Python syntax.

## How to Use This Guide

- **Quick Reference** — This README has dense comparison tables for quick lookup
- **Deep Dive** — Individual pages (linked below) cover specific topics in detail with code examples
- **Side-by-Side** — Python code on the left, Go on the right

---

## About Go

Go (or Golang) is a statically-typed, compiled language created at Google for building simple, reliable, and efficient software. It compiles directly to machine code with fast compilation times. Go emphasizes simplicity—it intentionally has fewer features than languages like Java or C++. Unlike object-oriented languages, Go uses **composition over inheritance** with structs and interfaces instead of classes. Go is widely used for cloud services, CLI tools, and concurrent applications. The syntax is cleaner than C-family languages, making it relatively easy to learn coming from Python.

---

## Key Differences

Go is a statically-typed, compiled language designed for simplicity and concurrency. Unlike Python, you must declare variable types (or use `:=` for inference), use braces for code blocks, and there are no classes—just structs and functions.

| Aspect | Python | Go |
|--------|--------|-----|
| **Typing** | Dynamic | Static (with inference) |
| **Execution** | Interpreted | Compiled (fast!) |
| **Memory** | Garbage collected | Garbage collected |
| **Blocks** | Indentation | Braces `{ }` |
| **Semicolons** | Not required | Optional (auto-inserted) |
| **Main function** | Optional | Required: `func main()` |
| **OOP** | Classes and inheritance | Structs and composition |
| **Concurrency** | Threading/async | Built-in goroutines |

---

## Quick Reference

### Output & Input

Go uses the `fmt` package for formatted I/O. `Println` adds a newline, `Print` doesn't, and `Printf` uses format verbs like C.

| Task | Python | Go |
|------|--------|-----|
| Print | `print("hi")` | `fmt.Println("hi")` |
| Print variable | `print(x)` | `fmt.Println(x)` |
| Formatted print | `print(f"Value: {x}")` | `fmt.Printf("Value: %v\n", x)` |
| Print without newline | `print("hi", end="")` | `fmt.Print("hi")` |

### Variables & Constants

Go has type inference with `:=` (short declaration) inside functions. Use `var` for explicit type declaration or package-level variables. Constants use `const`.

| Task | Python | Go |
|------|--------|-----|
| Integer | `x = 5` | `x := 5` or `var x int = 5` |
| Float | `x = 3.14` | `x := 3.14` or `var x float64 = 3.14` |
| String | `s = "hello"` | `s := "hello"` |
| Boolean | `flag = True` | `flag := true` |
| Constant | `PI = 3.14` | `const PI = 3.14` |

### Control Flow

Go requires braces but no parentheses around conditions (the opposite of most C-family languages). There's no ternary operator—use if/else instead.

| Task | Python | Go |
|------|--------|-----|
| If | `if x > 0:` | `if x > 0 {` |
| Else if | `elif x < 0:` | `} else if x < 0 {` |
| Else | `else:` | `} else {` |
| Ternary | `"yes" if x else "no"` | None (use if/else) |

### Loops

Go has only one loop keyword: `for`. It handles all loop patterns—traditional, while-style, and range-based.

| Task | Python | Go |
|------|--------|-----|
| For (range) | `for i in range(5):` | `for i := 0; i < 5; i++ {` |
| For (each) | `for x in items:` | `for _, x := range items {` |
| While | `while x > 0:` | `for x > 0 {` |
| Infinite | `while True:` | `for {` |

### Functions

Go functions declare return type after parameters. Multiple return values are common, especially for error handling.

| Task | Python | Go |
|------|--------|-----|
| Define | `def foo():` | `func foo() {` |
| With return | `def add(a, b): return a + b` | `func add(a, b int) int { return a + b }` |
| Multiple returns | `return a, b` | `func swap(a, b int) (int, int) { return b, a }` |

### Data Structures

Go uses slices (dynamic arrays) and maps. Slices are more flexible than arrays and are what you'll use most of the time.

| Task | Python | Go |
|------|--------|-----|
| List / Slice | `[1, 2, 3]` | `[]int{1, 2, 3}` |
| Append | `list.append(x)` | `slice = append(slice, x)` |
| Access | `list[0]` | `slice[0]` |
| Length | `len(list)` | `len(slice)` |
| Dictionary / Map | `{"a": 1}` | `map[string]int{"a": 1}` |

### Structs (Instead of Classes)

Go doesn't have classes. It uses structs to group data and attaches methods to them.

| Task | Python | Go |
|------|--------|-----|
| Define | `class Dog:` | `type Dog struct { }` |
| Constructor | `def __init__(self):` | Function returning struct |
| Method | `def bark(self):` | `func (d Dog) bark() {` |
| Create object | `d = Dog()` | `d := Dog{}` |

### Operators & Comments

Most operators are the same. Go uses `&&`, `||`, `!` for logical operators like other C-family languages.

| Task | Python | Go |
|------|--------|-----|
| And / Or / Not | `and` `or` `not` | `&&` `\|\|` `!` |
| Exponent | `x ** 2` | `math.Pow(x, 2)` |
| Integer division | `7 // 2` → `3` | `7 / 2` → `3` |
| Float division | `7 / 2` → `3.5` | `7.0 / 2` → `3.5` |
| Comment | `# comment` | `// comment` |
| Multi-line | `""" comment """` | `/* comment */` |

---

## Common Imports

Go uses `import` statements. Standard library packages are high-quality and cover most needs:

```go
import (
    "fmt"      // Formatted I/O (Println, Printf, Scanf)
    "strings"  // String manipulation
    "strconv"  // String conversion (Atoi, Itoa)
    "math"     // Math functions
    "os"       // Operating system functions
    "io"       // I/O primitives
)
```

---

## Detailed Sections

For more examples and in-depth explanations, see:

| Section | Topics |
|---------|--------|
| [01 - Basics](01-basics.md) | Comments, Hello World, I/O, variables, constants |
| [02 - Data Types](02-data-types.md) | Types, zero values, type conversion |
| [03 - Operators](03-operators.md) | Arithmetic, comparison, logical |
| [04 - Control Flow](04-control-flow.md) | If/else, for, switch |
| [05 - Data Structures](05-data-structures.md) | Slices, maps, strings |
| [06 - Functions](06-functions.md) | Definition, multiple returns, variadic, closures |
| [07 - Structs & Interfaces](07-structs-interfaces.md) | Structs, methods, interfaces, composition |
| [08 - Unique Features](08-unique-features.md) | Goroutines, channels, error handling, defer |

---

*This guide covers the basics. Go has many more features that you'll learn throughout the course.*
