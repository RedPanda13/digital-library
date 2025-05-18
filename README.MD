# Biblioteca Digital API

API RESTful para gerenciamento de uma biblioteca digital, incluindo microsserviços de Livros, Autores, Usuários, Empréstimos e Recomendações.

## Sumário

- [Visão Geral](#visão-geral)
- [Ambientes](#ambientes)
- [Recursos Principais](#recursos-principais)
    - [Livros](#livros)
    - [Autores](#autores)
    - [Usuários & Autenticação](#usuários--autenticação)
    - [Empréstimos](#empréstimos)
    - [Recomendações](#recomendações)
    - [Healthcheck](#healthcheck)
- [Modelos Principais](#modelos-principais)
- [Exemplos de Uso](#exemplos-de-uso)

---

## Visão Geral

Esta API permite:

- Gerenciar livros e autores
- Realizar cadastro e autenticação de usuários (JWT)
- Registrar e consultar empréstimos de livros
- Gerar recomendações de leitura
- Monitorar o status do serviço

## Ambientes

- **Produção:** `https://api.sualibrary.com/api/v1`
- **Local:** `http://localhost:8080/api/v1`

## Recursos Principais

### Livros

- **GET /books:** Lista, filtra e pagina livros (por título, autor, ano, status, etc.)
- **POST /books:** Cadastra novo livro (admin)
- **GET /books/{id}:** Detalhes de um livro
- **PUT /books/{id}:** Atualiza livro (admin)
- **DELETE /books/{id}:** Remove livro (admin)
- **GET /authors/{id}/books:** Lista livros de um autor

### Autores

- **GET /authors:** Lista/filtro de autores
- **POST /authors:** Cadastra autor (admin)
- **GET /authors/{id}:** Detalhes do autor
- **PUT /authors/{id}:** Edita autor (admin)
- **DELETE /authors/{id}:** Exclui autor (admin)

### Usuários & Autenticação

- **POST /users:** Cadastro de usuário
- **POST /login:** Autenticação (JWT)
- **POST /refresh-token:** Renovação de JWT
- **GET /users/me:** Dados do usuário autenticado
- **PUT /users/me:** Editar perfil
- **GET /users/{id}/roles:** Lista de roles do usuário
- **POST /logout:** Logout (blacklist JWT)

### Empréstimos

- **POST /loans:** Novo empréstimo de livro
- **GET /loans:** Lista/filtro de empréstimos
- **GET /loans/{id}:** Detalhe do empréstimo
- **PUT /loans/{id}/return:** Devolver livro
- **GET /users/{id}/status:** Status de empréstimos do usuário

### Recomendações

- **GET /recommendations:** Recomenda livros (personalizado ou geral)
- **GET /recommendations/top:** Livros mais populares

### Healthcheck

- **GET /health:** Verifica se o serviço está operacional