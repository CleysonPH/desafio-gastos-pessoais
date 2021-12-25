# Casos de Uso da Conta

## CON01 - Cadastrar conta

### Précondição
Usuário deve estar logado

### Ator
Usuário

### Fluxo de eventos

![Fluxo do caso CON01](./out/casos-de-uso/conta/CON01/CON01.svg)

### Dados da requisição

| Campo     | Tipo   | Exemplo                  |
|-----------|--------|--------------------------|
| nome      | String | Nubank                   |
| descricao | String | Conta do banco Nubank    |

### Regras de validação

- `nome`: não pode ser nulo
- `nome`: não pode ser vazio
- `nome`: não pode ter menos que 3 caracteres
- `nome`: não pode ter mais que 100 caracteres
- `descricao`: não pode ser nulo
- `descricao`: não pode ser vazio
- `descricao`: não pode ter menos que 3 caracteres
- `descricao`: não pode ter mais que 255 caracteres

### Dados da Resposta

| Campo         | Tipo   | Exemplo                       |
|---------------|--------|-------------------------------|
| id            | number | 1                             |
| nome          | string | Nubank                        |
| descricao     | string | Conta do banco Nubank         |
| criado_em     | string | 2021-12-24T01:41:36.556174143 |
| atualizado_em | string | 2021-12-24T01:41:36.556174143 |

### Exemplo da requisição

```
POST /api/v1/contas HTTP/1.1
Host: localhost:8080
Content-Type: application/json
Authorization: Bearer eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJjbGV5c29ucGgiLCJleHAiOjE2NDAzODI1NTUsImlhdCI6MTY0MDM4MjUyNX0.nbv6jkRJkbVdC-YQLvgP5gjENJIX2EZ-tHt9uELiiRe3ivkS5w-C_smbSyKcTRm9jtBEXGxTl0-tfKyVIKBHJQ
Accept: */*

{
  "nome": "Nubank",
  "descricao": "Conta do banco Nubank"
}
```

### Exemplos de resposta

**Dados válidos**

```
HTTP/1.1 201
Content-Type: application/json

{
  "id": 1,
  "nome": "Nubank",
  "descricao": "Conta do banco Nubank",
  "criadoEm": "2021-12-21T15:14:06.413402655",
  "atualizadoEm": "2021-12-21T15:14:06.413402655",
}

```

**Dados inválidos**

```
HTTP/1.1 400
Content-Type: application/json

{
  "status": 400,
  "causa": "Bad Request",
  "mensagem": "Houveram um ou mais erros de validação",
  "path": "/api/v1/contas",
  "timestamp": "2021-12-24T18:47:43.683494732",
  "erros": {
    "nome": [
      "size must be between 3 and 100"
    ]
  }
}
```

**Usuário não autenticado**

```
HTTP/1.1 401
Content-Type: application/json

{
  "status": 401,
  "causa": "Unauthorized",
  "mensagem": "Full authentication is required to access this resource",
  "path": "/api/v1/contas",
  "timestamp": "2021-12-24T18:48:12.568403848",
  "erros": null
}
```

## CON02 - Listar contas

### Précondição
Usuário deve estar logado

### Ator
Usuário

### Fluxo de eventos

![Fluxo do caso CON02](./out/casos-de-uso/conta/CON02/CON02.svg)

### Dados da requisição
Não se aplica

### Regras de validação
Não se aplica

### Dados da Resposta

Lista das contas cadastradas pelo usuário logado.

Dados de uma conta:
| Campo         | Tipo   | Exemplo                       |
|---------------|--------|-------------------------------|
| id            | number | 1                             |
| nome          | string | Nubank                        |
| descricao     | string | Conta do banco Nubank         |
| criado_em     | string | 2021-12-24T01:41:36.556174143 |
| atualizado_em | string | 2021-12-24T01:41:36.556174143 |

### Exemplo da requisição

