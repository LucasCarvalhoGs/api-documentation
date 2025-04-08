# **Documentação da API - Task Manager**

A API do **Task Manager** permite que você crie, leia, atualize e exclua tarefas no sistema. Ela segue o padrão REST e utiliza o formato de resposta JSON.

Base URL: `https://api.taskmanager.com/v1`

---

## **Autenticação**

A autenticação é feita através de um token de autenticação no cabeçalho das requisições. O token pode ser gerado ao realizar o login com suas credenciais.

**Exemplo de autenticação:**

```http
Authorization: Bearer <TOKEN_AQUI>
```

---

## **Recursos da API**

### 1. **Listar Tarefas**
**GET /tasks**

Retorna uma lista de todas as tarefas cadastradas no sistema.

#### Parâmetros:
- `status` (opcional): Filtro para buscar tarefas por status (ex: "pendente", "concluída").
- `due_date` (opcional): Filtro para buscar tarefas com data de vencimento específica.

**Exemplo de Requisição:**
```http
GET /tasks?status=pendente&due_date=2025-04-10
```

**Exemplo de Resposta:**
```json
[
  {
    "id": 1,
    "title": "Comprar mantimentos",
    "description": "Ir ao mercado para comprar alimentos.",
    "status": "pendente",
    "due_date": "2025-04-10"
  },
  {
    "id": 2,
    "title": "Estudar para a prova",
    "description": "Revisar os conteúdos de matemática para a prova de amanhã.",
    "status": "pendente",
    "due_date": "2025-04-09"
  }
]
```

---

### 2. **Criar Tarefa**
**POST /tasks**

Cria uma nova tarefa no sistema.

#### Corpo da Requisição:
```json
{
  "title": "Estudar para a prova",
  "description": "Revisar os tópicos de álgebra e geometria.",
  "status": "pendente",
  "due_date": "2025-04-09"
}
```

**Exemplo de Resposta:**
```json
{
  "id": 3,
  "title": "Estudar para a prova",
  "description": "Revisar os tópicos de álgebra e geometria.",
  "status": "pendente",
  "due_date": "2025-04-09"
}
```

---

### 3. **Atualizar Tarefa**
**PUT /tasks/{id}**

Atualiza os dados de uma tarefa existente.

#### Parâmetros:
- `id`: ID da tarefa que será atualizada.

#### Corpo da Requisição:
```json
{
  "title": "Estudar para a prova de matemática",
  "description": "Revisar álgebra, geometria e trigonometria.",
  "status": "pendente",
  "due_date": "2025-04-09"
}
```

**Exemplo de Resposta:**
```json
{
  "id": 3,
  "title": "Estudar para a prova de matemática",
  "description": "Revisar álgebra, geometria e trigonometria.",
  "status": "pendente",
  "due_date": "2025-04-09"
}
```

---

### 4. **Excluir Tarefa**
**DELETE /tasks/{id}**

Exclui uma tarefa do sistema.

#### Parâmetros:
- `id`: ID da tarefa que será excluída.

**Exemplo de Resposta:**
```json
{
  "message": "Tarefa excluída com sucesso."
}
```

---

## **Erros**

A API retorna erros no seguinte formato:

```json
{
  "error": {
    "code": "400",
    "message": "Descrição da falha"
  }
}
```

### Códigos de Erro Comuns:
- `400`: Requisição mal formada.
- `401`: Não autorizado. Token inválido ou ausente.
- `404`: Não encontrado. O recurso solicitado não existe.
- `500`: Erro interno do servidor.

---

## **Exemplo de Fluxo de Trabalho**

1. **Autenticação**: Envie suas credenciais para gerar um token de autenticação.
2. **Criar Tarefa**: Use o endpoint `POST /tasks` para criar uma nova tarefa.
3. **Listar Tarefas**: Use `GET /tasks` para visualizar todas as tarefas.
4. **Atualizar Tarefa**: Use `PUT /tasks/{id}` para editar uma tarefa existente.
5. **Excluir Tarefa**: Use `DELETE /tasks/{id}` para excluir uma tarefa.

---

## **Conclusão**

Essa documentação fornece os detalhes básicos para interagir com a API do Task Manager. Caso você tenha mais dúvidas, consulte nossa seção de ajuda ou entre em contato com o suporte.

---

Isso é apenas um exemplo básico e genérico de uma API. Dependendo das funcionalidades e características específicas do seu sistema, você pode expandir ou modificar essa documentação. Se precisar de algo mais específico ou avançado, me avise!
