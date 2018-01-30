@title[Introduction]
## /// CPM Engineering - Introduction to Go
---

#### Go(lang)

![alt text](./assets/gopher.png "Gopher")

* Created at Google by (Rob Pike, Ken Thompson, Robert Griesemer) since 2009
released in 2012
* Compiled (C/C++, Java, Rust)
* Statically typed (Java, C/C++, Kotlin)
* Imperative paradigm (Perl, Ruby, PHP, Rust, Groovy)
* Open source (all the tools including the programming language itself)
* Available on all major platforms (Linux, Windows, Darwin, BSD, available on
  mobile devices since 2015)

---
#### Tools && Ecosystem

`gofmt` -
`dep` -

---

Go structures instead of Objects.

```go
package main

// impor the fmt package from std-lib.
import (
  "fmt"
)

// declaring a new structure.
// declaring a structure lowercase makes it available at the package scope only.  
// declaring a struct with a capital letter, makes it available at the global
// scope.
type demo struct {
  name string
  id   int
}

// declaring a structure method that returns a value assigned
// to the struct.
func(d *demo) getName() string {
  return t.name
}

// declaring a structure method that sets the value of a structure
// field.
func(d *demo) setID(newID int) {
  t.id = newID
}

func(d *demo) getID() int {
  return d.id
}

func main()  {
  // create a new demo structure instance and assign values to its fields.
  newStruct := demo{
    name: 'test',
    id: 1,
  }
  fmt.Println(newStruct.getName())
  newStruct.setID(2)
  fmt.Println(newStruct.getID())
}

```
