## Overview

* Throws compile-time errors for linting issues
* Has a standardized format
* Uses block scope
* Built-ins can be shadowed
* Pass by value, pass by reference with a pointer
* Trailing commas required
* Accessing out-of-bounds element causes a "panic"

## Examples

```go
// Everything before the package declaration is the documentation
package main // has to start with the package name, has to be `main` to be called directly

imports (
  "fmt" // Prints, can handle arrays
  "math/random" // `math/random` is the import path, `random` is the package name
  "log"
  "math"
  "strings"
  "reflect"
  "time"
  "bufio"
  "os"
  "errors"
  "github.com/headfirstgo/greeting"
)

// Commands right before methods show up as the docs for that method
func main(){
  // Variables
  var message string
  message = "How are you?"
  // or
  message := "How are you?"
  // or
  thing1, thing2 := 1.2, 3.4

  // Printing
  fmt.Println("Hi!", message) // joins them with spaces

  // Types
  reflect.TypeOf(42)

  // Time
  now := time.Now()
  year := now.Year()
  unix := now.Unix()

  // Randomization
  rand.Seed(unix)
  someRandomNumber := rand.Intn(100) + 1 // makes it 1-100

  // String replacement
  replacer := strings.NewReplacer("#", "o") // `strings` is the value, `NewReplacer` is the method
  fixed := replacer.Replace("G# r#cks!")

  // CLI input
  fmt.Print("Enter something will ya!: ")
  reader = bufio.NewReader(os.Stdin)
  input, error := reader.ReadString('\n') // Newline terminates the input, using the rune
  // Can ignore one of the return values with _

  var someNumber int

  if err != nil {
    log.Fatal(err) // Kills the program
  } else if someNumber < 3 {
    // Something
  }

  // Conversions
  stringThatCanConvertToNumber := strings.TrimSpace(input) // Gets rid of newlines
  someFloat := strconv.ParseFloat(stringThatCanConvertToNumber)
  someInt := strconv.Atoi(stringThatCanConvertToNumber)

  // Loops
  for i := 0; i < someNumber; i++ {
    // Something
    continue
  }
  for i < someNumber {
    // Something
    break
  }

  // Formatting strings
  fmt.Printf("The %s cost %d cents.\n", "gum", 23)
  /*
    * %f float, %d int
      * Set the "width" with %5f, rounds and adds padding
      * Float display precision: %2.4f
    * %s string, %t boolean
    * %v value (infer the type), %#v print whitespace etc. as encoded
    * %% literal percent
  */

  // Errors
  err := errors.New("Oof")
  err = fmt.Errorf("This is an error %s", "message")
  err.Error() // Returns the error message, will be called automatically by loggers etc.

  // Pointers
  a := 1
  var b *string = &a // * is the pointer type, & gets the memory address
  b // the pointer itself
  *b // the value at the pointer
  *b = 2 // Update the value at the pointer

  c := 2
  d := double(&c)
  /*
  func double(number *int){
    *number *= 2
  }
  */

  // Constants
  const localConstant = "Hi"
  const ExportedConstant = "Hi"

  // Arrays
  var someArray [5]string // Declare size up front
  someArray[0] = "Hi"
  otherArray := [3]int{1, 2, 3}

  len(otherArray) // 3

  for index, value := range otherArray {
    // Can _ out the index
  }

  // Reading files
  file, err := os.Open("some-file.txt") // Returns a pointer to the file
  if err != nil {
    log.Fatal(err)
  }
  scanner := bufio.NewScanner(file) // Reads the file

  for scanner.Scan() {
    fmt.Println(scanner.Text())
  }

  err = file.Close() // Frees resources, only returns an error
  if err != nil {
    log.Fatal(err)
  }
  if scanner.Err() != nil { // Any errors that came up while reading the file
    log.Fatal(scanner.Err())
  }

  // Slices (a resizeable array, still one type)
  var someSlice []string
  someSlice = make([]string, 7)
  // or
  someSlice := []string{"a", "b", "c"}
  // or
  someSlice := []string{
    "a",
    "b",
    "c",
  }
}

func someOtherFunction(someString string, someInt int) string {
  return "hi"
}
func someOtherFunction(someString string, someInt int) (string, int) {
  return "hi", 5
}
```

## Types

* string - 0-value is ""
* int - 0-value is 0
* bool - 0-value is false
* rune - A single character that's represented by its character code
* float64
* array - all same type, can't change size, elements are initialized to zero-value for type
* slice - all same type, can change size

Prefixing with * references a pointer of that type.

### Casting

Call the type like a function:

```go
string(someNumber)
```

## CLI

* `go run file-name.go`
* `go build file-name.go`
* `go fmt file-name.go` - Applies built-in formatting
* `go install somepackage` - Finds the package in ~/go/src/somepackage, compiles it to ~/go/bin/somepackage
* `go get github.com/kylecoberly/somepackage` - Installs in `~/go/src/github.com/kylecoberly/somepackage` directory
* `go doc packagename` - Get documentation
  * `go doc packagename SomePublicMethod`
* `godoc -http=:6060` - Serve HTML docs on port 6060 - Includes your packages!

## Conventions

* camelCasing
* A public method that's runnable outside a package starts with a Capital letter

## Packages

## Folder structure

Default location is `~/go`, change with `GOPATH` environment variable

```
~
  |- go
    |- bin // executable programs
    |- pkg // compiled package code
    |- src // package source code
      |- somepackage
        |- somepackage.go
      |- otherpackage
        |- otherpackage.go
        |- nestedpackage
          |- nestedpackage.go
      |- github.com // domain the package came from
        |- kylecoberly // username
          |- packagename
            |- packagename.go
```
