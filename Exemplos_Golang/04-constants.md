# Constants

- Go oferece suporte a constantes de caracteres,
strings, valores booleanos e numéricos.


```go
package main

import (
    "fmt"
    "math"
)

// A palavra chave "const", declara um valor constante.
const s string = "constant"

func main() {	

    fmt.Println(s)
    
    // Uma instrução "const" pode aparecer em qualquer lugar que uma instrução "var" possa.

    const n = 50000000

    // Expressões constantes executam aritmética com precisão arbitrária.
    const d = 3e20 / n
    fmt.Println(d)

    // Uma constante numérica não tem tipo até receber um,
    // como por meio de uma conversão explícita.
    fmt.Println(int64(d))

    // Um número pode receber um tipo usando-o em um contexto que o exija,
    // como uma atribuição de variável ou chamada de função.
    // Por exemplo, aqui math.Sin espera um float64.
    fmt.Println(math.Sin(n))
}

```

```bash
$ go run constant.go
# constant
# 6e+11
# 600000000000
# -0.28470407323754404
```
