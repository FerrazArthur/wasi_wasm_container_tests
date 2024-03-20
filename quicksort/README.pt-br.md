# GERADOR DE CARGA QUICKSORT

[![en](https://img.shields.io/badge/lang-en-red)](/quicksort/README.md) [![pt-br](https://img.shields.io/badge/lang-pt--br-green)](/quicksort/README.pt-br.md)

Este é um algoritmo gerador de carga que implementa a busca pelo pior caso do quicksort, que é O(n²).

## BUILD

Este imagem já está no registro do repositório, mas o comando de construção segue abaixo:

```bash
docker buildx build -t quicksort .
```

## EXECUTAR

Para ver todos os argumentos possíveis, digite:

```bash
docker container run --rm --runtime io.containerd.wasmedge.v1 -i ghcr.io/ferrazarthur/wasi_wasm_container_tests:quicksort --help
```
