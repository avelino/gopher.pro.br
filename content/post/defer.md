+++
title = "defer"
date = "2016-11-11T17:00:21-05:00"
description = "A clausula defer define que uma função deve ser chamada no fim da execução da rotina atual. Essa clausula é muito útil para por exemplo fechar arquivos abertos durante a execução da função."
tags = ["Golang"]
+++

# defer

A clausula defer define que uma função deve ser chamada no fim da execução da rotina atual. Essa clausula é muito útil para por exemplo fechar arquivos abertos durante a execução da função.

```go
f, err := os.Open("filename.ext")
if err != nil {
    log.Fatal(err)
}
defer f.Close()

```

Mais um exemplo:

```go
package main

import (
	"fmt"
)

func main() {

	defer func() {
		fmt.Printf("Fim da função main\r\n")
	}()

	for i := 0; i < 5; i++ {
		defer fmt.Printf("%d\r\n", i)
		fmt.Printf("dentro do for %d\r\n", i)
	}
}
```
[Playground](https://play.golang.org/p/phrO0p0sW3)

## Arquivos desse post:

- [defer/README.md](https://github.com/go-br/estudos/blob/master/defer/README.md)
- [defer/defer.go](https://github.com/go-br/estudos/blob/master/defer/defer.go)
