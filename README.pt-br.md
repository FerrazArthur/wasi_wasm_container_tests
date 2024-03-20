# WASI-WASM

[![en](https://img.shields.io/badge/lang-en-red)](README.md) [![pt-br](https://img.shields.io/badge/lang-pt--br-green)](README.pt-br.md)

Este repositório contém implementações de imagens de contêiner que dependem da integração de runtimes WASM e do OCI, via docker, para executar aplicações WASM.

Existem duas aplicações WASM, um simples hello world e um gerador de carga escrito como um quicksort. Este último pode receber vários argumentos. O uso específico pode ser encontrado [aqui](./quicksort/README.pt-br.md).

## REQUISITOS DO AMBIENTE

Como um runtime alternativo para o docker, usamos o wasmedge. Isso exigirá um shim e o runtime instalado, além do docker configurado para aceitá-lo.

### Shims

Instale as  shims do repositório [deislabs/containerd-wasm-shims](https://github.com/deislabs/containerd-wasm-shims/releases).

### Wasmedge

Instale o wasmedge do repositório [oficial source](https://wasmedge.org/docs/start/install/) com o comando:  

```bash
curl -sSf https://raw.githubusercontent.com/WasmEdge/WasmEdge/master/utils/install.sh | bash -s -- -p /usr/local
```

### Configuração do Docker

<details>
<summary> Docker desktop engine </summary>

#### Docker Desktop Engine

Para executar os containers utilizando o docker-desktop, siga os passos a seguir.

Cargas de trabalho wasm requerem a ativação do recurso "image store" do containerd.

Para ativar esse recurso, siga as instruções abaixo.  

- Abra as configurações do docker desktop;
- Em "Features in development", selecione a aba com os recursos em beta;
- Ative as seguintes caixas:
  - "Use containerd for storing and pulling images";
  - "Enable WASM".
- Aplique as alterações e reinicie o cliente;
- No dialogo de confirmação, selecione "Install" para que os runtimes WASM sejam instalados.

O Docker desktop irá baixar e instalar os seguintes runtimes, que podem ser utilizados para executar cargas de trabalho WASM:

- io.containerd.slight.v1
- io.containerd.spin.v1
- io.containerd.wasmedge.v1
- io.containerd.wasmtime.v1

</details>

<details>
<summary> Docker Engine 24.0.6</summary>

#### Docker Engine 24.0.6

Para executar os contêineres usando o Docker Engine, siga as etapas abaixo: (os shims wasi-wasm do containerd não eram suportados no momento em que escrevi isso)

Vá para o arquivo /etc/docker/daemon.json e adicione isso dentro do bloco de comando dele:

```bash
  "features": {
    "containerd-snapshotter": true
  }
```

> Você precisa adicionar uma "," ao final da linha antes da linha "features".

Se esse arquivo não existe, então você o cria e cola dentro dele:

```bash
{
  "features": {
    "containerd-snapshotter": true
  }
}
```

Em seguida, reinicie o serviço do Docker executando o comando: 

```bash
sudo systemctl restart docker.service
```

</details>
