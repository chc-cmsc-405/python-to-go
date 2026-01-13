# 07 - Structs & Interfaces

[← Back to Go Guide](README.md)

Go doesn't have classes—it uses **structs** for data and **methods** attached to them. Instead of inheritance, Go uses **composition** and **interfaces**.

---

## Structs

**Python:**
```python
class Dog:
    def __init__(self, name, age):
        self.name = name
        self.age = age
```

**Go:**
```go
type Dog struct {
    Name string
    Age  int
}

d := Dog{Name: "Buddy", Age: 3}
```

## Methods

```go
type Dog struct {
    Name string
}

// Value receiver
func (d Dog) Bark() {
    fmt.Printf("%s says woof!\n", d.Name)
}

// Pointer receiver (can modify)
func (d *Dog) SetName(name string) {
    d.Name = name
}

d := Dog{Name: "Buddy"}
d.Bark()
d.SetName("Max")
```

## Constructor Functions

```go
func NewDog(name string, age int) *Dog {
    return &Dog{Name: name, Age: age}
}
```

## Composition (Instead of Inheritance)

```go
type Animal struct {
    Name string
}

type Dog struct {
    Animal  // Embedded
    Breed string
}

d := Dog{Animal: Animal{Name: "Buddy"}, Breed: "Lab"}
fmt.Println(d.Name)  // Access embedded field
```

## Interfaces

Types satisfy interfaces implicitly—no `implements` keyword:

```go
type Speaker interface {
    Speak()
}

type Dog struct{ Name string }
func (d Dog) Speak() { fmt.Println("Woof!") }

type Cat struct{ Name string }
func (c Cat) Speak() { fmt.Println("Meow!") }

func MakeSpeak(s Speaker) {
    s.Speak()
}

MakeSpeak(Dog{})  // Works
MakeSpeak(Cat{})  // Works
```

## Empty Interface

`interface{}` or `any` accepts any type:

```go
func printAny(x any) {
    fmt.Println(x)
}
```

---

[← Previous: Functions](06-functions.md) | [Next: Unique Features →](08-unique-features.md)
