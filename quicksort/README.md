# Quicksort load generator

This is a load generator algorithm that implements the wost case search for quicksort O(n²).

### Build

This image is already in the repository registry, but the build command follows:  

```bash
$ docker buildx build -t quicksort .
```

### Run

To see all possible arguments, type:

```bash
$ docker container run --rm --runtime io.containerd.wasmedge.v1 -i registry.quant1.com.br/arthur/wasm-wasi-tests:main-quicksort --help
```
