# Structs

- Os **structs** de Go são coleções tipadas de campos.
  Eles são úteis para agrupar dados para formar registros.

```go
package main

import "fmt"

/*
    Este tipo de struct person tem campos name e age.
*/
type person struct {
    name string
    age  int
}

/*
    newPerson constrói um novo struct person.
*/
func newPerson(name string) *person {

    /*
        Você pode retornar de forma segura um ponteiro para uma variável local,
        pois a variável local sobreviverá ao escopo da função.
    */
    p := person{name: name}
    p.age = 42
    return &p
}

func main() {

    // Esta sintaxe cria um novo struct.
    fmt.Println(person{"Bob", 20})

    // Você pode nomear os campos ao inicializar um struct.
    fmt.Println(person{name: "Alice", age: 30})

    // Campos omitidos terão valor zero.
    fmt.Println(person{name: "Fred"})

    // Um prefixo & produz um ponteiro para o struct.
    fmt.Println(&person{name: "Ann", age: 40})

    // É idiomático encapsular a criação de um novo struct em funções construtoras.
    fmt.Println(newPerson("Jon"))

    // Acesse os campos do struct com um ponto.
    s := person{name: "Sean", age: 50}
    fmt.Println(s.name)

    /*
        Você também pode usar pontos com ponteiros de struct
        - os ponteiros são automaticamente desreferenciados.
    */
    sp := &s
    fmt.Println(sp.age)

    // Structs são mutáveis.
    sp.age = 51
    fmt.Println(sp.age)

    /*
        Se um tipo de struct é usado apenas para um único valor,
        não precisamos dar um nome a ele.
        O valor pode ter um tipo de struct anônimo.
        Essa técnica é comumente usada para testes orientados por tabela.
    */
    dog := struct {
        name   string
        isGood bool
    }{
        "Rex",
        true,
    }
    fmt.Println(dog)
}
```

```bash
# SAIDA
$ go run structs.go
# {Bob 20}
# {Alice 30}
# {Fred 0}
# &{Ann 40}
# &{Jon 42}
# Sean
# 50
# 51
# {Rex true}
```
