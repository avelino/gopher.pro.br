+++
title = "godoc"
date = "2016-11-11T17:00:21-05:00"
description = "Go tem uma ferramenta muito poderosa para visualizar documentação."
tags = ["Golang"]
+++
# godoc

Go tem uma ferramenta muito poderosa para visualizar documentação.

Exemplos:

```sh
godoc fmt
godoc github.com/crgimenes/rotateString
```

Você pode facilmente exportar a documentação em formato html:

```sh
godoc -html github.com/crgimenes/rotateString > rotateString.html
```

Ou ainda subir a documentação toda em um servidor html.

```sh
godoc -http=:6060
```

## Arquivos desse post:

- [godoc/README.md](https://github.com/go-br/estudos/blob/master/godoc/README.md)
