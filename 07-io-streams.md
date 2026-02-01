# 07 - I/O Streams

[← Back to Go Guide](README.md)

Go provides file operations through the `os` and `bufio` packages. Error handling is explicit—functions return both a result and an error. This section covers file I/O—for console I/O (`fmt.Scan`), see [01-basics](01-basics.md).

---

## Reading a File

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

## Writing to a File

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

## Common File Operations

| Task | Python | Go |
|------|--------|-----|
| **Open for reading** | `open("f.txt", "r")` | `os.Open("f.txt")` |
| **Open for writing** | `open("f.txt", "w")` | `os.Create("f.txt")` |
| **Read line** | `line = file.readline()` | `scanner.Scan(); line := scanner.Text()` |
| **Read all lines** | `for line in file:` | `for scanner.Scan() { }` |
| **Write string** | `file.write(text)` | `file.WriteString(text)` |
| **Auto-close** | `with open(...) as f:` | `defer file.Close()` |

## Reading CSV Data

**Sample file (`grades.csv`):**
```
Alice,Math,95
Bob,English,87
Charlie,Math,92
```

**Python:**
```python
with open("grades.csv", "r") as file:
    for line in file:
        parts = line.strip().split(",")
        name = parts[0]
        subject = parts[1]
        score = int(parts[2])
```

**Go:**
```go
import (
    "bufio"
    "fmt"
    "os"
    "strconv"
    "strings"
)

file, err := os.Open("grades.csv")
if err != nil {
    return
}
defer file.Close()

scanner := bufio.NewScanner(file)
for scanner.Scan() {
    parts := strings.Split(scanner.Text(), ",")
    name := parts[0]
    subject := parts[1]
    score, _ := strconv.Atoi(parts[2])
    fmt.Printf("%s - %s: %d\n", name, subject, score)
}
```

Go's `strings.Split(",")` returns all parts at once, similar to Python.

## Using defer for Cleanup

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

## Error Handling Pattern

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

## Reading Entire File

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

## Common I/O Packages

| Package | Purpose |
|---------|---------|
| `os` | File operations (Open, Create, ReadFile) |
| `bufio` | Buffered I/O (Scanner for line-by-line reading) |
| `io` | I/O primitives and interfaces |
| `strings` | String manipulation (Split, Contains) |
| `strconv` | String conversions (Atoi, Itoa) |

---

[← Previous: Data Structures](06-data-structures.md) | [Next: Custom Types →](08-custom-types.md)
