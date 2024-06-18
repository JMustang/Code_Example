# Strings and Runes

- Uma string em Go é um slice de bytes somente leitura.
  A linguagem e a biblioteca padrão
  tratam as strings de forma especial - como contêineres de texto codificado em UTF-8.
  Em outras linguagens, strings são feitas de 'caracteres'.
  Em Go, o conceito de um caractere é chamado de rune - é um inteiro que representa um ponto de código Unicode.
  Este post no blog do Go é uma boa introdução ao tópico.

```go
package main

import (
    "fmt"
    "unicode/utf8"
)

func main() {

    /*
        s é uma string atribuída a um valor literal
        representando a palavra 'hello' na língua tailandesa.
        Literais de string em Go são texto codificado em UTF-8.
    */
    const s = "สวัสดี"

    /*
        Como strings são equivalentes a []byte,
        isso produzirá o comprimento dos bytes brutos armazenados dentro.
    */
    fmt.Println("Len:", len(s))

    /*
        Indexar uma string produz os valores brutos dos bytes em cada índice.
        Este loop gera os valores hexadecimais de
        todos os bytes que constituem os pontos de código em s.
    */
    for i := 0; i < len(s); i++ {
        fmt.Printf("%x ", s[i])
    }
    fmt.Println()

    /*
        Para contar quantas runes há em uma string,
        podemos usar o pacote utf8.
        Note que o tempo de execução de RuneCountInString depende do tamanho da string,
        porque ele precisa decodificar cada rune UTF-8 sequencialmente.
        Alguns caracteres tailandeses são representados
        por pontos de código UTF-8 que podem abranger vários bytes,
        então o resultado dessa contagem pode ser surpreendente.
    */
    fmt.Println("Rune count:", utf8.RuneCountInString(s))

    /*
        Um loop range lida com strings de forma
        especial e decodifica cada rune junto com seu deslocamento na string.
    */
    for idx, runeValue := range s {
        fmt.Printf("%#U starts at %d\n", runeValue, idx)
    }

    /*
        Podemos alcançar a mesma iteração
        usando a função utf8.DecodeRuneInString explicitamente.
    */
    fmt.Println("\nUsing DecodeRuneInString")
    for i, w := 0, 0; i < len(s); i += w {
        runeValue, width := utf8.DecodeRuneInString(s[i:])
        fmt.Printf("%#U starts at %d\n", runeValue, i)
        w = width

        // Isso demonstra passar um valor de rune para uma função.
        examineRune(runeValue)
    }
}

func examineRune(r rune) {

    /*
        Valores entre aspas simples são literais de rune.
        Podemos comparar um valor de rune diretamente com um literal de rune.
    */
    if r == 't' {
        fmt.Println("found tee")
    } else if r == 'ส' {
        fmt.Println("found so sua")
    }
}
```

```bash
# SAIDA
$ go run strings-and-runes.go
# Len: 18
# e0 b8 aa e0 b8 a7 e0 b8 b1 e0 b8 aa e0 b8 94 e0 b8 b5
# Rune count: 6
# U+0E2A 'ส' starts at 0
# U+0E27 'ว' starts at 3
# U+0E31 'ั' starts at 6
# U+0E2A 'ส' starts at 9
# U+0E14 'ด' starts at 12
# U+0E35 'ี' starts at 15
# Using DecodeRuneInString
# U+0E2A 'ส' starts at 0
# found so sua
# U+0E27 'ว' starts at 3
# U+0E31 'ั' starts at 6
# U+0E2A 'ส' starts at 9
# found so sua
# U+0E14 'ด' starts at 12
# U+0E35 'ี' starts at 15
```
