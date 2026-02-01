# Go Reading Guide by Phase

This guide maps the Python-to-Go reference materials to the course phases. Read the assigned sections **before** watching the async videos—they'll provide context and help you recognize familiar patterns.

---

## Phase 1: Basics (Session 1 Async)

**Topics:** Variables, types, I/O, operators

| Read | Sections | Key Concepts |
|------|----------|--------------|
| [01-basics](01-basics.md) | All | Hello World, fmt.Println, variables, := |
| [02-data-types](02-data-types.md) | All | int, float64, string, bool, type conversion |
| [03-operators](03-operators.md) | All | Arithmetic, comparison, logical (&&, \|\|, !) |

**Key takeaways:**
- Use `:=` for short variable declaration (type inferred)
- Use `var x int` for explicit type declaration
- `fmt.Println()` instead of `print()`
- `fmt.Scan()` or `bufio.Scanner` for input
- No semicolons needed (compiler adds them)
- No parentheses around `if`/`for` conditions

---

## Phase 2: Collections (Session 3-4)

**Topics:** Slices, maps, iteration, file I/O

| Read | Sections | Key Concepts |
|------|----------|--------------|
| [04-control-flow](04-control-flow.md) | All | if/else, for loops, range |
| [05-data-structures](05-data-structures.md) | All | Slices, maps, strings, file I/O |

**Key takeaways:**
- Slices (`[]int`) are like Python lists but single-typed
- Use `append(slice, item)` — must reassign! (`s = append(s, x)`)
- Use `len(s)` for length (same as Python)
- `for i, v := range slice` is like `for i, v in enumerate(list)`
- Maps: `map[string]int` — use `make()` to create
- Check map key: `value, ok := m[key]`
- Use `defer file.Close()` for cleanup (like Python's `with`)

---

## Phase 3: Structs & Methods (Session 5-7)

**Topics:** Structs, methods, interfaces

| Read | Sections | Key Concepts |
|------|----------|--------------|
| [06-functions](06-functions.md) | All | Functions, multiple returns, error handling |
| [07-structs-interfaces](07-structs-interfaces.md) | All | Structs, methods, receivers, interfaces |

**Key takeaways:**
- Go has no classes — use structs + methods instead
- Methods have receivers: `func (d Dog) Bark()`
- Use pointer receiver `*Dog` to modify the struct
- Interfaces are implicit — no `implements` keyword
- Return `(result, error)` pattern instead of exceptions
- Composition instead of inheritance: embed structs

---

## Phase 4: Unique Features (Session 8)

**Topics:** Goroutines, channels, concurrency

| Read | Sections | Key Concepts |
|------|----------|--------------|
| [08-unique-features](08-unique-features.md) | All | Goroutines, channels, defer, error handling |

**Key takeaways:**
- `go function()` launches a goroutine (lightweight thread)
- Channels (`chan`) communicate between goroutines
- `ch <- value` sends, `value := <-ch` receives
- Errors are values — check them explicitly
- `defer` schedules cleanup to run when function returns
- No try/catch — explicit error checking with `if err != nil`

---

## Quick Reference: What to Read When

| Phase | Session | Read Before Class |
|-------|---------|-------------------|
| 1 | S1 (Wed) | 01-basics, 02-data-types, 03-operators |
| 2 | S3 (Mon) | 04-control-flow, 05-data-structures |
| 3 | S5 (Mon) | 06-functions, 07-structs-interfaces |
| 4 | S8 (Wed) | 08-unique-features |

---

## Full Reference

For complete coverage or later review, all sections are available:

| Guide | Topics |
|-------|--------|
| [01-basics](01-basics.md) | Hello World, I/O, variables, constants |
| [02-data-types](02-data-types.md) | Types, zero values, type conversion |
| [03-operators](03-operators.md) | Arithmetic, comparison, logical |
| [04-control-flow](04-control-flow.md) | If/else, for, switch, range |
| [05-data-structures](05-data-structures.md) | Slices, maps, strings, file I/O |
| [06-functions](06-functions.md) | Functions, multiple returns, variadic |
| [07-structs-interfaces](07-structs-interfaces.md) | Structs, methods, interfaces, composition |
| [08-unique-features](08-unique-features.md) | Goroutines, channels, defer, errors |
