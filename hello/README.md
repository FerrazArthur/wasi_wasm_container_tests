# hello world wasm code

The wasmc.sh file is a helper to compile the c code into a wasm, with help of clang toolchain modules.toml is a file for use with wagi

## Env requirements

### Shims

Get and install shims from repo [deislabs/containerd-wasm-shims](https://github.com/deislabs/containerd-wasm-shims/releases).

### Wasmedge

In order to install wasmedge, you can get it from the [oficial source](https://wasmedge.org/docs/start/install/) with the command:  

```bash
curl -sSf https://raw.githubusercontent.com/WasmEdge/WasmEdge/master/utils/install.sh | bash -s -- -p /usr/local
```

### Docker configuration

<details>
<summary> Docker desktop engine </summary>

#### Docker Desktop Engine

The easiest way to run the images is to use docker-desktop.

Wasm workloads require the containerd image store feature to be turned on. If you’re not already using the containerd image store, then pre-existing images and containers will be inaccessible.

- Open the Docker Desktop Settings.  
- Go to Features in development and then select the Beta features tab.
- Check the following checkboxes:  
    - Use containerd for storing and pulling images
    - Enable Wasm
- Select Apply & restart to save the settings.
- In the confirmation dialog, select Install to install the Wasm runtimes.

Docker Desktop downloads and installs the following runtimes that you can use to run Wasm workloads:

- io.containerd.slight.v1
- io.containerd.spin.v1
- io.containerd.wasmedge.v1
- io.containerd.wasmtime.v1

</details>

<details>
<summary> Docker Engine 24.0.6</summary>

#### Docker Engine 24.0.6

Go to file /etc/docker/daemon.json and add this inside it's command block:

```bash
  "features": {
    "containerd-snapshotter": true
  }
```

> You need to add a "," in the end of the line before "features": line.

If that file doest exists, then you create it and paste inside:

```bash
{
  "features": {
    "containerd-snapshotter": true
  }
}
```

Then you want to restart docker.service.

</details>

### Build

```bash
$ docker buildx build -t hello .
```

### Run

```bash
$ docker container run --rm --runtime io.containerd.wasmedge.v1 -i hello
```
