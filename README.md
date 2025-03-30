## Propósito

Este repositório foi criado para ensinar o uso do Docker, criando uma imagem com um Banco de Dados Postgres chamado "Escola" com suas entidades Turma, Professor e Aluno

#3 Estrutura Inicial do Projeto

├── DB/ <!-- Contem os arquivos docker para subir o Banco Escola --><br>
│ ├── Escola.sql <!-- SQL utilizado para criar o Banco e as tabelas utilizadas no projeto --><br> 
│ ├── Dockerfile <!-- arquivo docker para inicializar o postgre --><br>
├── docker-compose.yml <!-- define a configuração para o serviço db --><br>
├── README.md <!-- Arquivo com instruções gerais --><br>

## Estrutura do Banco de Dados

Para o Banco de Dados, temos as entidades:

• Turma: possui os campos id_turma, nome, id_professor, etc.
• Professor: possui os campos id_professor, nome, email, etc.
• Aluno: possui os campos id_aluno, nome, data_nascimento, etc.

## Relacionamentos

## Pré-Requisitos

Para rodarmos essa aplicação, devemos ter algumas ferramentas instaladas na máquina:

• Docker Engine
• Docker-Compose
• Editor de Código de sua preferência

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


