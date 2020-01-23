# LT - Docker

## O que é docker? 

Docker é uma plataforma desenvolvida sobre LXC para virtualização, seu principal objetivo foi facilitar a distribuição de software e infraestrutura. 

## Quais as vantagens de usar?

Isolamento
Economia de recursos** 
Disponibilidade 
Padronização 

## Ok é bom, e desvantagens?

Gerenciamento
Tamanho** 

### Comandos básicos

| Comando           | Descrição                                     |
|-------------------|-----------------------------------------------|
| `docker run`      | Inicia um container a partir de uma imagem    | 	
| `docker ps`       | Lista containers em execução.                 |
| `docker stats`    | Informações sobre CPU/MEM                     |
| `docker start`    | Inicia um container já existente  	        |
| `docker stop`     | Finaliza o container                          |
| `docker rm`       | Remove um container                           |
| `docker logs`     | Visualização de logs do container             |
| `docker images`   | Lista as imagens locais.                      |
| `docker pull`	    | Baixa imagem do repositório                   |
| `docker push`     | Envia imagem para o repositório               |

### Criando primeiro container 

```bash
 docker pull nginx:alpine
 docker images | grep alpine 
 docker run -d --name nginx --memory="10m" --cpus="0.5" -p 80:80 ginx:alpine 
 docker ps 
 docker stats 
 docker logs
 docker stop nginx
 docker rm nginx 
```

### Construindo uma imagem docker 

#### Projeto Spring 

```bash
 mvn clean package
 docker build -f ./Dockerfile -t nonnemacher/lt-spring:latest .
 docker images | grep lt-spring
 docker run -d --name lt-spring --memory="128m" --cpus="1" -p 8080:8080 nonnemacher/lt-spring:latest
```

#### Projeto Angular

```bash 
 npm i && ng build
 docker build -f ./Dockerfile -t nonnemacher/lt-angular:latest .
 docker image | grep lt-angular
 docker run -d --name lt-spring --memory="10m" --cpus="0.5" -p 80:80 nonnemacher/lt-angular:latest
```

### Docker Compose

O compose é uma ferramenta do docker usada para criar infraestruturas de forma mais estruturada. (Ex. abaixo)

```bash
# docker-compose.yml
version: '2.2'
services:
  spring:
    image: 'nonnemacher/lt-spring:latest'
    ports:
     - '8080:8080'
    cpus: 1
    mem_limit: 128m
  angular:
    image: 'nonnemacher/lt-angular:latest'
    ports:
     - '80:80'
    cpus: 0.1
    mem_limit: 10m
```

### Comandos básicos

| Comando               | Descrição                             |
|-----------------------|---------------------------------------|
| `docker-compose up`   | Cria e inicia os recursos do compose  | 	
| `docker-compose down` | Apaga todos os recursos do compose    |
  
