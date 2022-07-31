<p align="center">
    <img src="assets/header-4noobs.svg">
</p>

<h1 align="center">Containers4Noobs</h1>

<p align="center">
    <img src="assets/containers.jpg">
</p>

# Introdução

Esse 4Noobs tem como objetivo ajudar quem quer começar a entender o conceito de containers, como utilizar, suas vantagens e ferramentas.


Ao longo do guia eu vou usar alguns ícones como informações extras, então, aqui está a legenda:

- 👍 = Recomendado
- 💰 = Pago

# Requisitos

Containers são Linux, viva com isso!

Para trabalhar de forma eficiência com containers você vai precisar saber um pouco de Linux, existe um 4Noobs para isso aqui: [Linux4Noobs](https://github.com/lucashe4rt/linux4noobs)

Você também vai precisar saber instalar aplicações no seu computador (seja, Linux, Windows ou Mac). E isso nos leva ao próximo requisito, você vai precisar de um computador.

Eu recomendaria no mínimo um i5 (ou equivalente) com pelo menos 8Gb de memória e uns 60Gb de espaço livre em disco.

# Roadmap

## Introdução

### O que são containers?

Container é uma tecnologia para criar um ambiente isolado para rodar serviços. Tentando ser o mais claro possível: é como se você tivesse distribuíndo junto com a sua aplicação/serviço todo o sistema configurado, necessário para que a aplicação seja executada sem muitos problemas. 

Desta forma, isso também permite que esta aplicação seja facilmente movida de um contexto/servidor para outro, sem grandes problemas.

Existem algumas pessoas que costumam chamar containers de Docker, e isso é equivocado, um container é um processo, enquanto o Docker é um serviço de container. Existem vários outros serviços para rodar containers, Docker é apenas um dos mais conhecidos.

Cada container deve ter apenas uma responsabilidade, ou seja, executar apenas uma aplicação/serviço. Desta forma você consegue isolar ambientes e processos, garantido que não haja conflito entre dependências ou até mesmo mapeamento de portas, etc.

Vale lembrar que, apesar de bastante similar, um container não é uma máquina virtual (VM), inclusive, você pode rodar containers dentro de uma VM.

### Qual a diferença de Container e Máquina Virtual (VM)?
@TODO

### Docker, LXC e VM. Quais são as diferenças?
@TODO

## Como instalar?
@TODO

## Usando containers
@TODO

## Orquestrando containers

### Kubernetes
@TODO

### Openshift
@TODO

### Docker Swarm
@TODO

# Recursos

## Livros

-  🇺🇸👍 [OpenShift for Developers, Second Edition](https://developers.redhat.com/e-books/openshift-for-developers)
- 🇺🇸 [Containers Networking: From Docker to Kubernetes](https://www.nginx.com/resources/library/container-networking-docker-kubernetes/)
- 🇧🇷👍 [Como criar aplicações modernas com containers Linux](https://www.redhat.com/pt-br/resources/building-modern-apps-with-containers-ebook)
- 🇧🇷💰 [Contrainers com Docker: Do desenvolvimento à producação](https://www.amazon.com.br/Containers-com-Docker-desenvolvimento-produ%C3%A7%C3%A3o-ebook/dp/B019NJB50C)

## Ferramentas

- [Docker](https://www.docker.com/)
- 👍 [Podman](https://podman.io/)

## Cursos completos

- 🇺🇸👍 [Kubernetes Crash Course for Absolute Beginners](https://www.youtube.com/watch?v=s_o8dwzRlu4)

## Vídeos

- 🇧🇷👍 [O mínimo que você precisa saber sobre Docker](https://www.youtube.com/watch?v=ntbpIfS44Gw)
- 🇧🇷👍 [Containers, Docker e Kubernetes com Giovanni Bassi](https://www.youtube.com/watch?v=wxLvvMxzc1Q)
- 🇧🇷 [Containers // Dicionário do Programador](https://www.youtube.com/watch?v=-pUZBovqRcU)
- 🇧🇷 [Afinal, o que é um container?](https://www.treinaweb.com.br/blog/afinal-o-que-e-um-container)

# Como contribuir

Contribuições fazem com que a comunidade opensource seja um lugar incrível para aprender, inspirar e criar. Todas contribuições são extremamente apreciadas.

- Realize um Fork do projeto
- Crie um branch com a nova feature (git checkout -b feature/sua-feature)
- Realize o Commit (git commit -m 'Adicionado conteudo brabo')
- Realize o Push no Branch (git push origin feature/sua-feature)
- Abra um Pull Request

Não sabe usar Git? [Git4Noobs](https://github.com/DanielHe4rt/git4noobs)

# Contribuidores

<a href="https://github.com/rluders/containers4noobs/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=rluders/containers4noobs"/>
</a>

<br/><br/>

<p align="center">
  <a href="https://github.com/he4rt/4noobs" target="_blank">
    <img src="assets/footer-4noobs.svg" width="380">
  </a>
</p>