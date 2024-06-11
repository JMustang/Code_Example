# Arrays

- Em Go, um array é uma sequência numerada de elementos de um comprimento específico.
No código Go típico,
as fatias são muito mais comuns;
matrizes são úteis em alguns cenários especiais.

```go
package main

import "fmt"

func main() {

    /* Aqui criamos um array a que conterá exatamente 5 ints.
      O tipo dos elementos e o comprimento fazem parte do tipo do array.
      Por padrão,
      uma matriz tem valor zero,
      o que para inteiros significa 0s.*/
    var a [5]int
    fmt.Println("emp:", a)

    /* Podemos definir um valor em um índice usando a sintaxe
       array[index] = value e obter um valor com array[index].*/
    a[4] = 100
    fmt.Println("set:", a)
    fmt.Println("get:", a[4])

    // O metodo **"len"**, retorna o comprimento de um array.
    fmt.Println("len:", len(a))

    // Use esta sintaxe para declarar e inicializar um array em uma linha.
    b := [5]int{1, 2, 3, 4, 5}
    fmt.Println("dcl:", b)

    // Você também pode fazer com que o compilador conte o número de elementos para você com **"..."**
    b = [...]int{1, 2, 3, 4, 5}
    fmt.Println("dcl:", b)

    // Se você especificar o índice com **":"**, os elementos intermediários serão zerados.
    b = [...]int{100, 3: 400, 500}
    fmt.Println("idx:", b)

    /* Os tipos de array são unidimensionais,
       mas você pode compor tipos para construir
       estruturas de dados multidimensionais.*/
    var twoD [2][3]int
    for i := 0; i < 2; i++ {
        for j := 0; j < 3; j++ {
            twoD[i][j] = i + j
        }
    }
    fmt.Println("2d: ", twoD)

    // Você também pode criar e inicializar arrays multidimensionais de uma só vez.
    twoD = [2][3]int{
        {1, 2, 3},
        {1, 2, 3},
    }
    fmt.Println("2d: ", twoD)
}
```

- Observe que os arrays aparecem no formato [v1 v2 v3 ...] quando impressas com fmt.Println.

```bash
# SAIDA
$ go run arrays.go
# emp: [0 0 0 0 0]
# set: [0 0 0 0 100]
# get: 100
# len: 5
# dcl: [1 2 3 4 5]
# dcl: [1 2 3 4 5]
# idx: [100 0 0 400 500]
# 2d:  [[0 1 2] [1 2 3]]
# 2d:  [[1 2 3] [1 2 3]]
```
