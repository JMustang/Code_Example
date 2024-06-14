# Multiple Return Values

- Go tem suporte embutido para múltiplos valores de retorno. Essa característica é frequentemente usada no Go idiomático, por exemplo, para retornar tanto o resultado quanto os valores de erro de uma função.

```go
package main

import "fmt"

/*
    O (int, int) nesta assinatura de função
    mostra que a função retorna 2 ints.
*/
func vals() (int, int) {
    return 3, 7
}

func main() {

    /*
        Aqui usamos os 2 diferentes valores de retorno
        da chamada com múltipla atribuição.
    */
    a, b := vals()
    fmt.Println(a)
    fmt.Println(b)


    /*
        Se você quiser apenas um subconjunto dos valores retornados,
        use o identificador em branco _.
    */
    _, c := vals()
    fmt.Println(c)
}
```

```bash
# SAIDA
$ go run multiple-return-values.go
# 3
# 7
# 7
```

- Aceitar um número variável de argumentos é outra característica interessante das funções em Go; vamos ver isso a seguir.
