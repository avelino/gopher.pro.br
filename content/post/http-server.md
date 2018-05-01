+++
title = "HTTP Server"
date = "2018-03-09T14:55:13-03:00"
description = "Este é um pequeno servidor HTTP usado para testes de clientes."
tags = ["Golang"]
+++

# HTTP Server

Este é um pequeno servidor HTTP usado para testes de clientes.

Ele abre a porta 8080 e ecoa tudo que for enviado para ele via terminal.

Para executar basta

```console
go get ./...
go run main.go
```

Se quiser ver um exemplo um pouco mais avançado usando HTTPS e servindo múltiplos domínios vá para [go-br/server](https://github.com/go-br/server)

## Arquivos desse post:

- [server/README.md](https://github.com/go-br/estudos/blob/master/server/README.md)
- [server/main.go](https://github.com/go-br/estudos/blob/master/server/main.go)
