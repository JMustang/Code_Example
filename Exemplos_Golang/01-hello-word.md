# Hello World

Nosso primeiro programa irá imprimir a clássica mensagem **“hello world”**.
Aqui está o código fonte completo.

```go
package main
import "fmt"
func main() {
    fmt.Println("hello world")
}
```

Para executar o programa, coloque o código em **hello-world.go** e use go run.

```bash
# SAIDA
$ go run hello-world.go
# hello world
```

Às vezes, vamos querer construir nossos programas em binários.

```bash
# SAIDA
$ go build hello-world.go
$ ls
# hello-world    hello-world.go
```

Podemos fazer isso usando go build. Em seguida, podemos executar o binário construído diretamente.

```bash
# SAIDA
$ ./hello-world
# hello world
```

Agora que podemos executar e construir programas básicos em Go,
vamos aprender mais sobre a linguagem.
