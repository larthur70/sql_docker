# Comandos úteis do Docker

Este documento contém uma lista de comandos úteis para gerenciar contêineres e volumes do Docker.

## Deletar volumes - OBS! Os volumes nao podem estar sendo usados por nenhum Container ativo

Para remover volumes que não estão mais em uso, você pode usar o seguinte comando:

```bash
docker volume prune
```

Se você quiser remover um volume específico, utilize:

```bash
docker volume rm nome_do_volume
```

## Criar banco com novos volumes

Para criar um novo banco de dados com volumes persistentes, você pode usar um arquivo `docker-compose.yml`. Um exemplo básico seria:

```yaml
services:
  mysql:
    image: mysql:latest
    environment:
      MYSQL_ROOT_PASSWORD: rootpassword
      MYSQL_DATABASE: mydatabase
      MYSQL_USER: user
      MYSQL_PASSWORD: userpassword
    volumes:
      - mysql_data:/var/lib/mysql

volumes:
  mysql_data:
```

Salve este conteúdo em um arquivo chamado `docker-compose.yml` e execute:

```bash
docker-compose up -d
```

## Pausar Containers

Para pausar todos os contêineres em execução, use:

```bash
docker pause $(docker ps -q)
```

Para retomar os contêineres pausados:

```bash
docker unpause $(docker ps -q --filter "status=paused")
```

## Listar containers Rodando

Para listar todos os contêineres que estão atualmente em execução, utilize:

```bash
docker ps
```

Se você quiser listar todos os contêineres, incluindo os que estão parados:

```bash
docker ps -a
```

## Conclusão

Esses são alguns dos comandos básicos do Docker que podem ser úteis para gerenciar seus contêineres e volumes. Certifique-se de consultar a [documentação oficial do Docker](https://docs.docker.com/) para mais informações e recursos avançados.


# Comando para ver se algum processo esta usando a porta 3306

`sudo netstat -tuln | grep 3306`
