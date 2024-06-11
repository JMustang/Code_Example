# Slices

- Slices são um tipo de dado importante em Go,
oferecendo uma interface mais poderosa para sequências do que arrays.

```go
package main

import (
    "fmt"
    "slices"
)

func main() {

    /* Diferente dos arrays,
       slices são tipados apenas pelos elementos que contêm (não pelo número de elementos).
       Um slice não inicializado é igual a nil e tem comprimento 0.*/
    var s []string
    fmt.Println("uninit:", s, s == nil, len(s) == 0)


    /* Para criar um slice vazio com comprimento diferente de zero,
       use a função embutida make. Aqui,
       criamos um slice de strings com comprimento 3 (inicialmente com valores zero).
       Por padrão,
       a capacidade de um novo slice é igual ao seu comprimento;
       se soubermos que o slice vai crescer antecipadamente,
       é possível passar uma capacidade explicitamente como um parâmetro adicional para make.*/
    s = make([]string, 3)
    fmt.Println("emp:", s, "len:", len(s), "cap:", cap(s))

    // Podemos definir e obter exatamente como acontece com os arrays.
    s[0] = "a"
    s[1] = "b"
    s[2] = "c"
    fmt.Println("set:", s)
    fmt.Println("get:", s[2])

    // len retorna o comprimento do slice conforme o esperado.
    fmt.Println("len:", len(s))

    /*
      Além dessas operações básicas,
      slices suportam várias outras que os tornam mais ricos do que arrays.
      Uma delas é a função embutida append,
      que retorna um slice contendo um ou mais novos valores.
      Note que precisamos aceitar um valor de retorno de append,
      pois podemos obter um novo valor de slice.
    */
    s = append(s, "d")
    s = append(s, "e", "f")
    fmt.Println("apd:", s)

    /* Slices também podem ser copiados. Aqui,
       criamos um slice vazio c com o mesmo comprimento de s e copiamos de s para c.
    */
    c := make([]string, len(s))
    copy(c, s)
    fmt.Println("cpy:", c)

    /*
      Slices suportam um operador de 'slice' com a sintaxe slice[low].
      Por exemplo, isso obtém um slice dos elementos s[2], s[3] e s[4].  
    */
    l := s[2:5]
    fmt.Println("sl1:", l)

    // Isso faz um slice até (mas excluindo) s[5].
    l = s[:5]
    fmt.Println("sl2:", l)

    // E isso faz um slice a partir de (e incluindo) s[2].
    l = s[2:]
    fmt.Println("sl3:", l)

    // Podemos declarar e inicializar uma variável para um slice em uma única linha também.
    t := []string{"g", "h", "i"}
    fmt.Println("dcl:", t)

    // O pacote slices contém várias funções utilitárias úteis para slices.
    t2 := []string{"g", "h", "i"}
    if slices.Equal(t, t2) {
        fmt.Println("t == t2")
    }

    /*
      Slices podem ser compostos em estruturas de dados multi-dimensionais.
      O comprimento dos slices internos pode variar,
      ao contrário dos arrays multi-dimensionais.
    */
    twoD := make([][]int, 3)
    for i := 0; i < 3; i++ {
        innerLen := i + 1
        twoD[i] = make([]int, innerLen)
        for j := 0; j < innerLen; j++ {
            twoD[i][j] = i + j
        }
    }
    fmt.Println("2d: ", twoD)
}
```

- Note que, embora slices sejam tipos diferentes de arrays,
  eles são renderizados de forma similar pelo fmt.Println.

```bash
  $ go run slices.go
  # uninit: [] true true
  # emp: [  ] len: 3 cap: 3
  # set: [a b c]
  # get: c
  # len: 3
  # apd: [a b c d e f]
  # cpy: [a b c d e f]
  # sl1: [c d e]
  # sl2: [a b c d e]
  # sl3: [c d e f]
  # dcl: [g h i]
  # t == t2
  # 2d:  [[0] [1 2] [2 3 4]]
```

- Dê uma olhada neste excelente [https://go.dev/blog/slices-intro](post)
no blog feito pela equipe do Go para mais detalhes sobre o design e implementação de slices em Go.

Agora que vimos arrays e slices, vamos dar uma olhada na outra estrutura de dados embutida do Go: maps.
