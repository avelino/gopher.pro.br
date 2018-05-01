+++
title = "interface"
date = "2016-11-11T17:00:21-05:00"
description = "A `interface` básicamente é como se fosse um contrato as para funções que o recebem."
tags = ["Golang"]
+++
# interface

A `interface` básicamente é como se fosse um contrato as para funções que o recebem.

Para implementar uma `interface` primeiro precisamos declarar-la:

```go

type Ser interface {
    Respirar() bool
}

```

Criando nossos tipos:

```go

type (
    Humano struct {}
    Cachorro struct {}
    Pedra struct {}
)

func (h Humano) Respirar() bool {
    return false
}

func (c Cachorro) Respirar() bool {
    return true
}

```

Agora criaremos uma função onde somente os `Seres vivos` podem recebidos:

```go

func VerificandoSeEstaVivo(s Ser) {
    if s.Respirar() {
        fmt.Println("Está vivo.")
    } else {
        fmt.Println("Não está vivo.")
    }
}

```

Agora vamos verificar nossos tipos:

```go

humano := Humano{}
cachorro := Cachorro{}
pedra := Pedra{}

VerificandoSeEstaVivo(humano) // Não está vivo.
VerificandoSeEstaVivo(cachorro) // Está vivo.
VerificandoSeEstaVivo(pedra) // erro: O tipo Pedra não é um Ser

```
[Playground](https://play.golang.org/p/VdEZ7M8wEi)

## Arquivos desse post:

- [interface/README.md](https://github.com/go-br/estudos/blob/master/interface/README.md)
- [interface/interface.go](https://github.com/go-br/estudos/blob/master/interface/interface.go)
