+++
title = "net Listando Interfaces e IPs"
date = "2016-11-11T17:00:21-05:00"
description = "Um exemplo simples listando as interfaces de rede."
tags = ["Golang"]
+++

# net Listando Interfaces e IPs

Um exemplo simples listando as interfaces de rede.

```go
package main

import (
	"fmt"
	"net"
)

func main() {
	ifaces, _ := net.Interfaces()
	for _, i := range ifaces {

		fmt.Printf("-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-\n")
		fmt.Printf("%v - %v\n", i.Name, i.HardwareAddr)
		addrs, err := i.Addrs()
		if err != nil {
			panic(err.Error())
		}

		for _, a := range addrs {
			if ipnet, ok := a.(*net.IPNet); ok {
				if ipnet.IP.To4() != nil {
					fmt.Printf("ip: %v\n", ipnet.IP.String())
				} else {
					fmt.Printf("ipv6: %v\n", ipnet.IP.String())

				}
			}
		}
	}
}
```

## Arquivos desse post:

- [net/README.md](https://github.com/go-br/estudos/blob/master/net/README.md)
- [net/net.go](https://github.com/go-br/estudos/blob/master/net/net.go)
