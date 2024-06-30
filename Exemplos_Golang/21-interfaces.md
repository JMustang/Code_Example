# Interfaces

- Interfaces são coleções nomeadas de assinaturas de métodos.

```go
package main

import (
    "fmt"
    "math"
)

// Aqui está uma interface básica para formas geométricas.
type geometry interface {
    area() float64
    perim() float64
}

// Para nosso exemplo,
// implementaremos esta interface nos tipos rect e circle.
type rect struct {
    width, height float64
}
type circle struct {
    radius float64
}

/*
    Para implementar uma interface em Go,
    precisamos apenas implementar todos os métodos da interface.
    Aqui, implementamos geometry em rects.
*/
func (r rect) area() float64 {
    return r.width * r.height
}
func (r rect) perim() float64 {
    return 2*r.width + 2*r.height
}

// A implementação para circles.
func (c circle) area() float64 {
    return math.Pi * c.radius * c.radius
}
func (c circle) perim() float64 {
    return 2 * math.Pi * c.radius
}


/*
    Se uma variável tem um tipo de interface,
    então podemos chamar métodos que estão na interface nomeada.
    Aqui está uma função measure genérica
    aproveitando isso para funcionar com qualquer geometria.
*/
func measure(g geometry) {
    fmt.Println(g)
    fmt.Println(g.area())
    fmt.Println(g.perim())
}

func main() {
    r := rect{width: 3, height: 4}
    c := circle{radius: 5}

    /*
        Os tipos de struct circle e rect ambos
        implementam a interface geometry,
        então podemos usar instâncias desses
        structs como argumentos para measure.
    */
    measure(r)
    measure(c)
}
```

```bash
# SAIDA
$ go run interfaces.go
# {3 4}
# 12
# 14
# {5}
# 78.53981633974483
# 31.41592653589793
```

Para aprender mais sobre as interfaces de Go, confira este excelente [post](https://jordanorelli.com/post/32665860244/how-to-use-interfaces-in-go) no blog.
