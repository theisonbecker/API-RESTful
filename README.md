# Node.js RESTful API - Shop API 🛍️

Uma API RESTful completa desenvolvida com **Node.js** e **Express**, planejada desde a sua concepção para simular o backend de uma loja virtual simples, gerenciando o catálogo de **produtos** e a criação/gestão de **pedidos (orders)**, além de controle de acesso com autenticação e autorização via **JWT**.

---

## 📌 Sobre o Projeto

Este projeto é uma API RESTful modular construída passo a passo, cobrindo as melhores práticas no desenvolvimento backend com o ecossistema Node.js:
* Estruturação de rotas e separação de responsabilidades com o padrão **MVC (Model-View-Controller)**.
* Tratamento centralizado de erros e requisições HTTP (404, 500, etc.).
* Integração com banco de dados NoSQL (**MongoDB**) via **Mongoose**.
* Upload e manipulação de arquivos de mídia (imagens dos produtos).
* Sistema completo de autenticação e proteção de rotas com **JSON Web Tokens (JWT)**.

---

## 🚀 Etapas de Desenvolvimento (Roadmap & Steps)

O desenvolvimento da aplicação foi estruturado nas seguintes etapas progressivas:

1. **Adding More Routes to the API**
   - Criação das rotas RESTful para recursos como `/products` e `/orders`.
   - Implementação de verbos HTTP fundamentais (`GET`, `POST`, `PATCH`, `DELETE`).

2. **Handling Errors & Improving the Project Setup**
   - Configuração de middlewares de logging (`morgan`).
   - Implementação de middleware global de captura de rotas inexistentes (404) e tratamento de exceções internas (500).

3. **Parsing the Body & Handling CORS**
   - Leitura de corpos de requisições JSON e urlencoded (`body-parser` / express body parsing).
   - Configuração de cabeçalhos de Cross-Origin Resource Sharing (CORS) para permitir a integração segura com frontends.

4. **MongoDB and Mongoose**
   - Conexão e configuração do banco de dados NoSQL MongoDB (local ou MongoDB Atlas).
   - Definição do schema e modelo base para a entidade `Product`.

5. **Mongoose Validation**
   - Adição de regras de validação nos schemas do Mongoose (campos obrigatórios, tipos de dados e valores padrão).

6. **Managing Orders with Mongoose**
   - Modelagem do schema `Order` com relacionamentos referenciando produtos (`Product`).
   - Regras de negócio para criação, listagem e exclusão de pedidos.

7. **Populating Queries with Mongoose**
   - Uso de `.populate()` do Mongoose para unir coleções (join entre pedidos e dados detalhados dos produtos).

8. **Uploading an Image**
   - Upload de imagens dos produtos usando o middleware `multer`.
   - Armazenamento estático e disponibilização pública de arquivos estáticos.

9. **Adding User Signup**
   - Criação do modelo de usuário (`User`).
   - Criptografia e hash seguro de senhas com `bcrypt`.

10. **Adding User Login & JWT Signing**
    - Verificação de credenciais e geração de tokens de acesso assinados com `jsonwebtoken` (JWT).

11. **JWT Route Protection**
    - Criação de middleware de autenticação (`check-auth`) para proteger rotas sensíveis contra acessos não autorizados.

12. **Adding Controllers**
    - Refatoração da camada de rotas para o padrão MVC, isolando toda a lógica de negócio em **Controllers** dedicados.

---

## 🛠️ Tecnologias e Ferramentas

* **Runtime:** [Node.js](https://nodejs.org/)
* **Framework:** [Express](https://expressjs.com/)
* **Banco de Dados:** [MongoDB](https://www.mongodb.com/) com [Mongoose](https://mongoosejs.com/)
* **Logging:** [Morgan](https://github.com/expressjs/morgan)
* **Parsing de Requisições:** [body-parser](https://github.com/expressjs/body-parser)
* **Upload de Imagens:** [Multer](https://github.com/expressjs/multer)
* **Segurança & Autenticação:** [Bcrypt](https://github.com/kelektiv/node.bcrypt.js) e [JSON Web Token (JWT)](https://jwt.io/)
* **Hot Reloading:** [Nodemon](https://nodemon.io/)

---

## ⚙️ Instalação e Execução

### Pré-requisitos
* [Node.js](https://nodejs.org/) instalado na máquina (versão 18+ recomendada)
* Instância do [MongoDB](https://www.mongodb.com/) em execução localmente ou conta no [MongoDB Atlas](https://www.mongodb.com/cloud/atlas)

### 1. Clonar o repositório ou abrir a pasta do projeto:
```bash
cd node-rest-shop
```

### 2. Instalar as dependências:
```bash
npm install
```

### 3. Iniciar o servidor em ambiente de desenvolvimento:
```bash
npm start
```
O servidor estará ativo em: `http://localhost:3000` (ou na porta definida na variável de ambiente `PORT`).

---

## 📡 Visão Geral dos Endpoints (Rotas)

| Método | Endpoint | Descrição | Autenticação |
| :--- | :--- | :--- | :---: |
| **GET** | `/products` | Lista todos os produtos cadastrados | Não |
| **POST** | `/products` | Cria um novo produto (suporte a upload de imagem) | Sim (JWT) |
| **GET** | `/products/:productId` | Retorna os detalhes de um produto específico | Não |
| **PATCH** | `/products/:productId` | Atualiza informações de um produto | Sim (JWT) |
| **DELETE** | `/products/:productId` | Remove um produto do catálogo | Sim (JWT) |
| **GET** | `/orders` | Lista todos os pedidos | Sim (JWT) |
| **POST** | `/orders` | Registra um novo pedido para um produto | Sim (JWT) |
| **GET** | `/orders/:orderId` | Consulta os detalhes de um pedido específico | Sim (JWT) |
| **DELETE** | `/orders/:orderId` | Cancela/deleta um pedido | Sim (JWT) |
| **POST** | `/user/signup` | Registra um novo usuário | Não |
| **POST** | `/user/login` | Autentica um usuário e retorna o token JWT | Não |
| **DELETE** | `/user/:userId` | Deleta um usuário existente | Sim (JWT) |

---

## 📝 Licença

Este projeto é desenvolvido para fins de estudo e prática. Distribuído sob a licença **ISC**.

