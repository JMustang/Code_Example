# Maps

- **"Maps"** são tipos de dados associativos integrados ao Go
(às vezes chamados de hashes ou dicts em outras linguagens).

```go
package main

import (
    "fmt"
    "maps"
)

func main() {

    // Para criar um mapa vazio, use a função embutida make: make(map[tipo-chave]tipo-valor).
    m := make(map[string]int)

    // Defina pares chave/valor usando a sintaxe típica nome[chave] = valor
    m["k1"] = 7
    m["k2"] = 13

    // Imprimir um mapa com, por exemplo, fmt.Println, mostrará todos os seus pares chave/valor.
    fmt.Println("map:", m)

    // Obtenha um valor para uma chave com nome[chave].
    v1 := m["k1"]
    fmt.Println("v1:", v1)

    // Se a chave não existir, o valor zero do tipo de valor é retornado.
    v3 := m["k3"]
    fmt.Println("v3:", v3)

    // A função embutida len retorna o número de pares chave/valor quando chamada em um mapa.
    fmt.Println("len:", len(m))

    // A função embutida delete remove pares chave/valor de um mapa.
    delete(m, "k2")
    fmt.Println("map:", m)

    // Para remover todos os pares chave/valor de um mapa, use a função embutida clear.
    clear(m)
    fmt.Println("map:", m)

    /*
      O segundo valor de retorno opcional ao obter um valor de um mapa indica se a chave estava presente no mapa.
      Isso pode ser usado para distinguir entre chaves ausentes e chaves com valores zero,
      como 0 ou ''. Aqui, não precisávamos do valor em si,
      então o ignoramos com o identificador em branco _.
    */
    _, prs := m["k2"]
    fmt.Println("prs:", prs)

    // Você também pode declarar e inicializar um novo mapa na mesma linha com esta sintaxe.
    n := map[string]int{"foo": 1, "bar": 2}
    fmt.Println("map:", n)

    // O pacote maps contém várias funções utilitárias úteis para mapas.
    n2 := map[string]int{"foo": 1, "bar": 2}
    if maps.Equal(n, n2) {
        fmt.Println("n == n2")
    }
}
```

- Note que mapas aparecem na forma map[k:v k:v]
quando impressos com fmt.Println.

```bash
# SAIDA
$ go run maps.go 
# map: map[k1:7 k2:13]
# v1: 7
# v3: 0
# len: 2
# map: map[k1:7]
# map: map[]
# prs: false
# map: map[bar:2 foo:1]
# n == n2
```
