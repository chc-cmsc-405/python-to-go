# 04 - Control Flow

[← Back to Go Guide](README.md)

Go has only one loop keyword: `for`. It handles all loop patterns. Conditions don't need parentheses but braces are required. Go's `switch` doesn't fall through by default.

---

## If / Else

**Python:**
```python
if x > 0:
    print("Positive")
elif x < 0:
    print("Negative")
else:
    print("Zero")
```

**Go:**
```go
if x > 0 {
    fmt.Println("Positive")
} else if x < 0 {
    fmt.Println("Negative")
} else {
    fmt.Println("Zero")
}
```

### If with Short Statement

```go
if err := doSomething(); err != nil {
    fmt.Println("Error:", err)
}
```

## Switch

```go
switch grade {
case 'A':
    fmt.Println("Excellent")
case 'B', 'C':
    fmt.Println("Good")
default:
    fmt.Println("Unknown")
}

// Switch with no expression
switch {
case x > 0:
    fmt.Println("Positive")
case x < 0:
    fmt.Println("Negative")
}
```

## For Loop

**Traditional:**
```go
for i := 0; i < 5; i++ {
    fmt.Println(i)
}
```

**While-style:**
```go
for x > 0 {
    x--
}
```

**Infinite:**
```go
for {
    // break when done
}
```

**Range (for-each):**
```go
for i, item := range items {
    fmt.Println(i, item)
}

for _, item := range items {  // Ignore index
    fmt.Println(item)
}
```

## Break and Continue

```go
for i := 0; i < 10; i++ {
    if i == 5 {
        break
    }
    if i%2 == 0 {
        continue
    }
    fmt.Println(i)
}
```

---

[← Previous: Operators](03-operators.md) | [Next: Data Structures →](05-data-structures.md)
