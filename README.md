# 📚 Livros API - Spring Boot & SQL (H2)

Uma API RESTful simples e eficiente para gerenciamento de livros, desenvolvida com **Java**, **Spring Boot** e banco de dados **SQL H2 (em memória)**.

Este projeto foi construído como um guia prático para iniciantes entenderem a integração entre a camada Web (Controllers), a camada de persistência de dados (Spring Data JPA) e um banco de dados SQL.

---

## 🛠️ Tecnologias Utilizadas

* **Java 17** - Linguagem de programação.
* **Spring Boot** - Framework Java para desenvolvimento rápido de aplicações.
    * **Spring Web** - Criação de endpoints HTTP / API REST.
    * **Spring Data JPA** - Mapeamento objeto-relacional e execução automática de comandos SQL.
* **H2 Database** - Banco de dados SQL em memória (não precisa instalar nada externamente).
* **Maven** - Gerenciador de dependências e build.
* **IntelliJ IDEA** - IDE de desenvolvimento.

---

## 📁 Estrutura do Projeto

O projeto segue a arquitetura em camadas padrão do Spring Boot:

```text
src/main/java/com/example/livrosapi/
 ├── controller/
 │    └── LivroController.java    # Gerencia os endpoints e requisições HTTP
 ├── model/
 │    └── Livro.java              # Entidade que mapeia a tabela no banco SQL
 ├── repository/
 │    └── LivroRepository.java    # Interface JPA para operações no banco (CRUD)
 └── LivrosApiApplication.java   # Classe principal que inicia o Spring Boot

# Porta onde a aplicação irá rodar
server.port=8081

# Configurações do Banco de Dados SQL (H2)
spring.datasource.url=jdbc:h2:mem:livrosdb
spring.datasource.driverClassName=org.h2.Driver
spring.datasource.username=sa
spring.datasource.password=
spring.h2.console.enabled=true

spring.h2.console.enabled=true
spring.h2.console.enabled=true

## ⚙️ Configuração do Ambiente (`application.properties`)

O arquivo `src/main/resources/application.properties` deve conter as seguintes configurações para rodar na porta `8081` e ativar o banco H2:

```properties
# Porta da aplicação
server.port=8081

# Configurações do Banco de Dados SQL (H2)
spring.datasource.url=jdbc:h2:mem:livrosdb
spring.datasource.driverClassName=org.h2.Driver
spring.datasource.username=sa
spring.datasource.password=
spring.h2.console.enabled=true

🚀 Como Executar o Projeto
Abrir no IntelliJ IDEA:

Abra o IntelliJ.

Vá em File > Open e selecione a pasta do projeto (livros-api).

Sincronizar as Dependências:

Caso o IntelliJ solicite, clique no ícone do Maven (canto superior direito) para baixar as bibliotecas do pom.xml.

Executar a Aplicação:

Navegue até a pasta src/main/java/com/example/livrosapi/.

Abra a classe LivrosApiApplication.java.

Clique no ícone do Play (triângulo verde) ao lado do nome da classe ou aperte Shift + F10.

Confirmar a Inicialização:

Acompanhe os logs no console do IntelliJ até aparecer a mensagem:
Started LivrosApiApplication in X seconds

🧪 Exemplos de Uso
A aplicação rodará no endereço base: http://localhost:8081

1. Cadastrar um Novo Livro (POST)
URL: http://localhost:8081/livros

Método: POST

Cabeçalho (Header): Content-Type: application/json

Corpo (Body JSON):
{
  "titulo": "Dom Casmurro",
  "autor": "Machado de Assis"
}

2. Listar Todos os Livros (GET)
URL: http://localhost:8081/livros

Método: GET

Resposta Esperada (JSON):
[
  {
    "id": 1,
    "titulo": "Dom Casmurro",
    "autor": "Machado de Assis"
  }
]

🗄️ Acessando o Console do Banco SQL (H2)
O Spring Boot fornece uma interface gráfica no navegador para visualizar e manipular as tabelas SQL diretamente.

Abra o seu navegador e acesse: http://localhost:8081/h2-console

Preencha os campos da tela de login exatamente assim:

JDBC URL: jdbc:h2:mem:livrosdb

User Name: sa

Password: (deixe o campo em branco)

Clique no botão Connect.

No painel esquerdo, você poderá visualizar a tabela LIVRO e executar comandos SQL (SELECT * FROM LIVRO;).
