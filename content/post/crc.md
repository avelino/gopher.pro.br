+++
title = "CRC"
date = "2017-09-14T22:50:05-03:00"
description = "Calcular o CRC de uma string ou um arquivo é muito útil para garantir que algum dado não foi alterado. As funções CRC tem a vantagem de serem rápidas comparado com outras formas de hash."
tags = ["Golang"]
+++

# CRC

Calcular o CRC de uma string ou um arquivo é muito útil para garantir que algum dado não foi alterado. As funções CRC tem a vantagem de serem rápidas comparado com outras formas de hash.

```
package main

import (
    "fmt"
    "hash/crc32"
)

func main() {
    valor := "Isto é um teste"    
    checksum := crc32.ChecksumIEEE([]byte(valor))
    fmt.Printf("Checksum: 0x%x\n", checksum)
}
```

## Arquivos desse post:

- [crc/README.md](https://github.com/go-br/estudos/blob/master/crc/README.md)
- [crc/checksum32](https://github.com/go-br/estudos/blob/master/crc/checksum32)
- [crc/checksum64](https://github.com/go-br/estudos/blob/master/crc/checksum64)
