# Recursion

- Go suporta funções recursivas. Aqui está um exemplo clássico.

```go
package main

import "fmt"

// Esta função fact chama a si mesma até alcançar o caso base de fact(0).
func fact(n int) int {
    if n == 0 {
        return 1
    }
    return n * fact(n-1)
}

func main() {
    fmt.Println(fact(7))

    /*
        Closures também podem ser recursivos,
        mas isso requer que o closure seja
        declarado com uma var tipada
        explicitamente antes de ser definido.
    */
    var fib func(n int) int

    fib = func(n int) int {
        if n < 2 {
            return n
        }

        /*
            Como fib foi declarado anteriormente em main,
            Go sabe
            qual função chamar com fib aqui.
        */
        return fib(n-1) + fib(n-2)
    }

    fmt.Println(fib(7))
}
```

```bash
# SAIDA
$ go run recursion.go
# 5040
# 13
```
