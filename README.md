# Fokus — Backend

API REST fake construída com [json-server](https://github.com/typicode/json-server) para servir de backend ao projeto **Fokus** do curso de JavaScript da Alura.

## Pré-requisitos

- [Node.js](https://nodejs.org/) v18 ou superior
- npm (já vem com o Node)

## Instalação

```bash
npm install
```

## Rodando o servidor

```bash
npm start
```

O servidor sobe em **http://localhost:4242**.

## Endpoints disponíveis

O json-server gera automaticamente uma API REST completa a partir do `db.json`.

### Tarefas — `/tasks`

| Método | Rota | Descrição |
|--------|------|-----------|
| `GET` | `/tasks` | Lista todas as tarefas |
| `GET` | `/tasks/:id` | Busca uma tarefa pelo id |
| `POST` | `/tasks` | Cria uma nova tarefa |
| `PUT` | `/tasks/:id` | Substitui uma tarefa por completo |
| `PATCH` | `/tasks/:id` | Atualiza campos específicos de uma tarefa |
| `DELETE` | `/tasks/:id` | Remove uma tarefa |

### Estrutura de uma tarefa

```json
{
  "id": 1748217600000,
  "description": "Estudar JavaScript",
  "completed": false
}
```

### Exemplos de uso

**Listar todas as tarefas:**
```bash
curl http://localhost:4242/tasks
```

**Criar uma tarefa:**
```bash
curl -X POST http://localhost:4242/tasks \
  -H "Content-Type: application/json" \
  -d '{"id": 1748300000000, "description": "Nova tarefa", "completed": false}'
```

**Marcar como concluída:**
```bash
curl -X PATCH http://localhost:4242/tasks/1748217600000 \
  -H "Content-Type: application/json" \
  -d '{"completed": true}'
```

**Deletar uma tarefa:**
```bash
curl -X DELETE http://localhost:4242/tasks/1748217600000
```

## Filtros e busca

O json-server suporta filtros via query string:

```bash
# Apenas tarefas pendentes
GET /tasks?completed=false

# Apenas tarefas concluídas
GET /tasks?completed=true
```

## Estrutura do projeto

```
backend/
├── db.json        # banco de dados (arquivo JSON)
├── package.json
└── README.md
```

> **Atenção:** toda alteração feita via API é persistida diretamente no `db.json`. Para resetar os dados, restaure o arquivo manualmente.
