# HELLO WORLD WASM

[![en](https://img.shields.io/badge/lang-en-red)](/hello/README.md) [![pt-br](https://img.shields.io/badge/lang-pt--br-green)](/hello/README.pt-br.md)

## BUILD

Esta imagem já está no registro do repositório, mas o comando de construção segue abaixo:  

```bash
docker buildx build -t hello .
```

## EXECUTAR

```bash
docker container run --rm --runtime io.containerd.wasmedge.v1 -i registry.quant1.com.br/arthur/wasm-wasi-tests:main-hello
```
