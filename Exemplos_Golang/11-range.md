# Range

- Range itera sobre elementos em uma variedade de estruturas de dados.
  Vamos ver como usar range com algumas das estruturas de dados que já aprendemos.

```go
package main

import "fmt"

func main() {

    // Aqui usamos range para somar os números em um slice. Arrays funcionam assim também.
    nums := []int{2, 3, 4}
    sum := 0
    for _, num := range nums {
        sum += num
    }
    fmt.Println("sum:", sum)

    /*
        range em arrays e slices fornece tanto o índice quanto o valor para cada entrada.
        Acima, não precisávamos do índice, então o ignoramos com o identificador em branco _. Às vezes,
        realmente queremos os índices, no entanto.
     */
    for i, num := range nums {
        if num == 3 {
            fmt.Println("index:", i)
        }
    }

    // range em map itera sobre pares chave/valor.
    kvs := map[string]string{"a": "apple", "b": "banana"}
    for k, v := range kvs {
        fmt.Printf("%s -> %s\n", k, v)
    }

    // range também pode iterar apenas nas chaves de um mapa.
    for k := range kvs {
        fmt.Println("key:", k)
    }

    /*
      range em strings itera sobre pontos de código Unicode.
      O primeiro valor é o índice do byte inicial da rune e o segundo é a própria rune.
      Veja Strings e Runes para mais detalhes.
    */
    for i, c := range "go" {
        fmt.Println(i, c)
    }
}
```

```bash
# SAIDA
$ go run range.go
# sum: 9
# index: 1
# a -> apple
# b -> banana
# key: a
# key: b
# 0 103
# 1 111
```
