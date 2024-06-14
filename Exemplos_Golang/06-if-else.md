# If/Else

- Ramificar com if e else em Go é simples.

```go
package main

import "fmt"

func main() {

    // Aqui está um exemplo básico.
    if 7%2 == 0 {
        fmt.Println("7 is even")
    } else {
        fmt.Println("7 is odd")
    }

    // Você pode ter uma instrução if sem else.
    if 8%4 == 0 {
        fmt.Println("8 is divisible by 4")
    }

    /*
        Uma instrução pode preceder condicionais;
        quaisquer variáveis declaradas nesta instrução
        estão disponíveis na ramificação atual e em todas as ramificações subsequentes.
    */
    if num := 9; num < 0 {
        fmt.Println(num, "is negative")
    } else if num < 10 {
        fmt.Println(num, "has 1 digit")
    } else {
        fmt.Println(num, "has multiple digits")
    }
}
```

- Veja que você não precisa de parênteses em torno das condições no Go,
  mas os colchetes são obrigatórios.

```bash
# SAIDA
$ go run if-else.go
# 7 is odd
# 8 is divisible by 4
# either 8 or 7 are even
# 9 has 1 digit
```

- Não há if ternário em Go,
  então você precisará usar uma instrução if completa,
  mesmo para condições básicas.
