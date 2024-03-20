# HELLO WORLD WASM

[![en](https://img.shields.io/badge/lang-en-red)](/hello/README.md) [![pt-br](https://img.shields.io/badge/lang-pt--br-green)](/hello/README.pt-br.md)

## BUILD

This image is already in the repository registry, but the build command follows:  

```bash
docker buildx build -t hello .
```

## RUN

```bash
docker container run --rm --runtime io.containerd.wasmedge.v1 -i ghcr.io/ferrazarthur/wasi_wasm_container_tests:hello
```
