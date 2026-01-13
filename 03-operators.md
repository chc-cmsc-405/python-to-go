# 03 - Operators

[← Back to Go Guide](README.md)

Most operators work the same in Go as in Python. Key differences: integer division between integers, symbols for logical operators (`&&`, `||`, `!`), and no exponent operator—use `math.Pow()`.

---

## Arithmetic

| Operation | Python | Go |
|-----------|--------|-----|
| Addition | `a + b` | `a + b` |
| Subtraction | `a - b` | `a - b` |
| Multiplication | `a * b` | `a * b` |
| Division | `a / b` (float) | `a / b` (int if both int!) |
| Modulus | `a % b` | `a % b` |
| Exponent | `a ** b` | `math.Pow(a, b)` |

## Integer Division

```go
7 / 2     // = 3 (integer division!)
7.0 / 2   // = 3.5 (float division)
```

## Increment/Decrement

```go
x++  // x = x + 1 (statement only, not expression)
x--  // x = x - 1
```

## Comparison

| Operation | Python | Go |
|-----------|--------|-----|
| Equal | `==` | `==` |
| Not equal | `!=` | `!=` |
| Less than | `<` | `<` |
| Greater than | `>` | `>` |

## Logical

| Operation | Python | Go |
|-----------|--------|-----|
| And | `and` | `&&` |
| Or | `or` | `\|\|` |
| Not | `not` | `!` |

```go
if x > 0 && y > 0 {
    fmt.Println("Both positive")
}
if !found {
    fmt.Println("Not found")
}
```

---

[← Previous: Data Types](02-data-types.md) | [Next: Control Flow →](04-control-flow.md)
