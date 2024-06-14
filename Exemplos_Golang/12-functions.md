# Functions

- Funções são centrais em Go.
Vamos aprender sobre funções com alguns exemplos diferentes.

```go
package main

import "fmt"

/*
  Aqui está uma função que recebe dois ints e retorna a soma deles como um int.
  Go requer retornos explícitos, ou seja,
  não retornará automaticamente o valor da última expressão.
*/
func plus(a int, b int) int {

    return a + b
}

/*
  Quando você tem múltiplos parâmetros consecutivos do mesmo tipo,
  pode omitir o nome do tipo para os parâmetros de mesmo tipo
  até o último parâmetro que declara o tipo.
*/
func plusPlus(a, b, c int) int {
    return a + b + c
}

// Chame uma função exatamente como você esperaria, com name(args).
func main() {

    res := plus(1, 2)
    fmt.Println("1+2 =", res)

    res = plusPlus(1, 2, 3)
    fmt.Println("1+2+3 =", res)
}
```

```bash
# SAIDA
$ go run functions.go 
# 1+2 = 3
# 1+2+3 = 6
```

- Há várias outras características das funções em Go.
Uma delas é múltiplos valores de retorno,
que veremos a seguir.
