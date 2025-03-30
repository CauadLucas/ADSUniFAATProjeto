## Propósito

Este repositório foi criado para ensinar o uso do Docker, criando uma imagem com um Banco de Dados Postgres chamado "Escola" com suas entidades Turma, Professor e Aluno

## Estrutura Inicial do Projeto

├── DB/ <!-- Contem os arquivos docker para subir o Banco Escola --><br>
│ ├── Escola.sql <!-- SQL utilizado para criar o Banco e as tabelas utilizadas no projeto --><br> 
│ ├── Dockerfile <!-- arquivo docker para inicializar o postgre --><br>
├── docker-compose.yml <!-- define a configuração para o serviço db --><br>
├── README.md <!-- Arquivo com instruções gerais --><br>

## Estrutura do Banco de Dados

Para o Banco de Dados, temos as entidades:

• Turma: possui os campos id_turma, nome, id_professor, etc. <br>
• Professor: possui os campos id_professor, nome, email, etc. <br>
• Aluno: possui os campos id_aluno, nome, data_nascimento, etc. <br>

## Pré-Requisitos

Para rodarmos essa aplicação, devemos ter algumas ferramentas instaladas na máquina:

• Docker Engine <br>
• Docker-Compose <br>
• Editor de Código de sua preferência <br>

## Docker-Compose

Siga o passos a seguir para rodar o Docker-Compose:

Certifique-se de que você tem o Docker e o Docker-Compose instalados na sua máquina.
```sh
docker --version
``` 
```sh
docker-compose --version
```

Execute o comando para iniciar os contêineres com o Docker-Compose:
```sh
docker-compose up --build
```

Caso precise parar ou remover contêineres, execute o seguinte comando no diretório raiz:
```sh
docker-compose down
```

## Dockerfile

O Dockerfile se baseia na imagem oficial do PostgreSQL para configurar o ambiente. Ele define o banco de dados com credenciais padrão e transfere um script SQL de inicialização para o diretório apropriado, garantindo que seja executado automaticamente ao iniciar o serviço.

## Estrutura do Dockerfile

```dockerfile
# Use a imagem oficial do PostgreSQL como base
FROM postgres:17

# Defina variáveis de ambiente para configurar o PostgreSQL
ENV POSTGRES_DB=Escola
ENV POSTGRES_USER=unifaat
ENV POSTGRES_PASSWORD=unifaat

# Copie o script de inicialização para o diretório de inicialização do PostgreSQL
COPY Escola.sql /docker-entrypoint-initdb.d/

# Exponha a porta padrão do PostgreSQL
EXPOSE 5432
```

## Como utilizar

1. Execute esse comando no diretório do Dockerfile para construir a imagem Docker:
```bash
docker build -t my-postgres-image .
```

2. Para executar o contêiner Docker com a imagem criada, utilize o seguinte comando:
```bash 
docker run -d --name my-postgres-container -p 2000:5432 my-postgres-image
```

3. Você pode se conectar ao PostgreSQL utilizando um cliente PostgreSQL, como dbeaver, psql, ou qualquer ferramenta de gerenciamento de banco de dados que suporte PostgreSQL, utilizando as seguintes credenciais:
```
Host: localhost
Porta: 3000
Banco de Dados: Escola
Usuário: unifaat
Senha: unifaat
```

## Escola.sql

Script para inicializar o banco de dados com as tabelas necessárias:

```sql
-- Criação da tabela de Turma
CREATE TABLE Turma (
    id_turma SERIAL PRIMARY KEY NOT NULL,
    nome_turma VARCHAR(50) NOT NULL,
    id_professor INTEGER NOT NULL,
    horario VARCHAR(100) NOT NULL,
    FOREIGN KEY (id_professor) REFERENCES Professor(id_professor) --id_professor é chave estrangeira em Turma referenciando id_professor em Professor
);

-- Criação da tabela de Professor
CREATE TABLE Professor (
    id_professor SERIAL PRIMARY KEY NOT NULL,
    nome_completo VARCHAR(255) NOT NULL,
    email VARCHAR(100) NOT NULL,
    telefone VARCHAR(20) NOT NULL
);

-- Criação da tabela de Aluno
CREATE TABLE Aluno (
    id_aluno SERIAL PRIMARY KEY NOT NULL,
    nome_completo VARCHAR(255) NOT NULL,
    data_nascimento DATE NOT NULL,
    id_turma INTEGER NOT NULL,
    nome_responsavel VARCHAR(255) NOT NULL,
    telefone_responsavel VARCHAR(20) NOT NULL,
    email_responsavel VARCHAR(100) NOT NULL,
    informacoes_adicionais TEXT,
    FOREIGN KEY (id_turma) REFERENCES Turma(id_turma) --id_turma é chave estrangeira em Aluno referenciando id_turma em Turma
);

--Depois que arrumar estilizaão, adicionar sobre o docker-compose.yml--


