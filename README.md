# 🎮 Loja de Games API

## 📋 Descrição do Projeto
API RESTful para gerenciamento de uma loja de games, desenvolvida com Spring Boot como parte do exercício prático do curso Generation Brasil.

## 🚀 Tecnologias Utilizadas
- **Java 17**
- **Spring Boot 3.1.5**
- **Spring Data JPA**
- **Spring Web MVC**
- **MySQL 8.0**
- **Maven**
- **Hibernate**

## 📦 Funcionalidades

### Categoria (CRUD completo - 6 métodos)
- `GET /categorias` - Listar todas as categorias
- `GET /categorias/{id}` - Buscar categoria por ID
- `GET /categorias/descricao/{descricao}` - Buscar categoria por descrição
- `POST /categorias` - Cadastrar nova categoria
- `PUT /categorias` - Atualizar categoria existente
- `DELETE /categorias/{id}` - Deletar categoria

### Produto (CRUD completo - 6 métodos)
- `GET /produtos` - Listar todos os produtos
- `GET /produtos/{id}` - Buscar produto por ID
- `GET /produtos/nome/{nome}` - Buscar produto por nome
- `POST /produtos` - Cadastrar novo produto
- `PUT /produtos` - Atualizar produto existente
- `DELETE /produtos/{id}` - Deletar produto

### Relacionamento
- **OneToMany / ManyToOne** entre Categoria e Produto
- Uma categoria pode ter vários produtos
- Cada produto pertence a uma categoria

## 🛠️ Configuração do Banco de Dados

### application.properties
```properties
spring.application.name=lojagames
spring.jpa.hibernate.ddl-auto=update
spring.datasource.url=jdbc:mysql://localhost:3306/db_lojagames?createDatabaseIfNotExist=true&serverTimezone=America/Sao_Paulo&useSSL=false&allowPublicKeyRetrieval=true
spring.datasource.username=root
spring.datasource.password=SUA_SENHA_AQUI
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
spring.jpa.show-sql=true
spring.jpa.open-in-view=true
spring.jpa.properties.hibernate.jdbc.time_zone=America/Sao_Paulo
```

## 📥 Como Executar o Projeto

### Pré-requisitos
- JDK 17 ou superior
- MySQL 8.0 instalado e rodando
- Maven
- Spring Tool Suite (STS) ou IDE de sua preferência

### Passos
1. Clone o repositório:
```bash
git clone https://github.com/talitatech/loja-de-games.git
```

2. Configure o banco de dados no `application.properties` com seu usuário e senha do MySQL

3. Execute a aplicação:
   - No STS: Clique com botão direito no projeto → Run As → Spring Boot App
   - Ou via terminal: `mvn spring-boot:run`

4. A aplicação estará disponível em: `http://localhost:8080`

## 🧪 Testando a API (Insomnia/Postman)

### Exemplo de requisições:

**1. Cadastrar Categoria (POST)**
```json
POST http://localhost:8080/categorias
Content-Type: application/json

{
  "tipo": "Ação",
  "descricao": "Jogos de ação e aventura"
}
```

**2. Cadastrar Produto (POST)**
```json
POST http://localhost:8080/produtos
Content-Type: application/json

{
  "nome": "God of War Ragnarok",
  "descricao": "Jogo épico de aventura na mitologia nórdica",
  "preco": 299.90,
  "plataforma": "PlayStation 5",
  "estoque": 50,
  "categoria": {
    "id": 1
  }
}
```

**3. Listar todos os produtos (GET)**
```
GET http://localhost:8080/produtos
```

**4. Buscar produto por nome (GET)**
```
GET http://localhost:8080/produtos/nome/God
```

**5. Atualizar produto (PUT)**
```json
PUT http://localhost:8080/produtos
Content-Type: application/json

{
  "id": 1,
  "nome": "God of War Ragnarok - Edição Deluxe",
  "descricao": "Jogo épico de aventura com conteúdo exclusivo",
  "preco": 349.90,
  "plataforma": "PlayStation 5",
  "estoque": 45,
  "categoria": {
    "id": 1
  }
}
```

**6. Deletar produto (DELETE)**
```
DELETE http://localhost:8080/produtos/1
```

## 📁 Estrutura do Projeto

```
lojagames/
├── src/main/java/com/generation/lojagames/
│   ├── controller/
│   │   ├── CategoriaController.java
│   │   └── ProdutoController.java
│   ├── model/
│   │   ├── Categoria.java
│   │   └── Produto.java
│   ├── repository/
│   │   ├── CategoriaRepository.java
│   │   └── ProdutoRepository.java
│   └── LojagamesApplication.java
├── src/main/resources/
│   └── application.properties
└── pom.xml
```

## ✅ Requisitos Atendidos

- [x] CRUD completo do recurso Produto (6 métodos)
- [x] CRUD completo do recurso Categoria (6 métodos)
- [x] Relacionamento OneToMany/ManyToOne entre Categoria e Produto
- [x] Configuração do banco de dados no application.properties
- [x] Seguindo boas práticas do Spring (Model, Repository, Controller)
- [x] API testada no Insomnia
- [x] Projeto versionado no GitHub

## 👩‍💻 Autora
**Talita** - Turma Generation Brasil

## 📅 Data da Entrega
Maio/2026

## 🔗 Links
- [Repositório no GitHub](https://github.com/talitatech/loja-de-games)
```
