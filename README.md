# gRPC Adder

Простой gRPC сервис для сложения двух чисел.

## Требования

- Go 1.16+
- protoc (Protocol Buffers compiler)
- protoc-gen-go
- protoc-gen-go-grpc

## Установка зависимостей

```bash
# Установка protoc-gen-go плагинов
go install google.golang.org/protobuf/cmd/protoc-gen-go@latest
go install google.golang.org/grpc/cmd/protoc-gen-go-grpc@latest

# Установка зависимостей проекта
go mod tidy
```

## Генерация кода из proto файлов

```bash
protoc -I api/proto \
  --go_out=pkg/api \
  --go_opt=paths=source_relative \
  --go-grpc_out=pkg/api \
  --go-grpc_opt=paths=source_relative \
  api/proto/adder.proto
```

## Запуск

### Сервер

```bash
go run cmd/server/main.go
```

### Клиент

```bash
go run cmd/client/main.go 5 3
```

Результат: `8`

## Структура проекта

```
.
├── api/proto/          # Proto файлы
├── pkg/
│   ├── api/           # Сгенерированный код
│   └── adder/         # Реализация сервиса
└── cmd/
    ├── server/        # Сервер
    └── client/        # Клиент
```
