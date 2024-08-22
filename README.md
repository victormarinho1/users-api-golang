# API de Usuários

Esta é uma API simples para gerenciamento de usuários, implementada em Go. A API permite realizar operações CRUD (Create, Read, Update, Delete) em um banco de dados PostgreSQL.

## Endpoints

### 1. **Buscar Todos os Usuários**

- **URL:** `/users/findall`
- **Método:** `GET`
- **Descrição:** Retorna uma lista de todos os usuários no banco de dados.
- **Resposta:**
  - **Código:** `200 OK`
  - **Corpo:** Lista de objetos `User` no formato JSON.

### 2. **Buscar Usuário por ID**

- **URL:** `/users/findbyid?id=<user_id>`
- **Método:** `GET`
- **Descrição:** Retorna um usuário específico baseado no ID fornecido.
- **Parâmetros:**
  - `id` (query parameter): ID do usuário a ser buscado.
- **Resposta:**
  - **Código:** `200 OK`
  - **Corpo:** Objeto `User` no formato JSON.
  - **Código:** `404 Not Found` se o usuário não for encontrado.

### 3. **Criar Novo Usuário**

- **URL:** `/users/create`
- **Método:** `POST`
- **Descrição:** Cria um novo usuário com os dados fornecidos.
- **Corpo da Requisição:** 
  - **Formato:** JSON
  - **Exemplo:**
    ```json
    {
      "name": "Nome do Usuário",
      "email": "usuario@exemplo.com",
      "age": 30
    }
    ```
- **Resposta:**
  - **Código:** `201 Created`
  - **Corpo:** Nenhum

### 4. **Atualizar Usuário**

- **URL:** `/users/update?id=<user_id>`
- **Método:** `PUT`
- **Descrição:** Atualiza os dados de um usuário específico baseado no ID fornecido.
- **Parâmetros:**
  - `id` (query parameter): ID do usuário a ser atualizado.
- **Corpo da Requisição:**
  - **Formato:** JSON
  - **Exemplo:**
    ```json
    {
      "Name": "Nome Atualizado",
      "Email": "novoemail@exemplo.com",
      "Age": 35
    }
    ```
- **Resposta:**
  - **Código:** `200 OK`
  - **Corpo:** Objeto `User` atualizado no formato JSON.
  - **Código:** `404 Not Found` se o usuário não for encontrado.

### 5. **Deletar Usuário**

- **URL:** `/users/delete?id=<user_id>`
- **Método:** `DELETE`
- **Descrição:** Remove um usuário específico baseado no ID fornecido.
- **Parâmetros:**
  - `id` (query parameter): ID do usuário a ser deletado.
- **Resposta:**
  - **Código:** `204 No Content`
  - **Código:** `404 Not Found` se o usuário não for encontrado.

## Configuração

1. **Banco de Dados:**
   - A API usa um banco de dados PostgreSQL. Certifique-se de que o banco de dados está configurado e acessível.
   - A URL de conexão usada na API é: `postgres://root:123456@postgres/crud?sslmode=disable`.

2. **Iniciar a API:**
   - Certifique-se de que você tem o Go e as dependências instaladas.
   - Execute o comando a seguir para iniciar o servidor:
     ```bash
     go run main.go
     ```

   - O servidor será iniciado na porta `8080`.

## Dependências

- Go (1.22.6 ou superior)
- PostgreSQL
- Pacote `pq` para PostgreSQL

## Exemplo de Configuração do Banco de Dados

Certifique-se de que o banco de dados PostgreSQL está configurado corretamente com a tabela `users`. Um exemplo básico de comando SQL para criar a tabela é:

```sql
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    name VARCHAR,
    email VARCHAR UNIQUE NOT NULL,
    age INT
);
