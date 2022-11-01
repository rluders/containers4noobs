<p align="center">
    <img src="../assets/header-4noobs.svg">
</p>

<h1 align="center">Containers4Noobs</h1>

<p align="center">
    <img src="../assets/containers.jpg" />
</p>

⬅️ [Voltar](../README.md)

# Instalação do Ambiente no Linux

Essa página tem como objetivo auxiliar na instalação de ferramentas de Containers no Linux, sendo que nesse tutorial abordaremos duas ferramentas:

- 👍 [Podman](#instalando-o-podman)
- [Docker](#instalando-o-docker)

## Instalando o Podman

### Debian / Ubuntu

```console
sudo apt-get -y update
sudo apt-get -y install podman
```

### Arch & Manjaro

```console
sudo pacman -S podman
```

### Fedora

```console
sudo dnf -y install podman
```
Caso esteja no **Fedora 35** utilize:

```console
sudo dnf -y copr enable rhcontainerbot/podman4
sudo dnf -y install podman
```


### CentOS

```console
sudo yum -y install podman
```


### Alpine

```console
sudo apk add podman
```


### Gentoo

```console
sudo emerge app-emulation/podman
```

### Certificando-se que a instalação do Podman foi um sucesso:

```
podman --version
```
Esperamos: `podman version 3.4` ou acima.

Agora que você já tem o Podman instalado, que tal [aprender como usar-lo?](./using-podman.md)

## Instalando o Docker

@TODO