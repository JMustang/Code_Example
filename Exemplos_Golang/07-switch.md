# Switch case

- As instruções switch expressam condicionais em muitas ramificações.

```go
package main

import (
    "fmt"
    "time"
)

func main() {

    // Aqui está uma exemplo básica de **"Switch"**.
    i := 2
    fmt.Print("Write ", i, " as ")
    switch i {
    case 1:
        fmt.Println("one")
    case 2:
        fmt.Println("two")
    case 3:
        fmt.Println("three")
    }

    /*
        Você pode usar vírgulas para separar múltiplas expressões na mesma instrução
        "case".
        Também usamos o **"case"** padrão opcional neste exemplo.
    */
    switch time.Now().Weekday() {
    case time.Saturday, time.Sunday:
        fmt.Println("It's the weekend")
    default:
        fmt.Println("It's a weekday")
    }

    /*
        "switch" sem uma expressão é uma maneira alternativa de expressar a lógica
        "if/else".
        Aqui também mostramos como as expressões **"case"** podem ser não constantes.
    */
    t := time.Now()
    switch {
    case t.Hour() < 12:
        fmt.Println("It's before noon")
    default:
        fmt.Println("It's after noon")
    }

    /*
        Um tipo "Switch" compara tipos em vez de valores.
        Você pode usar isso para descobrir o tipo de um valor de interface. Neste exemplo,
        a variável t terá o tipo correspondente à sua cláusula.
    */
    whatAmI := func(i interface{}) {
        switch t := i.(type) {
        case bool:
            fmt.Println("I'm a bool")
        case int:
            fmt.Println("I'm an int")
        default:
            fmt.Printf("Don't know type %T\n", t)
        }
    }
    whatAmI(true)
    whatAmI(1)
    whatAmI("hey")
}
```

```bash
# SAIDA
$ go run switch.go
# Write 2 as two
# It's a weekday
# It's after noon
# I'm a bool
# I'm an int
# Don't know type string
```
