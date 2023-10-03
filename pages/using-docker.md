<p align="center">
    <img src="../assets/header-4noobs.svg">
</p>

<h1 align="center">Containers4Noobs</h1>

<p align="center">
    <img src="../assets/containers.jpg" />
</p>

⬅️ [Voltar](../README.md)

# Usando Docker

Aqui os comandos tem a intenção de operar sem a necessidade de ter permissões de administrador.

Sempre que você tiver dúvida, a forma mais direta de acessar o "manual" do Docker é usando o comando:

```sh
$ docker --help
```

Irá retornar uma lista de opções disponíveis do docker.

## Rodando seu primeiro container

Aqui irá depender de qual imagem você baixou. O comando `docker run` necessita de alguns parâmetros específicos para cada imagem baixada (ex: porta onde a imagem será disponibilizada, nome do container, como será inicializada a imagem, diretório/volume da imagem).

Recorra a leitura da [descrição do comando "docker run"](https://docs.docker.com/engine/reference/run/#docker-run-reference) ou ao nosso ["Exemplos Úteis"](#exemplos-uteis) para mais *insights* sobre o funcionamento do comando.

Abaixo vamos explicar o passo a passo do que será necessário para executar seu container.

1. Baixe a imagem desejada:

```sh
$ docker pull docker.io/library/httpd
```

2. Confira se a imagem foi baixada corretamente:

```sh
$ docker images
```

Você deverá ter um output similar a este:

```sh
REPOSITORY               TAG         IMAGE ID      CREATED       SIZE
httpd                    latest      359570977af2  13 days ago   168MB
```

3. Vamos rodar um container com a imagem que acabamos de baixar e export o servidor http para que possamos acessar em nossa máquina:

```sh
$ docker run -dt --name meu-servidor-http -p 8080:80/tcp docker.io/library/httpd
```

> 💡 Você pode executar o comando acima diretamente, sem baixar a imagem, pois ele vai baixar a imagem automaticamente para você!

4. Se tudo der certo você ver seu container rodando com o comando:

```sh
$ docker container ls
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

Da mesma forma essa página deve ser acessível pelo seu navegador. **Parabéns!** Você acabou de executar seu primeiro container.

## Lista de comandos úteis

### Listando containers em andamento:

```sh
$ docker container ls
```

### Inspecionando containers em andamento

```sh
$ docker inspect <id_do_container_ou_imagem>
```

### Mostrando logs do docker no terminal

```sh
$ docker logs <nome_ou_id_do_container>
```

### Visualizando os PID's dos containers

```sh
$ docker top <nome_ou_id_do_container>
```

### Parando um container

```sh
$ docker stop <nome_ou_id_do_container>
```

### Removendo um container inativo

```sh
$ docker rm <nome_ou_id_do_container>
```

### Removendo um container ativo

```sh
$ docker rm -f <nome_ou_id_do_container>
```

### Baixando imagens

```sh
$ docker pull docker.io/library/<imagem_desejada>
```

Após a conclusão do download da imagem, você pode visualizá-las com o comando:

## Alguns exemplos úteis

Nesta seção serão listados alguns exemplos mais parecidos com a vida real que podemos utilizar no dia-a-dia.

### Opções/flags do comando `docker run` que serão utilizadas nos exemplos abaixo

- `--name`: adiciona um nome ao seu container (não é obrigatório e caso você não utilize você pode usar o ID do container para deletá-lo). Exemplo: `--name meucontainer`
- `-d`: roda o container como "daemon" ou seja um serviço (basicamente roda por "baixo dos panos" no seu computador, sem ficar conectado(*attached*) no seu terminal).
- `-p`: mapeia e expõe uma porta no seu SO(Sistema Operacional) a porta do container. Exemplo: `-p <porta_do_seu_sistema_operacional>:<porta_do_container>`
- `-e`: adiciona determinada variável de ambiente para que você adicionar configurações e segredos(senhas) nos seus containers. Exemplo: `-e MINHA_VARIAVEL_DE_AMBIENTE=meuvalor`
- `-v`: cria um mapeamento de uma pasta ou arquivo da sua máquina para dentro do container. Isso trás a possibilidade de guardar seus dados gerados dentro do container na sua máquina evitando perdê-los caso o container seja deletado. Exemplo: `-v /home/meuuser/minhapasta:/tmp/pastanocontainer`

### Executando o Nginx (webserver)

```sh
$ docker run -d --name meu-container-nginx -p 8080:80 nginx:alpine
```

### Executando o Postgres (database)

- **Sem persistência** (os dados são deletados quando o container é deletado, ou seja, você perde o banco, tabelas e dados que tiver dentro do container).

```sh
$ docker run -d \
  --name my-postgres-container \
  -e POSTGRES_PASSWORD=mysecretpassword \
  -e POSTGRES_USER=myuser \
  -e POSTGRES_DB=mydatabase \
  -p 5432:5432 \
  postgres:alpine
```

- **Com persistência** (os dados persistem mesmo se o container for deletado porque estarão linkados a uma pasta no seu Sistema Operacional).

```sh
$ docker run -d \
  --name my-postgres-container \
  -e POSTGRES_PASSWORD=mysecretpassword \
  -e POSTGRES_USER=myuser \
  -e POSTGRES_DB=mydatabase \
  -p 5432:5432 \
  -v /home/meuusuario/minhapastaquequeropersistirosdados:/var/lib/postgresql/data \
  postgres:alpine
```

### Executando o Redis (database)

docker run -d --name my-redis-container -p 6379:6379 redis:latest

```sh
$ docker run -d --name my-redis-container -p 6379:6379 redis:latest

```