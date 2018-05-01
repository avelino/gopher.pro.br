+++
title = "Go com C"
date = "2016-11-11T17:00:21-05:00"
description = "Go é ótimo mas as vezes é necessário usar alguma biblioteca de algum legado ou integrar com algum sistema embarcado que precisa de C para descer até o hardware. Felizmente é muito fácil integrar Go com C."
tags = ["Golang"]
+++

# Go com C

Go é ótimo mas as vezes é necessário usar alguma biblioteca de algum legado ou integrar com algum sistema embarcado que precisa de C para descer até o hardware. Felizmente é muito fácil integrar Go com C.

Veja o exemplo:

```go
package main

/*
int sum(int a,int b) {
	return a+b;
}
*/
import "C"

import (
	"fmt"
)

func main() {
	r := C.sum(2, 2)
	fmt.Printf("sum(2,2) = %v\r\n", r)

}
```

Sim eu sei que é estranho mas é isso mesmo, você coloca seu código em C dentro de um comentário especial que deve vir exatamente na linha anterior a *import "C"*.

Uma boa pratica é colocar nesse comentário apenas um arquivo de include do C com as rotinas que você quer consumir em Go e as diretivas de processamento, mas para rotinas muito pequenas e exemplos como esses, tudo bem colocar direto no código.

Agora vamos ver um exemplo um pouco mais complexo, usando uma biblioteca externa para fazer um LED piscar no [Intel Edison](https://software.intel.com/pt-br/iot/hardware/edison).

```go
package main

/*
    #cgo LDFLAGS: -lmraa
    #include <mraa.h>

    mraa_gpio_context led;

	void config(void) {
        led = mraa_gpio_init(13);
        mraa_gpio_dir(led, MRAA_GPIO_OUT);
	}

    void blink(int b) {
        mraa_gpio_write(led,b);
    }

*/
import "C"

import (
	"fmt"
	"time"
)

func main() {
	C.config()
	for {
		fmt.Print("blink!\r\n")
		C.blink(1)
		time.Sleep(300 * time.Millisecond)
		C.blink(0)
		time.Sleep(300 * time.Millisecond)
	}
}
```

## Arquivos desse post:

- [go_com_c/README.md](https://github.com/go-br/estudos/blob/master/go_com_c/README.md)
- [go_com_c/go_com_c_blink.go](https://github.com/go-br/estudos/blob/master/go_com_c/go_com_c_blink.go)
- [go_com_c/go_com_c_sum.go](https://github.com/go-br/estudos/blob/master/go_com_c/go_com_c_sum.go)
