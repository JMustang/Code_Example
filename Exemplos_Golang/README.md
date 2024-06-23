# Exemplos Golang

## Essa é uma versão pt-br do [Go by example](https://gobyexample.com/)

---

**O Básico**

**Go** é uma linguagem de programação compilada e estaticamente tipada. **Go** é sintaticamente similar ao **C**. A linguagem é frequentemente referida como **Golang** devido ao seu antigo nome de domínio, **golang.org**, mas o nome correto é **Go**.

O conceito de Básico introduzirá três características principais da linguagem:
**Pacotes**,
**Funções**,
**Variáveis**.

---

**Pacotes**

Aplicações **Go** são organizadas em pacotes. Um pacote é uma coleção de arquivos-fonte localizados no mesmo diretório. Todos os arquivos-fonte em um diretório devem compartilhar o mesmo nome de pacote. É convencional que o nome do pacote seja o último diretório no caminho de importação. Por exemplo, os arquivos no pacote **"math/rand"** começam com a declaração **package rand**. Quando um pacote é importado, apenas as entidades (funções, tipos, variáveis, constantes) cujos nomes começam com letra maiúscula podem ser usadas/acessadas. O estilo recomendado de nomenclatura em **Go** é que identificadores sejam nomeados usando **camelCase**, exceto aqueles destinados a serem acessíveis entre pacotes, que devem ser **PascalCase**.

```go
package math
```

---

**Variáveis**

**Go** é estaticamente tipada, o que significa que todas as variáveis devem ter um tipo definido em tempo de compilação.

Variáveis podem ser definidas especificando explicitamente um tipo:

```go
var num1 int // tipo explicito
```

Você também pode usar um inicializador, e o compilador atribuirá o tipo da variável para corresponder ao tipo do inicializador.

```go
var num1 := 10 // tipo int, implícito
```

Uma vez declaradas, as variáveis podem ser atribuídas valores usando o operador =. Uma vez declarada, o tipo de uma variável nunca pode mudar.

```go
num1 := 1 // Atribuir valor inicial
num1 = 2 // Atualizar para novo valor
num1 = false // Isso gera um erro do compilador devido à atribuição de um tipo não `int`
```

---

**Constantes**

Constantes mantêm um pedaço de dado assim como variáveis, mas seu valor não pode mudar durante a execução do programa.

Constantes são definidas usando a palavra-chave **const** e podem ser **números**, **caracteres**, **strings** ou **booleanos**:

```go
const Idade = 22 // Define uma constante numérica 'Idade' com o valor 21
```

---

**Funções**

Funções em **Go** aceitam zero ou mais parâmetros. Os parâmetros devem ser explicitamente tipados, não há inferência de tipo.

Valores são retornados das funções usando a palavra-chave **return**.

Uma função é invocada especificando o nome da função e passando argumentos para cada um dos parâmetros da função.

Note que **Go** suporta dois tipos de comentários. Comentários de uma linha são precedidos por **//** e comentários de múltiplas linhas são inseridos entre **/\*** e **\*/**.

```go
package ola

// "Ola" é uma função publica devido ao "O" maiúsculo
func Ola(nome string) string {
    return oi(nome)
}

// "oi" é uma função privada devido ao "o" minusculo
func oi(nome string) string {
    return "Oi "+nome
}
```
