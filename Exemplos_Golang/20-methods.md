# Methods

- Go suporta métodos definidos em tipos de struct.

```go
package main

import "fmt"

type rect struct {
    width, height int
}

// Este método area tem um tipo receptor de *rect.
func (r *rect) area() int {
    return r.width * r.height
}

/*
    Métodos podem ser definidos tanto para tipos de receptor ponteiro quanto valor.
    Aqui está um exemplo de um receptor de valor.
*/
func (r rect) perim() int {
    return 2*r.width + 2*r.height
}

func main() {
    r := rect{width: 10, height: 5}

    //Aqui chamamos os 2 métodos definidos para o nosso struct.
    fmt.Println("area: ", r.area())
    fmt.Println("perim:", r.perim())


/*
    Go lida automaticamente com a conversão entre valores e ponteiros para chamadas de método.
    Você pode querer usar um tipo receptor ponteiro para evitar
    cópias nas chamadas de método ou para permitir
    que o método mude o struct receptor.
*/
    rp := &r
    fmt.Println("area: ", rp.area())
    fmt.Println("perim:", rp.perim())
}
```

```bash
# SAIDA
$ go run methods.go
# area:  50
# perim: 30
# area:  50
# perim: 30
```
