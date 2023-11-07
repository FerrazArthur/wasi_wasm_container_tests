# hello world wasm code

The wasmc.sh file is a helper to compile the c code into a wasm, with help of clang toolchain modules.toml is a file for use with wagi

### Build

This image is already in the repository registry, but the build command follows:  

```bash
$ docker buildx build -t hello .
```

### Run

```bash
$ docker container run --rm --runtime io.containerd.wasmedge.v1 -i registry.quant1.com.br/arthur/wasm-wasi-tests:main-hello
```
