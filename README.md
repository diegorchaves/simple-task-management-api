# Simple Task Management API

---

## Visão Geral

Este projeto é uma **API RESTful** simples para gerenciamento de tarefas, desenvolvida utilizando **Java** e o framework **Spring Boot**. Ele foi projetado para demonstrar proficiência em tecnologias essenciais para o desenvolvimento back-end, incluindo gerenciamento de dados com **JPA/Hibernate** e **PostgreSQL**, exposição de endpoints RESTful, e versionamento de código com **Git**.

O projeto segue princípios de design modular, preparando a arquitetura para futura escalabilidade e possível integração em um contexto de **microsserviços**. A configuração externa do banco de dados o torna **cloud-native ready**, facilitando a implantação em plataformas como **AWS**.

---

## Tecnologias Utilizadas

* **Java 21**
* **Spring Boot 3.5.2**
    * Spring Web
    * Spring Data JPA
* **PostgreSQL**
* **Maven**
* **Git**
* **Lombok** (para redução de boilerplate code)
* **REST API**

---

## Funcionalidades da API

A API oferece operações CRUD (Create, Read, Update, Delete) para o gerenciamento de tarefas:

* **Criar Tarefa:** Adiciona uma nova tarefa com título, descrição e status.
* **Listar Todas as Tarefas:** Retorna uma lista completa de todas as tarefas cadastradas.
* **Obter Tarefa por ID:** Recupera os detalhes de uma tarefa específica.
* **Atualizar Tarefa:** Modifica os dados de uma tarefa existente.
* **Deletar Tarefa:** Remove uma tarefa do sistema.

---

## Pré-requisitos

Antes de rodar o projeto localmente, certifique-se de ter instalado:

* **Java Development Kit (JDK) 21** (ou a versão correspondente)
* **Maven**
* **PostgreSQL** (com um banco de dados criado, ex: `task_manager_db`)
* Um cliente REST para testes (ex: [Postman](https://www.postman.com/downloads/), [Insomnia](https://insomnia.rest/download/))

---

## Configuração do Banco de Dados

1.  **Crie um banco de dados PostgreSQL** chamado `task_manager_db`.
2.  Execute o seguinte comando SQL para criar a tabela `tasks`:

    ```sql
    CREATE TABLE tasks (
        id SERIAL PRIMARY KEY,
        title VARCHAR(255) NOT NULL,
        description TEXT,
        status VARCHAR(50) NOT NULL
    );
    ```

3.  **Atualize o arquivo `src/main/resources/application.properties`** com suas credenciais do PostgreSQL:

    ```properties
    spring.datasource.url=jdbc:postgresql://localhost:5432/task_manager_db
    spring.datasource.username=seu_usuario_postgresql
    spring.datasource.password=sua_senha_postgresql
    spring.jpa.hibernate.ddl-auto=update
    spring.jpa.show-sql=true
    spring.jpa.properties.hibernate.format_sql=true
    ```

---

## Como Rodar o Projeto Localmente

1.  **Clone o repositório:**
    ```bash
    git clone https://github.com/diegorchaves/simple-task-management-api.git
    cd simple-task-management-api
    ```
2.  **Inicie o servidor PostgreSQL.**
3.  **Compile e execute o aplicativo Spring Boot:**
    ```bash
    mvn clean install
    mvn spring-boot:run
    ```
    O aplicativo estará disponível em `http://localhost:8080` (ou na porta configurada em `application.properties`).

---

## Endpoints da API

A API está disponível no endpoint base: `http://localhost:8080/api/tasks`

| Método HTTP | Endpoint       | Descrição                      | Corpo da Requisição (JSON) Exemplo                                     |
| :---------- | :------------- | :----------------------------- | :--------------------------------------------------------------------- |
| `POST`      | `/api/tasks`   | Cria uma nova tarefa           | `{ "title": "Comprar leite", "description": "No mercado", "status": "PENDING" }` |
| `GET`       | `/api/tasks`   | Lista todas as tarefas         | `(Nenhum)`                                                             |
| `GET`       | `/api/tasks/{id}` | Busca uma tarefa pelo ID      | `(Nenhum)`                                                             |
| `PUT`       | `/api/tasks/{id}` | Atualiza uma tarefa existente | `{ "id": 1, "title": "Comprar pão", "description": "Na padaria", "status": "COMPLETED" }` |
| `DELETE`    | `/api/tasks/{id}` | Deleta uma tarefa pelo ID     | `(Nenhum)`                                                             |

---

## Contribuição

Contribuições são bem-vindas! Sinta-se à vontade para abrir issues ou pull requests.

---

## Licença

Este projeto está licenciado sob a [MIT License](LICENSE).