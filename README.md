<h1 align="center">
    <a href="https://docs.docker.com/">🔗 Docker</a>
</h1>

# Iniciando com Docker

<strong>docker run</strong> => Inicia um container com uma determinada image.

<strong>parameters</strong>

- <strong>-it</strong> Inicia o container em modo interativo.
  > example: docker run -it ubuntu:latest bash
- <strong>--rm</strong> Remove o container ao finalizar.
  > example: docker run --rm ubuntu:latest bash
- <strong>-p</strong> Direciona portas.
  > example: docker run -p 8080:80 nginx:latest
- <strong>-d</strong> Inicia o container em background.
  > example: docker run -d nginx:latest
- <strong>--name</strong> Define um nome para o container.
  > example: docker run --name my-nginx nginx:latest
- <strong>-v</strong> Cria um volume.

  > example: docker run -v /var/www/html:/var/www/html nginx:latest

  > example: docker run -v meudiretorio:diretoriodocontainer nginx:latest

- <strong>--mount</strong> Cria um volume explicitamente.

  > example: docker run --mount type=bind,source=/var/www/html,target=/var/www/html nginx:latest

<strong>docker ps</strong> => Lista os containers ativos no momento.

<strong>docker ps -a</strong> => Lista todos os containers ativos e inativos no momento.

<strong>docker ps -q</strong> => Lista os containers ativos no momento, retornando apenas o ID.

<strong>docker stop</strong> => Para um container.

> example: docker stop nomedocontainer ou id do container

<strong>docker start</strong> => Inicia um container que está parado.

> example: docker start nomedocontainer ou id do container

<strong>docker rm</strong> => Remove um container.

> example: docker rm nomedocontainer ou id do container

> example: docker rm nomedocontainer ou id do container -f (force) O container será removido mesmo que esteja rodando.

<strong>docker rm $(docker ps -a -q) -f</strong> => Remove todos os containers.

<strong>docker exec</strong> => Executa comandos no container.

> example: docker exec nomedocontainer ls

> example: docker exec -it nomedocontainer bash

<strong>docker volume</strong> => Volumes do docker.

<strong>characteristics</strong>

- Pode ser compartilhado entre containers.

  > example: docker run --name nginx-one --mount type=volume,source=meuvolume,target=/var/www/html nginx:latest

  > example: docker run --name nginx-two --mount type=volume,source=meuvolume,target=/var/www/html nginx:latest

  > example: docker run --name nginx-three -v meuvolume:/var/www/html nginx:latest

<strong>parameters</strong>

- <strong>create</strong> Cria um volume.

  > example: docker volume create meuvolume

- <strong>ls</strong> Lista os volumes existentes.

  > example: docker volume ls

- <strong>inspect</strong> Exibe informações sobre um volume.

  > example: docker volume inspect meuvolume

- <strong>prume</strong> Remove os arquivos dos volumes.
  > example: docker volume prune

<br>

# Trabalhando com imagens

<strong>docker imagens</strong> => Lista as imagens existentes.

<strong>docker pull</strong> => Baixa uma imagem do docker hub.

> example: docker pull nginx:latest

<strong>docker rmi</strong> => Remove uma imagem.

> example: docker rmi imagem:tag

<strong>Dockerfile</strong>

- Arquivo de configuração para criar uma imagem.

- Cada imagem é composta por um Dockerfile.

- <strong>parameters</strong>

  - <strong>FROM</strong> => Define a imagem base.

    > example: FROM nginx:latest

  - <strong>USER</strong> => Define o usuário do container.

    > example: USER william

    - <strong>root</strong> default

  - <strong>WORKDIR</strong> => Define o diretório de trabalho.

    > example: WORKDIR /app

  - <strong>RUN</strong> => Executa um comando.

    > example: RUN apt-get update && apt-get install vim -y

  - <strong>COPY</strong> => Copia arquivos para dentro do container.

    > example: COPY ./index.html /app/index.html

  - <strong>ENTRYPOINT</strong> => Define o comando que será executado quando o container for iniciado.

    > example: ENTRYPOINT ["echo", "Hello"]

    - Comando fixo, que sempre que o container for iniciado, o comando será executado.

  - <strong>CMD</strong> => Define o comando que será executado quando o container for iniciado.

    > example: CMD ["World"]

    - Comando variavel, que pode ser alterado ao iniciar o container.

<strong><a href="https://hub.docker.com/">🔗 Docker Hub</a></strong>

- Repositório de imagens docker.

<strong>docker build</strong>

- Cria uma imagem a partir de um Dockerfile.

  > example: docker build -t nomedaimagem .

- <strong>parameters</strong>
  - <strong>-t</strong> => Define o nome da imagem.
  - <strong>.</strong> => Diretório onde está o Dockerfile.

<strong>docker push</strong>

- Envia uma imagem para o Docker Hub.

  > example: docker push nomedaimagem
