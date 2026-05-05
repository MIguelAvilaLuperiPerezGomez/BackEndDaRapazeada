# BackEndDaRapazeada 📋

API REST para gerenciamento de tarefas, desenvolvida com **Node.js**, **Express** e **MongoDB (Mongoose)**. Serve como backend para aplicações de lista de tarefas (To-Do List), com suporte a criação, listagem, atualização e exclusão de tarefas.

---

## 🛠️ Tecnologias

- [Node.js](https://nodejs.org/)
- [Express 5](https://expressjs.com/)
- [Mongoose 9](https://mongoosejs.com/)
- [MongoDB Atlas](https://www.mongodb.com/atlas) (via variável de ambiente)

---

## 📁 Estrutura do Projeto

```
BackEndDaRapazeada/
├── index.js              # Entrada da aplicação (servidor + conexão com o banco)
├── routes/
│   └── routes.js         # Definição das rotas da API
├── models/
│   └── tarefa.js         # Schema/modelo da tarefa no MongoDB
└── package.json
```

---

## ⚙️ Configuração e Instalação

### Pré-requisitos

- Node.js instalado
- Uma instância do MongoDB (local ou [MongoDB Atlas](https://www.mongodb.com/atlas))

### Passos

1. Clone o repositório:
   ```bash
   git clone https://github.com/seu-usuario/BackEndDaRapazeada.git
   cd BackEndDaRapazeada
   ```

2. Instale as dependências:
   ```bash
   npm install
   ```

3. Configure a variável de ambiente com a URI do MongoDB:
   ```bash
   # Linux / macOS
   export MONGODB_URI="mongodb+srv://usuario:senha@cluster.mongodb.net/nomeDoBanco"

   # Windows (CMD)
   set MONGODB_URI="mongodb+srv://usuario:senha@cluster.mongodb.net/nomeDoBanco"
   ```

4. Inicie o servidor:
   ```bash
   npm start
   ```

O servidor estará disponível em `http://localhost:3000` (ou na porta definida pela variável `PORT`).

---

## 🗄️ Modelo de Dados — Tarefa

| Campo            | Tipo    | Obrigatório | Descrição                        |
|------------------|---------|-------------|----------------------------------|
| `descricao`      | String  | ✅ Sim      | Texto descritivo da tarefa       |
| `statusRealizada`| Boolean | ✅ Sim      | Indica se a tarefa foi concluída |

---

## 🔌 Endpoints da API

Base URL: `/api`

### ➕ Criar Tarefa

```
POST /api/post
```

**Body (JSON):**
```json
{
  "descricao": "Estudar para a prova",
  "statusRealizada": false
}
```

**Resposta (200):**
```json
{
  "_id": "664abc123...",
  "descricao": "Estudar para a prova",
  "statusRealizada": false
}
```

---

### 📋 Listar Todas as Tarefas

```
GET /api/getAll
```

**Resposta (200):**
```json
[
  {
    "_id": "664abc123...",
    "descricao": "Estudar para a prova",
    "statusRealizada": false
  }
]
```

---

### ✏️ Atualizar Tarefa

```
PATCH /api/update/:id
```

**Parâmetro:** `:id` — ID da tarefa no MongoDB

**Body (JSON):** Apenas os campos que deseja atualizar:
```json
{
  "statusRealizada": true
}
```

**Resposta (200):** Objeto atualizado.

---

### 🗑️ Deletar Tarefa

```
DELETE /api/delete/:id
```

**Parâmetro:** `:id` — ID da tarefa no MongoDB

**Resposta (200):** Objeto que foi removido.

---

## 🌐 CORS

A API está configurada para aceitar requisições de qualquer origem (`*`), permitindo integração com frontends em qualquer domínio. Os métodos permitidos são: `GET`, `POST`, `PATCH`, `PUT`, `DELETE` e `HEAD`.

---

## ☁️ Deploy

O projeto está preparado para deploy no [Render](https://render.com/). As variáveis de ambiente `PORT` e `MONGODB_URI` são lidas automaticamente do ambiente de produção.

---

## 📝 Scripts

| Comando       | Descrição               |
|---------------|-------------------------|
| `npm start`   | Inicia o servidor       |
