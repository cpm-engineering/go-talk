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
#### Tool chain  

* `cgo` - Cgo enables the creation of Go packages that call C code.  
* `cover` - Cover is a program for creating and analyzing the coverage profiles generated by "go test -coverprofile".  
* `fix` - Fix finds Go programs that use old features of the language and libraries and rewrites them to use newer ones.  
* `fmt` - Fmt formats Go packages, it is also available as an independent gofmt command with more general options.  
* `godoc` - Godoc extracts and generates documentation for Go packages.  
* `vet` - Vet examines Go source code and reports suspicious constructs, such as Printf calls whose arguments do not align with the format string.  
---
#### Popular Go projects
Moby (Docker), Kubernetes, OpenShift, Terraform, Packer, Consul, etcd, Prometheus, CRI-O, rkt.  
giantswarm (our current kubernetes infra is managed and run with Go apps).

---
#### Language quirks (Pedantic Go)
---
```go
// Can not compile a program with unused variables
// or unused imports
import (
  "net/http"
)

var unusedVar string

func main() {}
```
---
* Each file must be run through gofmt or satisfy gofmt constraints before
compilation
* gofmt will use builtin spacing and some minimal code 'linting'
---
```go
// declaring multiline variables with types, type inferred
// or with default values.
var (
	test            string
	intTest         int = 0
	testDefault     = "test"
)
```
---
Each error must be handled
```go
value, err := someFunc()
if err != nil {
  return err
}
// ignore the error returned - doable, but discouraged
value, _ := somFunc()
```
---
#### Standard library
---
Out of the box support for  
https://golang.org/pkg/   
special mention: builtin support for html templating  
---
#### The language
---
Go structures instead of Objects.

```go
type demo struct {
  name string
  id   int
}

func(d *demo) getName() string {
  return t.name
}

func(d *demo) setID(newID int) {
  d.id = newID
}

func(d *demo) getID() int {
  return d.id
}
```
---
Encoding/decoding is aided by struct tags (xml, json, bson)  
https://github.com/golang/go/wiki/Well-known-struct-tags  
Meta-information available via the reflect package.

```go
type Payload struct {
  Response int `json:"response,omitempty"`
}
```
---
Types satisfy an interface (automatically) when they contain
at least all defined methods of that interface.
```Go
type Service interface {
  Start()
  Stop()
}

type networkService struct {}
func(n *networkService) Start() {}
func(n *networkService) Stop() {}
```
---
Functions as first class citizens  

```go
type CmdFunc func(ctx context.Context) error

fakeFunc := func() error {
  return nil
}

func returnFunc(testFunc func() error) func() error {
  return func() error {
    if err := testFunc()
    return nil
  }
}
```
---
#### Concurrency primitives
---
Channels and goroutines  
Share by communicating as opposed to communicate by sharing
```go
ch := make(chan int)
go func() {
  ch <- 1
}()
fmt.Println(<-ch)
```
---
#### Honorable mentions
---
```go
file, err := os.Open('localFile')
defer file.Close()
```
---
init() Functionality
```go
func main() {

}

init(
  viper.SetConfigFile(".shep")
  viper.SetConfigType("json")
  logrus.SetLevel(logrus.DebugLevel)
)
```
---
Context package (cancelation and pipelines)
```go
import (
  "context"
)

```
---
Slices are not arrays
```go
slice = []string{
  'tes1',
  'test2',
  'test3',
}
```
