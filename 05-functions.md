# 05 - Functions

[← Back to Go Guide](README.md)

Go functions are first-class values. Multiple return values are common, especially for error handling. No function overloading.

---

## Basic Function

**Python:**
```python
def add(a, b):
    return a + b
```

**Go:**
```go
func add(a, b int) int {
    return a + b
}
```

## Multiple Return Values

```go
func divide(a, b float64) (float64, error) {
    if b == 0 {
        return 0, errors.New("division by zero")
    }
    return a / b, nil
}

result, err := divide(10, 2)
if err != nil {
    fmt.Println("Error:", err)
    return
}
```

## Variadic Functions

```go
func sum(numbers ...int) int {
    total := 0
    for _, n := range numbers {
        total += n
    }
    return total
}

sum(1, 2, 3, 4, 5)
```

## Anonymous Functions

```go
double := func(x int) int {
    return x * 2
}
fmt.Println(double(5))  // 10
```

## Closures

```go
func counter() func() int {
    count := 0
    return func() int {
        count++
        return count
    }
}

c := counter()
fmt.Println(c())  // 1
fmt.Println(c())  // 2
```

## Pass by Value and Pointers

In Python, the behavior depends on the type:
- **Immutable types** (`int`, `str`, `tuple`): Changes inside a function don't affect the original
- **Mutable types** (`list`, `dict`): Changes inside a function affect the original

Go is **always pass-by-value**—everything is copied. To modify the original, you must explicitly use pointers:

```go
// Pass by value (copy) — changes stay inside the function
func doubleByValue(x int) {
    x = x * 2
    fmt.Println("Inside function:", x)
}

// Pass by pointer — changes affect the caller
func doubleByPointer(x *int) {
    *x = *x * 2
    fmt.Println("Inside function:", *x)
}

func main() {
    a := 5
    doubleByValue(a)
    fmt.Println("After doubleByValue:", a)  // Still 5

    b := 5
    doubleByPointer(&b)
    fmt.Println("After doubleByPointer:", b)  // Now 10
}
```

**Note:** Slices and maps appear to be passed by reference because they contain internal pointers, but technically the header is copied. For most purposes, modifications to slice/map contents affect the original.

## The const Keyword

Go's `const` is limited to compile-time constants—numbers, strings, and booleans only:

```go
const MaxSize = 100      // OK
const Name = "Alice"     // OK
const list = []int{1,2}  // Error! Slices can't be const
```

**Note:** Unlike C++, Go has no way to mark a function parameter as "read-only." If you pass a slice to a function, that function can always modify its contents.

---

[← Previous: Control Flow](04-control-flow.md) | [Next: Data Structures →](06-data-structures.md)
