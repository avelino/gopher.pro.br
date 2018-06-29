+++
title = "Usando defer para mudar o valor de retorno"
description = "Hoje usamos o defer para mudar o valor retornado por uma função, Hangout do grupo de estudos de Go 2018-06-28"
tags = ["Golang"]
date = "2018-06-28T06:45:14Z"
+++

{{< youtube TCa82B1pOGk >}}

Hoje mostramos como usar o defer e alterar o valor de retorno de uma função.

```go
package main

import (
	"fmt"
)

func processValue1(s string) (ret int) {
	for _, v := range s {
		if v != '0' {
			ret = (ret + 1) * 4
			return
		}
		ret++
	}
	ret = (ret + 1) * 4
	return
}

func processValue2(s string) (ret int) {
	defer func() { ret = (ret + 1) * 4 }()
	for _, v := range s {
		if v != '0' {
			return
		}
		ret++
	}
	return
}

func main() {
	value := "0000000082"
	c := processValue1(value)
	fmt.Println(c)
	c = processValue2(value)
	fmt.Println(c)
}
```


Links mencionados, alguns foram mencionados fora da gravação:

- [Código fonte de hoje](https://play.golang.org/p/LGj23boK-SO)
- [Repositório do nosso grupo](https://github.com/go-br/estudos)
- [E você encontra mais exemplos aqui](https://github.com/go-br)

Nossos encontros ocorrem todas as quintas-feiras ás 22h00, para participar [entre no canal de Go no slack](https://invite.slack.golangbridge.org/) e procure por #brazil