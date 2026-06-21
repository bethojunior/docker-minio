# MinIO — Local S3

MinIO rodando localmente via Docker com bucket pré-configurado.

## Requisitos

- Docker + Docker Compose

## Setup

```bash
cp .env.example .env
# edite .env se quiser mudar credenciais ou portas
docker compose up -d
```

O serviço `mc` sobe automaticamente, aguarda o MinIO ficar saudável e cria o bucket. Após isso, apenas o MinIO continua rodando.

## Acessos

| Serviço       | URL                        |
|---------------|----------------------------|
| API (S3)      | http://localhost:9000      |
| Console (UI)  | http://localhost:9001      |

## Variáveis de ambiente

| Variável              | Padrão         | Descrição                        |
|-----------------------|----------------|----------------------------------|
| `MINIO_ROOT_USER`     | `minioadmin`   | Usuário root                     |
| `MINIO_ROOT_PASSWORD` | `minioadmin`   | Senha root                       |
| `MINIO_API_PORT`      | `9000`         | Porta da API S3                  |
| `MINIO_CONSOLE_PORT`  | `9001`         | Porta do console web             |
| `S3_BUCKET_NAME`      | `dev-bucket`   | Bucket criado automaticamente    |
| `S3_REGION`           | `us-east-1`    | Região (informativa para clientes S3) |
| `S3_ENDPOINT`         | `http://localhost:9000` | Endpoint para SDKs S3   |

## Uso em aplicações

Configure seu SDK S3 com as variáveis do `.env`:

```env
S3_ENDPOINT=http://localhost:9000
S3_REGION=us-east-1
S3_ACCESS_KEY_ID=minioadmin
S3_SECRET_ACCESS_KEY=minioadmin
S3_BUCKET_NAME=dev-bucket
```

## Comandos úteis

```bash
# subir
docker compose up -d

# parar
docker compose down

# remover dados também
docker compose down -v

# ver logs
docker compose logs -f minio
```
