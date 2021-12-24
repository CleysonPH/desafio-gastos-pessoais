# Casos de Uso

## USU01 - Cadastro

### Précondição
Nenhuma

### Ator
Usuário

### Fluxo de eventos

![Fluxo do caso USU01](./out/casos-de-uso/USU01/USU01.svg)

### Dados da requisição

| Campo             | Tipo   | Exemplo      |
|-------------------|--------|--------------|
| nome_completo     | String | Cleyson Lima |
| username          | String | cleysonph    |
| senha             | String | senha@123    |
| confirmacao_senha | String | senha@123    |

### Regras de validação

- `nome_completo` não pode ser nulo
- `nome_completo` não pode ser vazio
- `nome_completo` não pode ter menos que 3 caracteres
- `nome_completo` não pode ter mais que 100 caracteres
- `username` não pode ser nulo
- `username` não pode ser vazio
- `username` não pode ter menos que 3 caracteres
- `username` não pode ter mais que 100 caracteres
- `username` deve ser único no banco de dados
- `senha` não pode ser nulo
- `senha` não pode ser vazio
- `senha` não pode ter menos que 3 caracteres
- `senha` não pode ter mais que 255 caracteres
- `confirmacao_senha` não pode ser nulo
- `confirmacao_senha` não pode ser vazio
- `confirmacao_senha` não pode ter menos que 3 caracteres
- `confirmacao_senha` não pode ter mais que 255 caracteres
- `confirmacao_senha` deve ser igual ao campo `senha`

### Dados da Resposta

| Campo         | Tipo   | Exemplo                                |
|---------------|--------|----------------------------------------|
| id            | number | 1                                      |
| nome_completo | string | Cleyson Lima                           |
| username      | string | cleysonph                              |
| criado_em     | string | 2021-12-24T01:41:36.556174143          |
| atualizado_em | string | 2021-12-24T01:41:36.556174143          |

### Exemplo da requisição

```
POST /api/v1/usuarios HTTP/1.1
Host: localhost:8080
Content-Type: application/json
Accept: */*

{
  "nome_completo": "Cleyson Lima",
  "username": "cleysonph",
  "senha": "senha@123",
  "confirmacao_senha": "senha@123"
}
```

### Exemplos de resposta

**Dados válidos**

```
HTTP/1.1 201
Content-Type: application/json

{
  "id": 1,
  "nome_completo": "Cleyson Lima",
  "username": "cleysonph",
  "criado_em": "2021-12-24T01:41:36.556174143",
  "atualizado_em": "2021-12-24T01:41:36.556174143",
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
  "path": "/api/v1/usuarios",
  "timestamp": "2021-12-24T01:43:34.529720027",
  "erros": {
    "nome_completo": [
      "não deve estar vazio",
      "não deve ser nulo"
    ],
    "username": [
      "username já cadastrado"
    ]
  }
}
```

## USU02 - Alteração de dados pessoais

### Précondição
Usuário deve estar logado

### Ator
Usuário

### Fluxo de eventos

![Fluxo do caso USU02](./out/casos-de-uso/USU02/USU02.svg)

### Dados da requisição

| Campo             | Tipo   | Exemplo      |
|-------------------|--------|--------------|
| nome_completo     | String | Cleyson Lima |
| username          | String | cleysonph    |

### Regras de validação

- `nome_completo` não pode ser nulo
- `nome_completo` não pode ser vazio
- `nome_completo` não pode ter menos que 3 caracteres
- `nome_completo` não pode ter mais que 100 caracteres
- `username` não pode ser nulo
- `username` não pode ser vazio
- `username` não pode ter menos que 3 caracteres
- `username` não pode ter mais que 100 caracteres
- `username` deve ser único no banco de dados

### Dados da Resposta

| Campo         | Tipo   | Exemplo                                |
|---------------|--------|----------------------------------------|
| id            | number | 1                                      |
| nome_completo | string | Cleyson Lima                           |
| username      | string | cleysonph                              |
| criado_em     | string | 2021-12-24T01:41:36.556174143          |
| atualizado_em | string | 2021-12-24T01:41:36.556174143          |

### Exemplo da requisição

```
PUT /api/v1/me/ HTTP/1.1
Host: localhost:8080
Content-Type: application/json
Authorization: Bearer eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJjbGV5c29ucGgiLCJleHAiOjE2NDAzMjIyOTAsImlhdCI6MTY0MDMyMjI2MH0.Q0MjIR_ha7GvvuRNISE8Iez7q8sd3hXVSRGamB19nUeRMQfOCJj5YS9ZphdfNfCGi8o8kaJ-t4Zixi0Z3YwkAw
Accept: */*

{
  "nome_completo": "Cleyson Lima",
  "username": "cleysonph",
}
```

### Exemplos de resposta

**Dados válidos**

