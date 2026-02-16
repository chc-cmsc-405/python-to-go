# 09 - Go Unique Features

[← Back to Go Guide](README.md)

These concepts don't have direct Python equivalents. Go has built-in concurrency with goroutines and channels, explicit error handling via return values, and `defer` for cleanup.

## Contents

- [Goroutines](#goroutines-lightweight-concurrency)
- [Channels](#channels-communication)
- [Error Handling](#error-handling)
- [Defer](#defer)
- [Panic and Recover](#panic-and-recover)
- [Memory Management: Python vs Go](#memory-management-python-vs-go)

---

## Goroutines (Lightweight Concurrency)

Goroutines are lightweight threads managed by Go:

**Python (threading):**
```python
import threading
def task():
    print("Running")
t = threading.Thread(target=task)
t.start()
```

**Go:**
```go
func task() {
    fmt.Println("Running")
}

go task()  // Starts goroutine
```

Just add `go` before a function call!

## Channels (Communication)

Channels allow goroutines to communicate safely:

```go
ch := make(chan string)

go func() {
    ch <- "Hello"  // Send
}()

msg := <-ch  // Receive
fmt.Println(msg)
```

### Buffered Channels

```go
ch := make(chan int, 3)  // Buffer size 3
ch <- 1
ch <- 2
ch <- 3
// ch <- 4  // Would block (buffer full)
```

## Error Handling

Go uses explicit error returns instead of exceptions:

**Python:**
```python
try:
    result = risky_operation()
except ValueError as e:
    print(f"Error: {e}")
```

**Go:**
```go
result, err := riskyOperation()
if err != nil {
    fmt.Println("Error:", err)
    return
}
// Use result
```

### Creating Errors

```go
import "errors"

func divide(a, b float64) (float64, error) {
    if b == 0 {
        return 0, errors.New("division by zero")
    }
    return a / b, nil
}
```

## Defer

`defer` schedules a function to run when the surrounding function returns:

**Python:**
```python
with open("file.txt") as f:
    content = f.read()
# File automatically closed
```

**Go:**
```go
f, err := os.Open("file.txt")
if err != nil {
    return err
}
defer f.Close()  // Will run when function returns

// Use f...
```

### Multiple Defers (LIFO)

```go
defer fmt.Println("First")
defer fmt.Println("Second")
defer fmt.Println("Third")
// Output: Third, Second, First
```

## Panic and Recover

For unrecoverable errors (use sparingly):

```go
func mayPanic() {
    panic("something went wrong")
}

func safeCall() {
    defer func() {
        if r := recover(); r != nil {
            fmt.Println("Recovered:", r)
        }
    }()
    mayPanic()
}
```

## Memory Management: Python vs Go

Both use garbage collection:

| Aspect | Python | Go |
|--------|--------|-----|
| **Memory management** | Automatic (GC) | Automatic (GC) |
| **GC type** | Reference counting + cycle detection | Concurrent, tri-color mark-and-sweep |
| **Manual control** | None | None (some tuning available) |
| **Memory leaks** | Rare | Rare |

## Key Differences Summary

| Concept | Python | Go |
|---------|--------|-----|
| Concurrency | `threading`, `asyncio` | `go` keyword, channels |
| Error handling | Exceptions | Return values |
| Cleanup | `with` statement | `defer` |
| Visibility | `_private` convention | Capitalization |

---

[← Previous: Custom Types](08-custom-types.md) | [Back to Go Guide](README.md)
