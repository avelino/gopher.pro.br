+++
title = "select"
date = "2016-11-11T17:00:21-05:00"
description = "Select trabalha junto com canais para esperar retornos de canais específicos."
tags = ["Golang"]
+++

# select

Select trabalha junto com canais para esperar retornos de canais específicos.

```go
select {
case msg1 := <-c1:
    fmt.Println("canal 1 retornou :", msg1)
case msg2 := <-c2:
    fmt.Println("canal 2 retornou :", msg2)
}
```
[Playground](https://play.golang.org/p/C2RkmGcZBX)

## Arquivos desse post:

- [select/README.md](https://github.com/go-br/estudos/blob/master/select/README.md)
- [select/select.go](https://github.com/go-br/estudos/blob/master/select/select.go)
