# Loop for

- For é a única construção de loop do Go.
  Aqui estão alguns tipos básicos de loops for.

```go
package main

import "fmt"

func main() {

    // O tipo mais básico, com uma única condição.
    i := 1
    for i <= 3 {
        fmt.Println(i)
        i = i + 1
    }

    // Um loop "for" classico inicial/condição/depois do loop.
    for j := 0; j < 3; j++ {
        fmt.Println(j)
    }

    /*
         Outra maneira de realizar a iteração básica
        “faça isso N vezes” é o intervalo em um número inteiro.
    */
    for i := range 3 {
        fmt.Println("range", i)
    }

    /*
        "for" sem uma condição,
         fará um loop repetidamente até você sair do loop ou retornar da função envolvente.
    */
    for {
        fmt.Println("loop")
        break
    }


    // Você também pode continuar para a próxima iteração do loop.
    for n := range 6 {
        if n%2 == 0 {
            continue
        }
        fmt.Println(n)
    }
}
```

```bash
# SAIDA

$ go run for.go
# 1
# 2
# 3
# 0
# 1
# 2
# range 0
# range 1
# range 2
# loop
# 1
# 3
# 5
```