```
GET /api/v1/contas HTTP/1.1
Host: localhost:8080
Authorization: Bearer eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJjbGV5c29ucGgiLCJleHAiOjE2NDAzODI1NTUsImlhdCI6MTY0MDM4MjUyNX0.nbv6jkRJkbVdC-YQLvgP5gjENJIX2EZ-tHt9uELiiRe3ivkS5w-C_smbSyKcTRm9jtBEXGxTl0-tfKyVIKBHJQ
Accept: */*
```

### Exemplos de resposta

**Usuário autenticado**

```
HTTP/1.1 200
Content-Type: application/json

[
  {
    "id": 1,
    "nome": "Nubank",
    "descricao": "Conta do banco Nubank",
    "criadoEm": "2021-12-21T15:14:06.413402655",
    "atualizadoEm": "2021-12-21T15:14:06.413402655",
  },
  {
    "id": 2,
    "nome": "Santander",
    "descricao": "Conta do banco Santander",
    "criadoEm": "2021-12-22T15:14:06.413402655",
    "atualizadoEm": "2021-12-22T15:14:06.413402655",
  }
]

```

**Usuário não autenticado**

```
HTTP/1.1 401
Content-Type: application/json

{
  "status": 401,
  "causa": "Unauthorized",
  "mensagem": "Full authentication is required to access this resource",
  "path": "/api/v1/contas",
  "timestamp": "2021-12-24T18:48:12.568403848",
  "erros": null
}
```

## CON03 - Detalhes da conta

### Précondição
Usuário deve estar logado

### Ator
Usuário

### Fluxo de eventos

![Fluxo do caso CON03](./out/casos-de-uso/conta/CON03/CON03.svg)

### Dados da requisição
Não se aplica

### Regras de validação
Não se aplica

### Dados da Resposta

| Campo         | Tipo   | Exemplo                       |
|---------------|--------|-------------------------------|
| id            | number | 1                             |
| nome          | string | Nubank                        |
| descricao     | string | Conta do banco Nubank         |
| criado_em     | string | 2021-12-24T01:41:36.556174143 |
| atualizado_em | string | 2021-12-24T01:41:36.556174143 |

### Exemplo da requisição

```
GET /api/v1/contas/1 HTTP/1.1
Host: localhost:8080
Authorization: Bearer eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJjbGV5c29ucGgiLCJleHAiOjE2NDAzODI1NTUsImlhdCI6MTY0MDM4MjUyNX0.nbv6jkRJkbVdC-YQLvgP5gjENJIX2EZ-tHt9uELiiRe3ivkS5w-C_smbSyKcTRm9jtBEXGxTl0-tfKyVIKBHJQ
Accept: */*
```

### Exemplos de resposta

**Usuário dono da conta**

```
HTTP/1.1 200
Content-Type: application/json


{
  "id": 1,
  "nome": "Nubank",
  "descricao": "Conta do banco Nubank",
  "criadoEm": "2021-12-21T15:14:06.413402655",
  "atualizadoEm": "2021-12-21T15:14:06.413402655",
}
```

**Usuário não autenticado**

```
HTTP/1.1 401
Content-Type: application/json

{
  "status": 401,
  "causa": "Unauthorized",
  "mensagem": "Full authentication is required to access this resource",
  "path": "/api/v1/contas/1",
  "timestamp": "2021-12-24T18:48:12.568403848",
  "erros": null
}
```

**Usuário não é dono da conta**

```
HTTP/1.1 403
Content-Type: application/json

{
  "status": 403,
  "causa": "Forbidden",
  "mensagem": "Usuário logado não é dono da conta",
  "path": "/api/v1/contas/1",
  "timestamp": "2021-12-24T19:11:32.627959138",
  "erros": null
}
```

**Conta não existente**

```
HTTP/1.1 404
Content-Type: application/json

{
  "status": 404,
  "causa": "Not Found",
  "mensagem": "Conta não encontrada",
  "path": "/api/v1/contas/1",
  "timestamp": "2021-12-24T19:13:24.097714655",
  "erros": null
}
```

