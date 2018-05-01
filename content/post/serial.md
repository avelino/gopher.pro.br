+++
title = "Serial"
date = "2017-09-24T20:38:34-03:00"
description = "Em exemplo simples de como ler a porta serial usando o pacote tarm/serial."
tags = ["Golang"]
+++

# Serial

Em exemplo simples de como ler a porta serial usando o pacote tarm/serial.

## instalar o pacote

```
go get github.com/tarm/serial
```

## Abre a porta serial

```go
c := &serial.Config{Name: "/dev/porta-serial", Baud: 115200}
s, err := serial.OpenPort(c)
if err != nil {
	log.Fatal(err)
}
```

## Lendo

```go
buf := make([]byte, 128)
n, err := s.Read(buf)
if err != nil {
	log.Fatal(err)
}
log.Print(string(buf[:n]))
```

## Fechando

É muito importante sempre fechar a porta serial porque esse se ela ficar aberta nenhum programa vai conseguir usar ela.

```go
err = s.Close()
if err != nil {
	log.Fatal(err)
}
```

## Arquivos desse post:

- [serial/README.md](https://github.com/go-br/estudos/blob/master/serial/README.md)
- [serial/arduino-serial](https://github.com/go-br/estudos/blob/master/serial/arduino-serial)
- [serial/example1](https://github.com/go-br/estudos/blob/master/serial/example1)
- [serial/example2](https://github.com/go-br/estudos/blob/master/serial/example2)
