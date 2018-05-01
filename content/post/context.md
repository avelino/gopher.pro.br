+++
title = "context"
date = "2017-09-23T18:34:49-03:00"
description = "Exemplos simples de contexto"
tags = ["Golang"]
+++
# context

Exemplos simples de contexto

```go
import (
	"bufio"
	"context"
	"fmt"
	"os"
	"time"
)

func main() {
	ctx := context.Background()
	ctx, cancel := context.WithTimeout(ctx, 1*time.Second)

	defer cancel()

	go func(ctx context.Context, cancel context.CancelFunc) {
		s := bufio.NewScanner(os.Stdin)
		s.Scan()
		cancel()
	}(ctx, cancel)

	select {
	case <-time.After(5 * time.Second):
		fmt.Println("timeout")
	case <-ctx.Done():
		fmt.Println(ctx.Err())
	}
}
```

## Arquivos desse post:

- [context/README.md](https://github.com/go-br/estudos/blob/master/context/README.md)
- [context/example1](https://github.com/go-br/estudos/blob/master/context/example1)
- [context/example2](https://github.com/go-br/estudos/blob/master/context/example2)