## CON04 - Alterar dados da conta

### Précondição
Usuário deve estar logado

### Ator
Usuário

### Fluxo de eventos

![Fluxo do caso CON04](./out/casos-de-uso/conta/CON04/CON04.svg)

| Campo     | Tipo   | Exemplo                  |
|-----------|--------|--------------------------|
| nome      | String | Nubank                   |
| descricao | String | Conta do banco Nubank    |

### Regras de validação

- `nome`: não pode ser nulo
- `nome`: não pode ser vazio
- `nome`: não pode ter menos que 3 caracteres
- `nome`: não pode ter mais que 100 caracteres
- `descricao`: não pode ser nulo
- `descricao`: não pode ser vazio
- `descricao`: não pode ter menos que 3 caracteres
- `descricao`: não pode ter mais que 255 caracteres

### Dados da Resposta

| Campo         | Tipo   | Exemplo                       |
|---------------|--------|-------------------------------|
| id            | number | 1                             |
| nome          | string | Nubank                        |
| descricao     | string | Conta do banco Nubank         |
| criado_em     | string | 2021-12-24T01:41:36.556174143 |
| atualizado_em | string | 2021-12-24T01:41:36.556174143 |

### Exemplo da requisição

```
PUT /api/v1/contas/3 HTTP/1.1
Host: localhost:8080
Content-Type: application/json
Authorization: Bearer eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJjbGV5c29ucGgiLCJleHAiOjE2NDAzODI1NTUsImlhdCI6MTY0MDM4MjUyNX0.nbv6jkRJkbVdC-YQLvgP5gjENJIX2EZ-tHt9uELiiRe3ivkS5w-C_smbSyKcTRm9jtBEXGxTl0-tfKyVIKBHJQ
Accept: */*

{
	"nome": "Nubank",
	"descricao": "Conta do banco Nubank"
}
```

### Exemplos de resposta

**Usuário dono da conta**

```
HTTP/1.1 200
Content-Type: application/json


{
  "id": 1,
  "nome": "Nubank",
  "descricao": "Conta do banco Nubank",
  "criadoEm": "2021-12-21T15:14:06.413402655",
  "atualizadoEm": "2021-12-21T15:14:06.413402655",
}
```

**Dados inválidos**

```
HTTP/1.1 400
Content-Type: application/json

{
  "status": 400,
  "causa": "Bad Request",
  "mensagem": "Houveram um ou mais erros de validação",
  "path": "/api/v1/contas/1",
  "timestamp": "2021-12-24T18:47:43.683494732",
  "erros": {
    "nome": [
      "size must be between 3 and 100"
    ]
  }
}
```

**Usuário não autenticado**

```
HTTP/1.1 401
Content-Type: application/json

{
  "status": 401,
  "causa": "Unauthorized",
  "mensagem": "Full authentication is required to access this resource",
  "path": "/api/v1/contas/1",
  "timestamp": "2021-12-24T18:48:12.568403848",
  "erros": null
}
```

**Usuário não é dono da conta**

```
HTTP/1.1 403
Content-Type: application/json

{
  "status": 403,
  "causa": "Forbidden",
  "mensagem": "Usuário logado não é dono da conta",
  "path": "/api/v1/contas/1",
  "timestamp": "2021-12-24T19:11:32.627959138",
  "erros": null
}
```

**Conta não existente**

```
HTTP/1.1 404
Content-Type: application/json

{
  "status": 404,
  "causa": "Not Found",
  "mensagem": "Conta não encontrada",
  "path": "/api/v1/contas/1",
  "timestamp": "2021-12-24T19:13:24.097714655",
  "erros": null
}
```

## CON05 - Excluir conta

### Précondição
Usuário deve estar logado

### Ator
Usuário

### Fluxo de eventos

![Fluxo do caso CON05](./out/casos-de-uso/conta/CON05/CON05.svg)