```
HTTP/1.1 201
Content-Type: application/json

{
  "id": 1,
  "nome_completo": "Cleyson Lima",
  "username": "cleysonph",
  "criado_em": "2021-12-24T01:41:36.556174143",
  "atualizado_em": "2021-12-24T01:41:36.556174143",
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
  "path": "/api/v1/usuarios",
  "timestamp": "2021-12-24T01:43:34.529720027",
  "erros": {
    "nome_completo": [
      "não deve estar vazio",
      "não deve ser nulo"
    ],
    "username": [
      "username já cadastrado"
    ]
  }
}
```

**Sem token de autenticação**

```
HTTP/1.1 401
Content-Type: application/json

{
  "status": 401,
  "causa": "Unauthorized",
  "mensagem": "Full authentication is required to access this resource",
  "path": "/api/v1/contas",
  "timestamp": "2021-12-24T02:05:13.550486877",
  "erros": null
}
```

**Token inválido**
```
HTTP/1.1 401
Content-Type: application/json

{
  "status": 401,
  "causa": "Unauthorized",
  "mensagem": "JWT expired at 2021-12-24T02:04:50Z. Current time: 2021-12-24T02:06:39Z, a difference of 109143 milliseconds.  Allowed clock skew: 0 milliseconds.",
  "path": "/api/v1/contas",
  "timestamp": "2021-12-24T02:06:39.144015887",
  "erros": null
}
```

## USU03 - Alteração de senha

### Précondição
Usuário deve estar logado

### Ator
Usuário

### Fluxo de eventos

![Fluxo do caso USU03](./out/casos-de-uso/USU03/USU03.svg)

### Dados da requisição

| Campo                  | Tipo   | Exemplo    |
|------------------------|--------|------------|
| senha_atual            | string | senha@123  |
| nova_senha             | string | senha@1234 |
| confirmacao_nova_senha | string | senha@1234 |

### Regras de validação

- `senha_atual` não pode ser nulo
- `senha_atual` não pode ser vazio
- `senha_atual` não pode ter menos que 3 caracteres
- `senha_atual` não pode ter mais que 255 caracteres
- `senha_atual` deve ser igual a senha atualmente cadastrada
- `nova_senha` não pode ser nulo
- `nova_senha` não pode ser vazio
- `nova_senha` não pode ter menos que 3 caracteres
- `nova_senha` não pode ter mais que 255 caracteres
- `confirmacao_nova_senha` não pode ser nulo
- `confirmacao_nova_senha` não pode ser vazio
- `confirmacao_nova_senha` não pode ter menos que 3 caracteres
- `confirmacao_nova_senha` não pode ter mais que 255 caracteres
- `confirmacao_nova_senha` deve ser igual ao campo `nova_senha`

### Dados da Resposta

| Campo         | Tipo   | Exemplo                                |
|---------------|--------|----------------------------------------|
| id            | number | 1                                      |
| nome_completo | string | Cleyson Lima                           |
| username      | string | cleysonph                              |
| criado_em     | string | 2021-12-24T01:41:36.556174143          |
| atualizado_em | string | 2021-12-24T01:41:36.556174143          |

### Exemplo da requisição

```
PUT /api/v1/me/atualizar-senha HTTP/1.1
Host: localhost:8080
Content-Type: application/json
Authorization: Bearer eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJjbGV5c29ucGgiLCJleHAiOjE2NDAzMjIyOTAsImlhdCI6MTY0MDMyMjI2MH0.Q0MjIR_ha7GvvuRNISE8Iez7q8sd3hXVSRGamB19nUeRMQfOCJj5YS9ZphdfNfCGi8o8kaJ-t4Zixi0Z3YwkAw
Accept: */*

{
  "senha_atual": "senha@123",
  "nova_senha": "senha@1234",
  "confirmacao_nova_senha": "senha@123"
}
```

### Exemplos de resposta

**Dados válidos**

```
HTTP/1.1 201
Content-Type: application/json

{
  "mensagem": "senha atualizada com sucesso"
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
  "path": "/api/v1/usuarios",
  "timestamp": "2021-12-24T01:43:34.529720027",
  "erros": {
    "senha": [
      "a senha informada está incorreta"
    ],
    "confirmacao_nova_senha": [
      "senha de confirmação diferente da senha informada"
    ]
  }
}
```

**Sem token de autenticação**

```
HTTP/1.1 401
Content-Type: application/json

{
  "status": 401,
  "causa": "Unauthorized",
  "mensagem": "Full authentication is required to access this resource",
  "path": "/api/v1/contas",
  "timestamp": "2021-12-24T02:05:13.550486877",
  "erros": null
}
```

**Token inválido**
```
HTTP/1.1 401
Content-Type: application/json

{
  "status": 401,
  "causa": "Unauthorized",
  "mensagem": "JWT expired at 2021-12-24T02:04:50Z. Current time: 2021-12-24T02:06:39Z, a difference of 109143 milliseconds.  Allowed clock skew: 0 milliseconds.",
  "path": "/api/v1/contas",
  "timestamp": "2021-12-24T02:06:39.144015887",
  "erros": null
}
```