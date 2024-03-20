# QUICKSORT LOAD GENERATOR

[![en](https://img.shields.io/badge/lang-en-red)](/quicksort/README.md) [![pt-br](https://img.shields.io/badge/lang-pt--br-green)](/quicksort/README.pt-br.md)

This is a load generator algorithm that implements the wost case search for quicksort O(n²).

## BUILD

This image is already in the repository registry, but the build command follows:  

```bash
docker buildx build -t quicksort .
```

## RUN

To see all possible arguments, type:

```bash
docker container run --rm --runtime io.containerd.wasmedge.v1 -i ghcr.io/ferrazarthur/wasi_wasm_container_tests:quicksort --help
```