### Dados da requisição
Não se aplica

### Regras de validação
Não se aplica

### Dados da Resposta
Não se aplica

### Exemplo da requisição

```
DELETE /api/v1/contas/1 HTTP/1.1
Host: localhost:8080
Authorization: Bearer eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJjbGV5c29ucGgiLCJleHAiOjE2NDAzODI1NTUsImlhdCI6MTY0MDM4MjUyNX0.nbv6jkRJkbVdC-YQLvgP5gjENJIX2EZ-tHt9uELiiRe3ivkS5w-C_smbSyKcTRm9jtBEXGxTl0-tfKyVIKBHJQ
Accept: */*
```

### Exemplos de resposta

**Usuário dono da conta**

```
HTTP/1.1 204
Content-Type: application/json
```

**Usuário não autenticado**

```
HTTP/1.1 401
Content-Type: application/json

{
  "status": 401,
  "causa": "Unauthorized",
  "mensagem": "Full authentication is required to access this resource",
  "path": "/api/v1/contas/1",
  "timestamp": "2021-12-24T18:48:12.568403848",
  "erros": null
}
```

**Usuário não é dono da conta**

```
HTTP/1.1 403
Content-Type: application/json

{
  "status": 403,
  "causa": "Forbidden",
  "mensagem": "Usuário logado não é dono da conta",
  "path": "/api/v1/contas/1",
  "timestamp": "2021-12-24T19:11:32.627959138",
  "erros": null
}
```

**Conta não existente**

```
HTTP/1.1 404
Content-Type: application/json

{
  "status": 404,
  "causa": "Not Found",
  "mensagem": "Conta não encontrada",
  "path": "/api/v1/contas/1",
  "timestamp": "2021-12-24T19:13:24.097714655",
  "erros": null
}
```

## CON06 - Calcular saldo

### Précondição
Usuário deve estar logado

### Ator
Usuário

### Fluxo de eventos

![Fluxo do caso CON06](./out/casos-de-uso/conta/CON06/CON06.svg)

### Dados da requisição
Não se aplica

### Regras de validação
Não se aplica

### Dados da Resposta
| Campo | Tipo   | Exemplo |
|-------|--------|---------|
| saldo | number | 100.50  |

### Exemplo da requisição

```
GET /api/v1/contas/1/saldo HTTP/1.1
Host: localhost:8080
Authorization: Bearer eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJjbGV5c29ucGgiLCJleHAiOjE2NDAzODI1NTUsImlhdCI6MTY0MDM4MjUyNX0.nbv6jkRJkbVdC-YQLvgP5gjENJIX2EZ-tHt9uELiiRe3ivkS5w-C_smbSyKcTRm9jtBEXGxTl0-tfKyVIKBHJQ
Accept: */*
```

### Exemplos de resposta

**Usuário dono da conta**

```
HTTP/1.1 200
Content-Type: application/json

{
  "saldo": 100.50
}
```

**Usuário não autenticado**

```
HTTP/1.1 401
Content-Type: application/json

{
  "status": 401,
  "causa": "Unauthorized",
  "mensagem": "Full authentication is required to access this resource",
  "path": "/api/v1/contas/1/saldo",
  "timestamp": "2021-12-24T18:48:12.568403848",
  "erros": null
}
```

**Usuário não é dono da conta**

```
HTTP/1.1 403
Content-Type: application/json

{
  "status": 403,
  "causa": "Forbidden",
  "mensagem": "Usuário logado não é dono da conta",
  "path": "/api/v1/contas/1/saldo",
  "timestamp": "2021-12-24T19:11:32.627959138",
  "erros": null
}
```

**Conta não existente**

```
HTTP/1.1 404
Content-Type: application/json

{
  "status": 404,
  "causa": "Not Found",
  "mensagem": "Conta não encontrada",
  "path": "/api/v1/contas/1/saldo",
  "timestamp": "2021-12-24T19:13:24.097714655",
  "erros": null
}
```