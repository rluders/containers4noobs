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

# Familiarizando-se com o Podman
Aqui os comandos tem a intenção de operar sem a necessidade de ter permissões de administrador.

### Certificando-se que a instalação do Podman foi um sucesso:

```
podman --version
```
Esperamos: `podman version 3.4` ou acima.


### Buscando por ajuda:

```console
podman --help
```
Irá retornar uma lista de opções disponíveis do podman.


### Pesquisando e listando por imagens:
Podman busca por imagens em registros remotos com algumas keywords simples (Palavras-chave).

```console
podman search <termo_de_busca>
```
Tente: pesquisar por imagens de containers (ex: fedora, go)

Recorra a [documentação do comando search](https://docs.podman.io/en/v4.0.0/markdown/podman-search.1.html) para mais detalhes.


### Baixando imagens:

```console
podman pull docker.io/library/<imagem_desejada>
```
É importante entender que o podman usa o domínio do docker para baixar as imagens que você deseja.

Após a conclusão do download da imagem, você pode visualizá-las com o comando:

```console
podman images
```


### Rodando a imagem baixada:
Aqui irá depender de qual imagem você baixou. O comando `podman run` necessita de alguns parâmetros específicos para cada imagem baixada (ex: porta onde a imagem será disponibilizada, nome do container, como será inicializada a imagem, diretório/volume da imagem).

Recorra a leitura da [descrição do comando "podman run"](https://docs.podman.io/en/latest/markdown/podman-run.1.html#description) ou ao nosso ["Exemplo Completo"](#exemplo-completo) para mais *insights* sobre o funcionamento do comando.

No exemplo do [`getting-started`](https://podman.io/getting-started/#running-a-container) do podman temos:

```console
podman run -dt -p 8080:80/tcp docker.io/library/httpd
```
**Não repita esse comando caso não esteja rodando o container de 'httpd', ele está parametrizado com as especificações de um container 'httpd'.**


### Listando containers em andamento:

```console
podman ps
```

### Inspecionando containers em andamento
Note: aqui todas as flags `-l` ou `--latest` são referentes ao último container que foi executado por você. Você ainda pode optar por utilizar o **nome** ou **ID** do container para executar as ações específicas para aquele container.
```console
podman inspect -l | grep <endereço_ip_do_container>
```

### Mostrando logs do podman no terminal

```console
podman logs -l
```

### Visualizando os PID's dos containers
```console
podman top -l
```

### Parando um container
```console
podman stop -l
```

### Removendo um container
```console
podman rm -l
```


### Exemplo completo de um container MongoDB funcional

Baixando uma imagem MongoDB com podman:
```console
podman pull docker.io/library/mongo
```
output:
```console
Trying to pull docker.io/library/mongo:latest...
```

Ao final do download esperamos:
```console
Getting image source signatures
Copying blob bcf274af89b0 done
Copying blob 73a471eaa4ad done
Copying blob 7fd6635b9ddf done
Copying blob 73738965c4ce done
Copying blob 6f9c8c301e0f done
Copying blob 675920708c8b done
Copying blob 04fc489f2a3b done
Copying blob e1abc36251b9 done
Copying blob 396db6f4d800 done
Copying config a70885e78c done
Writing manifest to image destination
Storing signatures
a70885e78ca893b5e53b9c8f0d0679ac828f4d8846ce144a8cbca60c001cfe91
```
Ou algo similar...

Visualizando a imagem baixada:

```console
podman images
```
output:

```console
REPOSITORY               TAG         IMAGE ID      CREATED       SIZE
docker.io/library/mongo  latest      a70885e78ca8  39 hours ago  699 MB
```

Rodando a imagem com o podman:
```console
podman run -dt --name <nome_desejado> -p 27017:27017 -v '/home/<username>/podman/data:/data/db:Z' docker.io/library/mongo:latest
```
explicando o comando acima:

- As flags `-d` e `-t` ou apenas`-dt` representadas juntas reproduzem duas coisas:

    - 1º Expressa que o container irá rodar em background ou 'Detached Mode' como explicado na documentação...

    - 2º Aloca um 'pseudo-TTY' ou um 'pseudo-terminal' ao seu container...

**leia mais sobre [TTY](https://www.man7.org/linux/man-pages/man1/tty.1.html) e [PTY](https://man7.org/linux/man-pages/man7/pty.7.html) no manual.**

- A flag `--name` nomeia a sua imagem/container para melhor identificação/utilização em seu(s) projeto(s).

- E então <nome_desejado> você troca para um nome de sua preferência, seja específico/exclusivo de um projeto ou apenas o nome do que você estará rodando.

- A flag `-p` é referente a qual porta você disponibilizará na sua máquina local e qual porta a imagem/container utilizará para instanciar suas funcionalidades.

- A flag `-v` é referente ao 'volume' que o container utilizará, em outras palavras, em qual diretório será montado o container.

- no nosso exemplo temos: `'/home/<username>/podman/data:/data/db:Z'`

- certifique-se de ter criado o diretório `/home/<username>/podman/data`

- troque `<username>` para o seu nome de usuário. (ex: 'rluders' ou 'grandehe4rt')

### Listando containers em andamento:

```console
podman ps
```


## Instalando o Docker

@TODO