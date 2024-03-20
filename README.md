# WASI-WASM

[![en](https://img.shields.io/badge/lang-en-red)](README.md) [![pt-br](https://img.shields.io/badge/lang-pt--br-green)](README.pt-br.md)

This repository contains implementations of container's images that relies on the integration of wasm runtimes and the OCI, via docker, to run wasm applications.

There are two wasm applications, a simple hello world and a load generator written as a quicksort. The latter can receive multiple arguments. Specífic usage can be found [here](./quicksort/README.md).

## Env requirements

As a alternative runtime for docker, we use wasmedge. This will need a shim and the runtime installed, as well as the docker configured to accept it.

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

To run the containers using docker-desktop engine, follow the steps bellow.

Wasm workloads require the containerd image store feature to be turned on. If you’re not already using the containerd image store, then pre-existing images and containers will be inaccessible.

In order to enable containerd image store in docker desktop, follow the instructions bellow.  

- Open the Docker Desktop Settings;
- Go to Features in development and then select the Beta features tab;
- Check the following checkboxes:
  - Use containerd for storing and pulling images;
  - Enable Wasm.
- Select Apply & restart to save the settings;
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

To run the containers using docker engine, follow the steps bellow: (wasi-wasm containerd shims wasnt supported by the time i wrote this)

Go to file /etc/docker/daemon.json and add this inside it's command block:

```bash
  "features": {
    "containerd-snapshotter": true
  }
```

> You need to add a "," in the end of the line before "features" line.

If that file doest exists, then you create it and paste inside:

```bash
{
  "features": {
    "containerd-snapshotter": true
  }
}
```

Then you want to restart docker.service with command:

```bash
sudo systemctl restart docker.service
```

</details>
