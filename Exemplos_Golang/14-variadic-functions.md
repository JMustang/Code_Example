# Variadic Functions

-Funções variádicas podem ser chamadas com qualquer número de argumentos adicionais. Por exemplo, fmt.Println é uma função variádica comum.

```go
package main

import "fmt"

/*
    Aqui está uma função que
    aceitará um número arbitrário de
    ints como argumentos.
*/
func sum(nums ...int) {
    fmt.Print(nums, " ")
    total := 0

    /*
        Dentro da função,
        o tipo de nums é equivalente a []int.
        Podemos chamar len(nums),
        iterar sobre ele com range, etc.
    */
    for _, num := range nums {
        total += num
    }
    fmt.Println(total)
}

func main() {

    /*
        Funções variádicas podem ser
        chamadas da maneira usual
        com argumentos individuais.
    */
    sum(1, 2)
    sum(1, 2, 3)

    /*
        Se você já tem vários argumentos em um slice,
        aplique-os a uma função
        variádica usando func(slice...) assim.
    */
    nums := []int{1, 2, 3, 4}
    sum(nums...)
}
```

```bash
# SAIDA
$ go run variadic-functions.go
# [1 2] 3
# [1 2 3] 6
# [1 2 3 4] 10
```

- Outro aspecto chave das funções em Go é sua capacidade de formar closures, que veremos a seguir.
