# Casos de Uso do Usuário

## USU01 - Cadastro

### Précondição
Nenhuma

### Ator
Usuário

### Fluxo de eventos

![Fluxo do caso USU01](./out/casos-de-uso/usuario/USU01/USU01.svg)

### Dados da requisição

| Campo             | Tipo   | Exemplo      |
|-------------------|--------|--------------|
| nome_completo     | String | Cleyson Lima |
| username          | String | cleysonph    |
| senha             | String | senha@123    |
| confirmacao_senha | String | senha@123    |

### Regras de validação

- `nome_completo`: não pode ser nulo
- `nome_completo`: não pode ser vazio
- `nome_completo`: não pode ter menos que 3 caracteres
- `nome_completo`: não pode ter mais que 100 caracteres
- `username`: não pode ser nulo
- `username`: não pode ser vazio
- `username`: não pode ter menos que 3 caracteres
- `username`: não pode ter mais que 100 caracteres
- `username`: deve ser único no banco de dados
- `senha`: não pode ser nulo
- `senha`: não pode ser vazio
- `senha`: não pode ter menos que 3 caracteres
- `senha`: não pode ter mais que 255 caracteres
- `confirmacao_senha`: não pode ser nulo
- `confirmacao_senha`: não pode ser vazio
- `confirmacao_senha`: não pode ter menos que 3 caracteres
- `confirmacao_senha`: não pode ter mais que 255 caracteres
- `confirmacao_senha`: deve ser igual ao campo `senha`

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

![Fluxo do caso USU02](./out/casos-de-uso/usuario/USU02/USU02.svg)

### Dados da requisição

| Campo             | Tipo   | Exemplo      |
|-------------------|--------|--------------|
| nome_completo     | String | Cleyson Lima |
| username          | String | cleysonph    |

### Regras de validação

- `nome_completo`: não pode ser nulo
- `nome_completo`: não pode ser vazio
- `nome_completo`: não pode ter menos que 3 caracteres
- `nome_completo`: não pode ter mais que 100 caracteres
- `username`: não pode ser nulo
- `username`: não pode ser vazio
- `username`: não pode ter menos que 3 caracteres
- `username`: não pode ter mais que 100 caracteres
- `username`: deve ser único no banco de dados

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

![Fluxo do caso USU03](./out/casos-de-uso/usuario/USU03/USU03.svg)

### Dados da requisição

| Campo                  | Tipo   | Exemplo    |
|------------------------|--------|------------|
| senha_atual            | string | senha@123  |
| nova_senha             | string | senha@1234 |
| confirmacao_nova_senha | string | senha@1234 |

### Regras de validação

- `senha_atual`: não pode ser nulo
- `senha_atual`: não pode ser vazio
- `senha_atual`: não pode ter menos que 3 caracteres
- `senha_atual`: não pode ter mais que 255 caracteres
- `senha_atual`: deve ser igual a senha atualmente cadastrada
- `nova_senha`: não pode ser nulo
- `nova_senha`: não pode ser vazio
- `nova_senha`: não pode ter menos que 3 caracteres
- `nova_senha`: não pode ter mais que 255 caracteres
- `confirmacao_nova_senha`: não pode ser nulo
- `confirmacao_nova_senha`: não pode ser vazio
- `confirmacao_nova_senha`: não pode ter menos que 3 caracteres
- `confirmacao_nova_senha`: não pode ter mais que 255 caracteres
- `confirmacao_nova_senha`: deve ser igual ao campo `nova_senha`

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

## USU04 - Autenticação

### Précondição
Nenhuma

### Ator
Usuário

### Fluxo de eventos

![Fluxo do caso USU04](./out/casos-de-uso/usuario/USU04/USU04.svg)

### Dados da requisição

| Campo    | Tipo   | Exemplo    |
|----------|--------|------------|
| username | string | cleysonph  |
| senha    | string | senha@123  |

### Regras de validação

- `username`: não pode ser nulo
- `username`: não pode ser vazio
- `username`: não pode ter menos que 3 caracteres
- `username`: não pode ter mais que 100 caracteres
- `username`: deve haver algum usuário cadastro com esse `username`
- `senha`: não pode ser nulo
- `senha`: não pode ser vazio
- `senha`: não pode ter menos que 3 caracteres
- `senha`: não pode ter mais que 255 caracteres
- `senha`: deve ser igual a senha atualmente cadastrada

### Dados da Resposta

| Campo   | Tipo   | Exemplo                                                                                                                                                                             |
|---------|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| access  | string | eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJjbGV5c29ucGgiLCJleHAiOjE2NDAzMjIyOTAsImlhdCI6MTY0MDMyMjI2MH0.Q0MjIR_ha7GvvuRNISE8Iez7q8sd3hXVSRGamB19nUeRMQfOCJj5YS9ZphdfNfCGi8o8kaJ-t4Zixi0Z3YwkAw |
| refresh | string | eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJjbGV5c29ucGgiLCJleHAiOjE2NDAzMjIzMjAsImlhdCI6MTY0MDMyMjI2MH0.mcVQlmImbniJQjmz0j7UTxfplISfPhsSTy7HUHezuQ8YB--ytEhLyTifZtbSEwHhcZ4IfhMWD9c-kZXu3mcUuw |

### Exemplo da requisição

