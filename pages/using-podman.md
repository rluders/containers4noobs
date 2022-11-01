<p align="center">
    <img src="../assets/header-4noobs.svg">
</p>

<h1 align="center">Containers4Noobs</h1>

<p align="center">
    <img src="../assets/containers.jpg" />
</p>

⬅️ [Voltar](../README.md)

# Usando Podman

Aqui os comandos tem a intenção de operar sem a necessidade de ter permissões de administrador.

Sempre que você tiver dúvida, a forma mais direta de acessar o "manual" do podman é usando o comando:

```sh
$ podman --help
```

Irá retornar uma lista de opções disponíveis do podman.

## Rodando seu primeiro container

Aqui irá depender de qual imagem você baixou. O comando `podman run` necessita de alguns parâmetros específicos para cada imagem baixada (ex: porta onde a imagem será disponibilizada, nome do container, como será inicializada a imagem, diretório/volume da imagem).

Recorra a leitura da [descrição do comando "podman run"](https://docs.podman.io/en/latest/markdown/podman-run.1.html#description) ou ao nosso ["Exemplo Completo"](#exemplo-completo) para mais *insights* sobre o funcionamento do comando.

No exemplo do [`getting-started`](https://podman.io/getting-started/#running-a-container) do podman temos um exemplo de como rodar um servidor http, vamos explicar o exemplo de forma mais detalhada:

1. Baixe a imagem desejada:

```sh
$ podman pull docker.io/library/httpd
```

2. Confira se a imagem foi baixada corretamente:

```sh
$ podman images
```

Você deverá ter um output similar a este:

```sh
REPOSITORY               TAG         IMAGE ID      CREATED       SIZE
docker.io/library/mongo  latest      a70885e78ca8  39 hours ago  699 MB
```

3. Vamos rodar um container com a imagem que acabamos de baixar e export o servidor http para que possamos acessar em nossa máquina:

```sh
$ podman run -dt --name meu-servidor-http -p 8080:80/tcp docker.io/library/httpd
```

> 💡 Você executar o comando acima diretamente, sem baixar a imagem, pois ele vai baixar a imagem automaticamente para você!

4. Se tudo der certo você ver seu container rodando com o comando:

```sh
$ podman ps
```

O output deverá ser algo similar a:

```sh
CONTAINER ID  IMAGE                           COMMAND           CREATED             STATUS                 PORTS                 NAMES
d2452bb8b3f2  docker.io/library/httpd:latest  httpd-foreground  About a minute ago  Up About a minute ago  0.0.0.0:8080->80/tcp  meu-servidor-http
```

Mas será que o servidor está rodando MESMO? Vamos conferir.

Vode pusar usar `curl` ou simplesmente acessar pelo seu navegador (http://localhost:8080)[http://localhost:8080].

```sh
$ curl http://localhost:8080
```

Se você usar o curl, o seu output deverá ser:

```sh
<html><body><h1>It works!</h1></body></html>
```

Da mesma forma essa página deve ser acessível pelo seu navegador. Parabéns! Você acabou de executar seu primeiro container.

## Lista de comandos úteis

### Listando containers em andamento:

```sh
$ podman ps
```

### Inspecionando containers em andamento
Note: aqui todas as flags `-l` ou `--latest` são referentes ao último container que foi executado por você. Você ainda pode optar por utilizar o **nome** ou **ID** do container para executar as ações específicas para aquele container.

```sh
$ podman inspect -l | grep <endereço_ip_do_container>
```

### Mostrando logs do podman no terminal

```sh
$ podman logs -l
```

### Visualizando os PID's dos containers

```sh
$ podman top -l
```

### Parando um container

```sh
$ podman stop -l
```

### Removendo um container

```sh
$ podman rm -l
```

### Pesquisando e listando por imagens

Podman busca por imagens em registros remotos com algumas keywords simples (Palavras-chave).

```sh
$ podman search <termo_de_busca>
```

Tente: pesquisar por imagens de containers (ex: fedora, go)

Recorra a [documentação do comando search](https://docs.podman.io/en/v4.0.0/markdown/podman-search.1.html) para mais detalhes.

### Baixando imagens

```sh
$ podman pull docker.io/library/<imagem_desejada>
```

É importante entender que o podman usa o domínio do docker para baixar as imagens que você deseja.

Após a conclusão do download da imagem, você pode visualizá-las com o comando:

```sh
$ podman images
```
