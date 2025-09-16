
# MediaWiki com Docker Compose

## Português

Este projeto demonstra como criar uma instância do MediaWiki utilizando Docker Compose. O arquivo `docker-compose.yaml` define os serviços necessários para rodar o MediaWiki com um banco de dados PostgreSQL.

### Sobre o MediaWiki
MediaWiki é uma plataforma colaborativa para criação de wikis, utilizada por projetos como a Wikipédia. Permite que múltiplos usuários editem e organizem conteúdos facilmente.

### Explicação do docker-compose.yaml
- **version: '3.8'**: Define a versão do Docker Compose.
- **services**: Lista os serviços que serão criados.
	- **db**: Serviço do banco de dados PostgreSQL.
		- **image: postgres:13**: Usa a imagem oficial do PostgreSQL versão 13.
		- **restart: always**: Reinicia o container automaticamente.
		- **environment**: Variáveis para configurar o banco (usuário, senha, nome do banco).
		- **volumes**: Persiste os dados do banco em um volume chamado `db-data`.
		- **networks**: Conecta à rede interna `app-network`.
	- **web**: Serviço da aplicação web (MediaWiki).
		- **build: .**: Constrói a imagem a partir do Dockerfile local.
		- **ports**: Mapeia a porta 8080 do host para a porta 80 do container.
		- **volumes**: Monta o diretório `./app` no container.
		- **depends_on**: Garante que o serviço web só inicie após o banco.
		- **networks**: Conecta à rede interna `app-network`.
- **networks**: Define a rede interna do tipo bridge.
- **volumes**: Volume nomeado para persistência dos dados do banco.

### O que este Compose produz?
Cria um ambiente pronto para rodar o MediaWiki localmente, com persistência de dados e fácil configuração.

---

## English

This project demonstrates how to create a MediaWiki instance using Docker Compose. The `docker-compose.yaml` file defines the services required to run MediaWiki with a PostgreSQL database.

### About MediaWiki
MediaWiki is a collaborative platform for creating wikis, used by projects like Wikipedia. It allows multiple users to edit and organize content easily.

### docker-compose.yaml explanation
- **version: '3.8'**: Sets the Docker Compose version.
- **services**: Lists the services to be created.
	- **db**: PostgreSQL database service.
		- **image: postgres:13**: Uses the official PostgreSQL version 13 image.
		- **restart: always**: Automatically restarts the container.
		- **environment**: Variables to configure the database (user, password, database name).
		- **volumes**: Persists database data in a volume named `db-data`.
		- **networks**: Connects to the internal `app-network`.
	- **web**: Web application service (MediaWiki).
		- **build: .**: Builds the image from the local Dockerfile.
		- **ports**: Maps host port 8080 to container port 80.
		- **volumes**: Mounts the `./app` directory in the container.
		- **depends_on**: Ensures the web service starts only after the database.
		- **networks**: Connects to the internal `app-network`.
- **networks**: Defines the internal bridge network.
- **volumes**: Named volume for database data persistence.

### What does this Compose produce?
Creates a ready-to-use environment to run MediaWiki locally, with data persistence and easy configuration.

---

## Como usar / How to use

**PT:**
1. Instale o Docker e Docker Compose.
2. Execute `docker-compose up -d` na pasta do projeto.
3. Acesse o MediaWiki via navegador em `http://localhost:8080`.

**EN:**
1. Install Docker and Docker Compose.
2. Run `docker-compose up -d` in the project folder.
3. Access MediaWiki via browser at `http://localhost:8080`.

---

Repositório: https://github.com/Ch1c4n0/Create-MediaWiki-with-Docker-Compose
