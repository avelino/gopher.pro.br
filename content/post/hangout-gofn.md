+++
title = "Usando gofn para subir containers docker e rodar Clojure e Python"
description = "Como usar gofn para carregar containers Docker e se comunicar com eles. Mostramos três containers rodando com gofn, dois em Python e um em Clojure."
tags = ["Golang"]
date = "2018-07-05T06:45:14Z"
+++

{{< youtube s8VN26tSQEY >}}

# Como carregar containers Docker usando gofn

[![gofn](https://gopher.pro.br/gofn.png)](https://github.com/gofn/gofn)

Primeiro instanciamos a struct BuildOptions que vai informar para o gofn os detalhes do container como o nome da imagem por exemplo.

```go
buildOpts := &provision.BuildOptions{
	ImageName: "nome da imagem aqui",
	StdIN:     "o que você quer passar no stdin para o container aqui",
	DoNotUsePrefixImageName: true,
}
```

Depois instanciamos as opções do container por exemplo se você quer passar variáveis de ambiente.

```go
containerOpts := &provision.ContainerOptions{}
```

É uma boa pratica criar um contexto e definir um timeout para ele, no nosso caso definimos um timeout de 5 segundos, se seu container não retornar nesse tempo o gofn se encarrega de matar ele.

```go
ctx, cancelFunc := context.WithTimeout(
	context.Background(),
	time.Duration(5)*time.Second)
```

Então rodamos o gofn passando nossas opções e pegamos o retorno de stdin, stdout e error caso exista.

```go
stdout, stderr, err = gofn.Run(ctx, buildOpts, containerOpts)
```

Por fim como criamos uma função cancel devido ao nosso contexto de timeout sempre temos que chamar a função cancel no final.

```go
cancelFunc()
```

## O container

É bem simples fazer containers docker para usar com gofn, basicamente tudo que você faz com um container normal vai funcionar, geralmente preferimos mandar e receber informações via stdin, sdtout e stderr porque é uma forma simples e fácil de modificar.

Esse é um exemplo bem simples usando Clojure:

```clojure
(ns runner.core
  (:gen-class))

(defn upper []
  (print (clojure.string/upper-case (slurp *in*)))
  (flush))

(defn -main []
  (upper))
```

E agora um exemplo usando Python:

```python
import sys
import json
import base64

d = json.load(sys.stdin)
d["encoded"] = base64.b64encode(d["phrase"].encode('utf-8')).decode('utf-8')
json.dump(d, sys.stdout, ensure_ascii=False)
```

Links mencionados, alguns foram mencionados fora da gravação:

- [Código fonte de hoje](https://github.com/crgimenes/gofn-example)
- [Repositório do gofn](https://github.com/gofn/gofn)
- [Repositório do nosso grupo](https://github.com/go-br/estudos)
- [E você encontra mais exemplos aqui](https://github.com/go-br)
- [Pagina do grupo de estudos](https://gopher.pro.br)

Nossos encontros ocorrem todas as quintas-feiras ás 22h00, para participar [entre no canal de Go no slack](https://invite.slack.golangbridge.org/) e procure por #brazil