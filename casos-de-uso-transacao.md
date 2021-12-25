# Casos de Uso da Transação

## TRA01 - Cadastrar transação

### Précondição
Usuário deve estar logado

### Ator
Usuário

### Fluxo de eventos

![Fluxo do caso TRA01](./out/casos-de-uso/transacao/TRA01/TRA01.svg)

### Dados da requisição

| Campo     | Tipo   | Exemplo                 |
|-----------|--------|-------------------------|
| nome      | string | Academia                |
| descricao | string | Mensalidade da academia |
| valor     | number | 89.90                   |
| tipo      | string | SAIDA                   |
| data      | string | 2021-12-20              |
| conta     | number | 1                       |

### Regras de validação

- `nome`: não pode ser nulo
- `nome`: não pode ser vazio
- `nome`: não pode ter menos que 3 caracteres
- `nome`: não pode ter mais que 100 caracteres
- `descricao`: não pode ser nulo
- `descricao`: não pode ser vazio
- `descricao`: não pode ter menos que 3 caracteres
- `descricao`: não pode ter mais que 255 caracteres
- `valor`: não pode ser nulo
- `valor`: deve ser positivo
- `tipo`: não pode ser nulo
- `tipo`: não pode ser vazio
- `tipo`: deve ser correspondente aos valores "SAIDA" ou "ENTRADA"
- `data`: não pode ser nulo
- `data`: não pode ser vazio
- `data`: não pode ser uma data no futuro
- `conta`: não pode ser nulo
- `conta`: não pode ser vazio
- `conta`: deve corresponder ao `id` de uma conta cadastrada
- `conta`: deve corresponder ao `id` de uma conta cadastrada pelo usuário logado

### Dados da Resposta

| Campo         | Tipo   | Exemplo                       |
|---------------|--------|-------------------------------|
| id            | number | 1                             |
| nome          | string | TreinaWeb                     |
| tipo          | string | SAIDA                         |
| descricao     | string | Assinatura anual da TreinaWeb |
| data          | string | 2021-12-20                    |
| valor         | number | 804.00                        |
| conta         | number | 1                             |
| criado_em     | string | 2021-12-24T01:41:36.556174143 |
| atualizado_em | string | 2021-12-24T01:41:36.556174143 |

### Exemplo da requisição

```
POST /api/v1/transacoes HTTP/1.1
Host: localhost:8080
Content-Type: application/json
Authorization: Bearer eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJjbGV5c29ucGgiLCJleHAiOjE2NDAzODI1NTUsImlhdCI6MTY0MDM4MjUyNX0.nbv6jkRJkbVdC-YQLvgP5gjENJIX2EZ-tHt9uELiiRe3ivkS5w-C_smbSyKcTRm9jtBEXGxTl0-tfKyVIKBHJQ
Accept: */*

{
  "nome": "Academia",
  "descricao": "Mensalidade da academia"
  "valor": 89.90,
  "tipo": "SAIDA",
  "data": "2021-12-20",
  "conta": 1
}
```

### Exemplos de resposta

**Dados válidos**

```
HTTP/1.1 201
Content-Type: application/json

{
  "id": 1,
  "nome": "Academia",
  "tipo": "SAIDA",
  "descricao": "Mensalidade da academia"
  "data": "2021-12-20",
  "valor": 89.90,
  "criado_em": "2021-12-21T15:14:34.367856319",
  "atualizado_em": "2021-12-21T15:14:34.367856319"
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
  "path": "/api/v1/transacoes",
  "timestamp": "2021-12-25T17:24:14.272889423",
  "erros": {
    "data": [
      "must be a date in the past or in the present"
    ],
    "conta": [
      "Conta com id 1 não existe"
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
  "path": "/api/v1/transacoes",
  "timestamp": "2021-12-24T18:48:12.568403848",
  "erros": null
}
```

**Usuário logado não é dono da conta**

```
HTTP/1.1 403
Content-Type: application/json

{
  "status": 403,
  "causa": "Forbidden",
  "mensagem": "Usuário logado não é dono da conta",
  "path": "/api/v1/transacoes",
  "timestamp": "2021-12-25T17:25:16.394201335",
  "erros": null
}
```