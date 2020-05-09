## Overview

* Throws compile-time errors for linting issues
* Has a standardized format
* Uses block scope
* Built-ins can be shadowed
* Pass by value, pass by reference with a pointer

## Examples

```go
package main // has to start with the package name, has to be `main` to be called directly

imports (
  "fmt" // Prints strings
  "math/random" // `math/random` is the import path, `random` is the package name
  "log"
  "math"
  "strings"
  "reflect"
  "time"
  "bufio"
  "os"
  "errors"
)

func main(){
  var message string
  message = "How are you?"
  // or
  message := "How are you?"
  // or
  thing1, thing2 := 1.2, 3.4

  fmt.Println("Hi!", message) // joins them with spaces

  reflect.TypeOf(42)

  now := time.Now()
  year := now.Year()
  unix := now.Unix()

  rand.Seed(unix)
  someRandomNumber := rand.Intn(100) + 1 // makes it 1-100

  replacer := strings.NewReplacer("#", "o") // `strings` is the value, `NewReplacer` is the method
  fixed := replacer.Replace("G# r#cks!")

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

  stringThatCanConvertToNumber := strings.TrimSpace(input) // Gets rid of newlines
  someFloat := strconv.ParseFloat(stringThatCanConvertToNumber)
  someInt := strconv.Atoi(stringThatCanConvertToNumber)

  for i := 0; i < someNumber; i++ {
    // Something
    continue
  }
  for i < someNumber {
    // Something
    break
  }

  fmt.Printf("The %s cost %d cents.\n", "gum", 23)
  /*
    * %f float, %d int
      * Set the "width" with %5f, rounds and adds padding
      * Float display precision: %2.4f
    * %s string, %t boolean
    * %v value (infer the type), %#v print whitespace etc. as encoded
    * %% literal percent
  */

  err := errors.New("Oof")
  err = fmt.Errorf("This is an error %s", "message")
  err.Error() // Returns the error message, will be called automatically by loggers etc.

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

## Conventions

* camelCasing
* A public method that's runnable outside a package starts with a Capital letter
