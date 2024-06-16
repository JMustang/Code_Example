# Pointers

- Go suporta ponteiros, permitindo que você passe referências a valores e registros dentro do seu programa.

```go
package main

import "fmt"

/*
    Vamos mostrar como os ponteiros
    funcionam em contraste com valores usando 2 funções:
    zeroval e zeroptr. zeroval tem um parâmetro int,
    então os argumentos serão passados para ela por valor.
    zeroval receberá uma cópia de ival
    distinta daquela na função chamadora.
*/
func zeroval(ival int) {
    ival = 0
}

/*
    zeroptr, em contraste, tem um parâmetro *int,
    o que significa que aceita um ponteiro para int.
    O código *iptr no corpo da função então
    desreferencia o ponteiro de seu endereço de memória
    para o valor atual nesse endereço.
    Atribuir um valor a um ponteiro
    desreferenciado muda o valor
    no endereço referenciado.
*/
func zeroptr(iptr *int) {
    *iptr = 0
}

func main() {
    i := 1
    fmt.Println("initial:", i)

    zeroval(i)
    fmt.Println("zeroval:", i)

    // A sintaxe &i dá o endereço de memória de i, ou seja, um ponteiro para i.
    zeroptr(&i)
    fmt.Println("zeroptr:", i)

    // Os ponteiros também podem ser impressos.
    fmt.Println("pointer:", &i)
}
```

- zeroval não muda o i em main, mas zeroptr muda porque tem uma referência ao endereço de memória dessa variável.

```bash
# SAIDA
$ go run pointers.go
# initial: 1
# zeroval: 1
# zeroptr: 0
# pointer: 0x42131100
```
