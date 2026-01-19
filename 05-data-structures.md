# 05 - Data Structures

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

| Concept | Python | Go |
|---------|--------|-----|
| **Length** | `len(s)` | `len(s)` |
| **Contains** | `"x" in s` | `strings.Contains(s, "x")` |
| **Split** | `s.split(",")` | `strings.Split(s, ",")` |
| **Upper** | `s.upper()` | `strings.ToUpper(s)` |

```go
import "strings"

text := "Hello, World!"
fmt.Println(strings.Contains(text, "World"))
fmt.Println(strings.ToUpper(text))
```

---

## File I/O

Go provides file operations through the `os` and `bufio` packages. Error handling is explicit—functions return both a result and an error.

### Reading a File

**Python:**
```python
with open("data.txt", "r") as file:
    for line in file:
        print(line.strip())
```

**Go:**
```go
import (
    "bufio"
    "fmt"
    "os"
)

file, err := os.Open("data.txt")
if err != nil {
    fmt.Println("Error:", err)
    return
}
defer file.Close()

scanner := bufio.NewScanner(file)
for scanner.Scan() {
    fmt.Println(scanner.Text())
}
```

### Writing to a File

**Python:**
```python
with open("output.txt", "w") as file:
    file.write("Hello, World!\n")
```

**Go:**
```go
import (
    "os"
)

file, err := os.Create("output.txt")
if err != nil {
    fmt.Println("Error:", err)
    return
}
defer file.Close()

file.WriteString("Hello, World!\n")
```

### Common File Operations

| Task | Python | Go |
|------|--------|-----|
| **Open for reading** | `open("f.txt", "r")` | `os.Open("f.txt")` |
| **Open for writing** | `open("f.txt", "w")` | `os.Create("f.txt")` |
| **Read line** | `line = file.readline()` | `scanner.Scan(); line := scanner.Text()` |
| **Read all lines** | `for line in file:` | `for scanner.Scan() { }` |
| **Write string** | `file.write(text)` | `file.WriteString(text)` |
| **Auto-close** | `with open(...) as f:` | `defer file.Close()` |

### Reading CSV Data

**Python:**
```python
with open("data.csv", "r") as file:
    for line in file:
        parts = line.strip().split(",")
        name = parts[0]
        score = int(parts[1])
```

**Go:**
```go
import (
    "bufio"
    "os"
    "strconv"
    "strings"
)

file, err := os.Open("data.csv")
if err != nil {
    return
}
defer file.Close()

scanner := bufio.NewScanner(file)
for scanner.Scan() {
    parts := strings.Split(scanner.Text(), ",")
    name := parts[0]
    score, _ := strconv.Atoi(parts[1])
    fmt.Printf("%s: %d\n", name, score)
}
```

### Using defer for Cleanup

Go's `defer` keyword schedules a function call to run when the surrounding function returns—similar to Python's `with` statement but more flexible:

```go
func processFile(filename string) error {
    file, err := os.Open(filename)
    if err != nil {
        return err
    }
    defer file.Close()  // Runs when function returns

    // Process file...
    return nil
}
```

### Error Handling Pattern

Go requires explicit error checking (no exceptions):

```go
file, err := os.Open("data.txt")
if err != nil {
    // Handle error
    fmt.Println("Could not open file:", err)
    return
}
defer file.Close()

// File operations here...
```

### Reading Entire File

For small files, you can read the entire contents at once:

```go
import "os"

data, err := os.ReadFile("data.txt")
if err != nil {
    return
}
content := string(data)
fmt.Println(content)
```

---

[← Previous: Control Flow](04-control-flow.md) | [Next: Functions →](06-functions.md)
