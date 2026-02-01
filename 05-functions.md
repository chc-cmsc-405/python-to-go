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

## Pointers for Modification

```go
func double(x *int) {
    *x = *x * 2
}

num := 5
double(&num)
fmt.Println(num)  // 10
```

---

[← Previous: Control Flow](04-control-flow.md) | [Next: Data Structures →](06-data-structures.md)
