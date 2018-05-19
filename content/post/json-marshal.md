+++
title = "json.Marshal"
description = "Dicas de como usar json.Marshal para converter structs para JSON"
tags = ["Golang","dica"]
date = "2018-05-18T06:45:14Z"
+++

{{< youtube FoHEIqTkksw >}}

# Algumas dicas rápidas para usar `json.Marshal`

- Os campos da struct que você quer fazer marshal precisam ser declarados com a primeira letra maiúscula ou seja precisam ser `public`, caso contrario a função `Marshal` não consegue encontrar os campos.
- O retorno de `json.Marshal` é um array de bytes, para converter para string basta fazer cast usando `string(nomeDoVetor)`.
- É uma boa pratica usar os nomes dos campos quando for popular a struct.

## Veja o exemplo

```go
package main

import (
	"encoding/json"
	"fmt"
)

type Bla struct {
	Nome  string
	Idade int
}

func main() {
	jess := Bla{
		Nome:  "temps",
		Idade: 22,
	}
	ret, err := json.Marshal(jess)
	if err != nil {
		fmt.Println("errroouuu")
	}
	fmt.Println(string(ret))
}
```

[Você pode testar esse exemplo no Go Playground](https://play.golang.org/p/C3jLqXxjYiN)

# Links úteis

- [Blog da Jessica Temporal](http://jtemporal.com/) onde você pode encontrar mais exemplos e posts interessantes.
- [Repositório do nosso grupo](https://github.com/go-br/estudos)
- [E você encontra mais exemplos aqui](https://github.com/go-br)
