+++
title = "Pacotes"
date = "2016-11-11T17:00:21-05:00"
description = "Go é organizada em pacotes, os nomes dos pacotes fornecem um contexto e um espaço de nomes."
tags = ["Golang"]
+++
# Pacotes

Go é organizada em pacotes, os nomes dos pacotes fornecem um contexto e um espaço de nomes.

```go
import (
	"fmt"
)
```

O pacote rotateString criado para exemplificar vários conceitos.
https://github.com/crgimenes/rotateString


```go
go get github.com/crgimenes/rotateString
```

Referencia completa ao pacote direto no código.

```go
import (
	"fmt"
	r "github.com/crgimenes/rotateString"
)
```


Atualizar o pacote

```bash
go get -u github.com/crgimenes/rotateString
```

Exemplo de uso do pacote rotateString

```go
package main

import (
	"fmt"
	r "github.com/crgimenes/rotateString"
)

func main() {
	s := r.Rotate("Isto é um teste de Rotate")
	fmt.Printf("rotate: %s\r\n", s)
}
```

## Arquivos desse post:

- [package/README.md](https://github.com/go-br/estudos/blob/master/package/README.md)
- [package/package.go](https://github.com/go-br/estudos/blob/master/package/package.go)
