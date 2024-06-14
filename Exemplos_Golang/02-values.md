# Values

- Go tem vários tipos de valores, incluindo strings, integers, floats, booleans, etc.
  Aqui estão alguns exemplos básicos.

```go
package main

import "fmt"


func main() {

    // Strings, que podem ser somadas com +.
    fmt.Println("go" + "lang")

    // Inteiros e flutuantes.
    fmt.Println("1+1 =", 1+1)
    fmt.Println("7.0/3.0 =", 7.0/3.0)

    // Booleanos, com operadores booleanos como seria de esperar.
    fmt.Println(true && false)
    fmt.Println(true || false)
    fmt.Println(!true)
}
```

```bash
# SAIDA
$ go run values.go
# golang
# 1+1 = 2
# 7.0/3.0 = 2.3333333333333335
# false
# true
# false
```
