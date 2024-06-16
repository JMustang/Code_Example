# Closures

- Go suporta funções anônimas,
  que podem formar closures.
  Funções anônimas são úteis quando
  você quer definir uma função
  inline sem ter que nomeá-la.

```go
package main

import "fmt"

/*
    Esta função intSeq retorna outra função,
    que definimos anonimamente no corpo de intSeq.
    A função retornada envolve a variável i para
    formar um closure.
*/
func intSeq() func() int {
    i := 0
    return func() int {
        i++
        return i
    }
}

func main() {

    /*
        Chamamos intSeq,
        atribuindo o resultado (uma função) a nextInt.
        Este valor de função captura seu próprio valor de i,
        que será atualizado cada vez que chamarmos nextInt.
    */
    nextInt := intSeq()

    /*
        Veja o efeito do closure
        chamando nextInt algumas vezes.
    */
    fmt.Println(nextInt())
    fmt.Println(nextInt())
    fmt.Println(nextInt())

    /*
        Para confirmar que o estado é exclusivo
        para aquela função específica,
        crie e teste uma nova.
    */
    newInts := intSeq()
    fmt.Println(newInts())
}
```

```bash
# SAIDA
$ go run closures.go
# 1
# 2
# 3
# 1
```

- A última característica das funções que veremos por agora é a recursão.
