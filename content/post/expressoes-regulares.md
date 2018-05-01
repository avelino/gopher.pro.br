+++
title = "Expressões Regulares"
date = "2016-11-11T16:32:08-02:00"
description = "Um exemplo simples usando o package regexp para extrair informação de um texto."
tags = ["Golang"]
+++
# Expressões Regulares

Um exemplo simples usando o package regexp para extrair informação de um texto.

```go
package main

import (
	"fmt"
	"regexp"
)

func main() {

	var conteudoHTML = `<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Titulo</title>
</head>

<body>
<img src='imagem1.jpg'>
<img src="imagem2.jpg">
</body>

</html>`

	imagens := pegaImagens(conteudoHTML)

	for indice, valor := range imagens {
		fmt.Println(indice, valor)
	}

}

func pegaImagens(textoHTML string) (retorno []string) {
	encontraImagem := regexp.MustCompile(`<img[^>]+\bsrc=["']([^"']+)["']`)
	listaDeImagens := encontraImagem.FindAllStringSubmatch(textoHTML, -1)

	retorno = make([]string, len(listaDeImagens))

	for i := range listaDeImagens {
		retorno[i] = listaDeImagens[i][1]
	}
	return
}
```
[Playground](https://play.golang.org/p/b9J9ffTKnT)

Você também pode testar via unit test

```
go test
```

Ou rodar o programa com:

```
go run regexp.go
```

Ou então compilar e executar da seguinte maneira:

```
go build
./regexp
```

## Arquivos desse post:

- [regexp/README.md](https://github.com/go-br/estudos/blob/master/regexp/README.md)
- [regexp/regexp.go](https://github.com/go-br/estudos/blob/master/regexp/regexp.go)
- [regexp/regexp_test.go](https://github.com/go-br/estudos/blob/master/regexp/regexp_test.go)