```
POST /api/v1/auth/token HTTP/1.1
Host: localhost:8080
Content-Type: application/json
Accept: */*

{
  "username": "cleysonph",
  "senha": "senha@123"
}
```

### Exemplos de resposta

**Dados válidos**

```
HTTP/1.1 200
Content-Type: application/json

{
  "access": "eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJjbGV5c29ucGgiLCJleHAiOjE2NDAzMjIyOTAsImlhdCI6MTY0MDMyMjI2MH0.Q0MjIR_ha7GvvuRNISE8Iez7q8sd3hXVSRGamB19nUeRMQfOCJj5YS9ZphdfNfCGi8o8kaJ-t4Zixi0Z3YwkAw",
  "refresh": "eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJjbGV5c29ucGgiLCJleHAiOjE2NDAzMjIzMjAsImlhdCI6MTY0MDMyMjI2MH0.mcVQlmImbniJQjmz0j7UTxfplISfPhsSTy7HUHezuQ8YB--ytEhLyTifZtbSEwHhcZ4IfhMWD9c-kZXu3mcUuw"
}

```

**Dados inválidos**

```
HTTP/1.1 401
Content-Type: application/json

{
  "status": 401,
  "causa": "Unauthorized",
  "mensagem": "Bad credentials",
  "path": "/api/v1/auth/token",
  "timestamp": "2021-12-24T18:06:30.590583624",
  "erros": null
}
```

## USU05 - Reautenticação

### Précondição
Nenhuma

### Ator
Usuário

### Fluxo de eventos

![Fluxo do caso USU05](./out/casos-de-uso/usuario/USU05/USU05.svg)

### Dados da requisição

| Campo   | Tipo   | Exemplo                                                                                                                                                                             |
|---------|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| refresh | string | eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJjbGV5c29ucGgiLCJleHAiOjE2NDAwNTQxMDcsImlhdCI6MTY0MDA1NDA0N30.XIlbxniQ9Yswn8Xlxpw4T8etTBbuc7ydzN49zJFCbFn-_WCbZlOoqfqBL5kRCDynq_GaAfZtQpS6Khd2mhPAyA |

### Regras de validação

- `refresh`: não pode ser nulo
- `refresh`: não pode ser vazio
- `refresh`: deve ser um token válido

### Dados da Resposta

| Campo   | Tipo   | Exemplo                                                                                                                                                                             |
|---------|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| access  | string | eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJjbGV5c29ucGgiLCJleHAiOjE2NDAzMjIyOTAsImlhdCI6MTY0MDMyMjI2MH0.Q0MjIR_ha7GvvuRNISE8Iez7q8sd3hXVSRGamB19nUeRMQfOCJj5YS9ZphdfNfCGi8o8kaJ-t4Zixi0Z3YwkAw |
| refresh | string | eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJjbGV5c29ucGgiLCJleHAiOjE2NDAzMjIzMjAsImlhdCI6MTY0MDMyMjI2MH0.mcVQlmImbniJQjmz0j7UTxfplISfPhsSTy7HUHezuQ8YB--ytEhLyTifZtbSEwHhcZ4IfhMWD9c-kZXu3mcUuw |

### Exemplo da requisição

```
POST POST /api/v1/auth/refresh?token=eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJjbGV5c29ucGgiLCJleHAiOjE2NDAzODEwNTUsImlhdCI6MTY0MDM4MDk5NX0.hCk9QAjEJk2WlUyYS4854GQAydw3TqHiC1yHdJbuGMSTmS9lcn96aP8tmyny6KuiokEvzSPqGj3fovRRHLw2Jw HTTP/1.1
Host: localhost:8080
Accept: */*
```

### Exemplos de resposta

**Refresh token válido**

```
HTTP/1.1 200
Content-Type: application/json

{
  "access": "eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJjbGV5c29ucGgiLCJleHAiOjE2NDAzMjIyOTAsImlhdCI6MTY0MDMyMjI2MH0.Q0MjIR_ha7GvvuRNISE8Iez7q8sd3hXVSRGamB19nUeRMQfOCJj5YS9ZphdfNfCGi8o8kaJ-t4Zixi0Z3YwkAw",
  "refresh": "eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJjbGV5c29ucGgiLCJleHAiOjE2NDAzMjIzMjAsImlhdCI6MTY0MDMyMjI2MH0.mcVQlmImbniJQjmz0j7UTxfplISfPhsSTy7HUHezuQ8YB--ytEhLyTifZtbSEwHhcZ4IfhMWD9c-kZXu3mcUuw"
}

```

**Refresh token inválido**

```
HTTP/1.1 401
Content-Type: application/json

{
  "status": 401,
  "causa": "Unauthorized",
  "mensagem": "JWT strings must contain exactly 2 period characters. Found: 0",
  "path": "/api/v1/auth/refresh",
  "timestamp": "2021-12-24T18:24:18.983353607",
  "erros": null
}
```

**Refresh token não enviado**

```
HTTP/1.1 400
Content-Type: application/json

{
  "status": 400,
  "causa": "Bad Request",
  "mensagem": "Required request parameter 'token' for method parameter type String is not present",
  "path": "/api/v1/auth/refresh",
  "timestamp": "2021-12-24T18:39:19.011115333",
  "erros": null
}
```