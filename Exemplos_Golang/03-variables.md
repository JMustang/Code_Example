# Variaveis

- Em Go, as variáveis são explicitamente declaradas e usadas pelo compilador,
por exemplo. verifique a correção do tipo das chamadas de função.

```go
package main

import "fmt"


func main() {

    // var declara uma ou mais variáveis.
    var a = "pagode"
    fmt.Println(a)

    // Você pode declarar múltiplas variáveis de uma só vez.
    var b, c int = 1, 2
    fmt.Println(b, c)

    // Go irá inferir o tipo de variáveis inicializadas.
    var d = true
    fmt.Println(d)

    // Variáveis declaradas sem uma inicialização correspondente têm valor zero.
    // Por exemplo, o valor zero para um int é 0.
    var e int
    fmt.Println(e)

    // A sintaxe ":=" é uma abreviação para declarar e inicializar uma variável,
    // por ex. para var f string = "apple" neste caso.
    // Esta sintaxe está disponível apenas dentro de funções.
    f := "apple"
    fmt.Println(f)
}
```

```bash
# SAIDA
$ go run variables.go
# initial
# 1 2
# true
# 0
# apple
```
