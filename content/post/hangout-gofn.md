+++
title = "Usando gofn para subir containers docker e rodar Clojure e Python"
description = "Como usar gofn para carregar containers Docker e se comunicar com eles. Mostramos três containers rodando com gofn, dois em Python e um em Clojure."
tags = ["Golang"]
date = "2018-07-05T06:45:14Z"
+++

{{< youtube s8VN26tSQEY >}}

# Como carregar containers Docker usando gofn

![GitHub Logo](https://raw.githubusercontent.com/gofn/gofn/master/docs/assets/logo.png =250x250)

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

Links mencionados, alguns foram mencionados fora da gravação:

- [Código fonte de hoje](https://play.golang.org/p/LGj23boK-SO)
- [Repositório do nosso grupo](https://github.com/go-br/estudos)
- [E você encontra mais exemplos aqui](https://github.com/go-br)

Nossos encontros ocorrem todas as quintas-feiras ás 22h00, para participar [entre no canal de Go no slack](https://invite.slack.golangbridge.org/) e procure por #brazil