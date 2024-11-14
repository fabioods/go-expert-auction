# Projeto de Leilão - Lab Go Expert

Este sistema permite criar leilões, fazer lances e verificar o vencedor. Como diferencial, foi implementada a funcionalidade de fechamento automático dos leilões após um tempo especificado.

---

## Índice
- [Pré-requisitos](#pré-requisitos)
- [Configuração do Ambiente](#configuração-do-ambiente)
- [Construção e Execução](#construção-e-execução)
   - [Usando Docker Compose](#usando-docker-compose)
- [Endpoints da API](#endpoints-da-api)
- [Execução dos Testes](#execução-dos-testes)

---

## Pré-requisitos

- Docker
- Docker Compose

---

## Configuração do Ambiente

No arquivo `.env` no diretório `cmd/auction/` temos o tempo em minutos sendo definido pela variável `AUCTION_DURATION_MINUTES` para fechamento automático dos leilões:

```env
AUCTION_DURATION_MINUTES=1
```

Isso vale para execução local e para os testes. Para o caso de usar o docker-compose, o arquivo `docker-compose.yaml` já está configurado para usar o valor definido no `.env`.

---

## Construção e Execução

### Usando Docker Compose

1. **Build e start dos serviços**:

    ```sh
    docker-compose up --build
    ```

2. **Executar os testes** (em um novo terminal):

    ```sh
    docker-compose exec auction-app go test ./tests -v
    ```

3. **Parar os serviços**:

    ```sh
    docker-compose down
    ```

---

## Endpoints da API

A aplicação oferece os seguintes endpoints:

### Leilões
- `GET /auction`: Lista todos os leilões.
- `GET /auction/:auctionId`: Busca um leilão pelo ID.
- `POST /auction`: Cria um novo leilão.
- `GET /auction/winner/:auctionId`: Busca o lance vencedor de um leilão pelo ID.

### Lances
- `POST /bid`: Cria um novo lance.
- `GET /bid/:auctionId`: Lista todos os lances de um leilão.

### Usuários
- `GET /user/:userId`: Busca um usuário pelo ID.

---

## Execução dos Testes

Para rodar os testes de fechamento automático de leilões:

1. Certifique-se de que o MongoDB esteja em execução na sua máquina.
2. Execute:

    ```sh
    go test ./tests -v
    ```

Esses testes verificam o correto funcionamento da funcionalidade de fechamento automático dos leilões.

