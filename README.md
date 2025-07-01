# Microserviço de Recuperação de Email - Plataforma Zeelus

Este é um microserviço desenvolvido em Spring Boot responsável pelo gerenciamento e envio de emails na Plataforma Zeelus. O serviço utiliza RabbitMQ para processamento assíncrono de mensagens e PostgreSQL para persistência de dados.

## 🚀 Tecnologias Utilizadas

- Java 21
- Spring Boot 3.4.3
- PostgreSQL
- RabbitMQ
- Docker
- Maven

## 📋 Pré-requisitos

Para executar este projeto, você precisará ter instalado em sua máquina:

- Java 21
- Docker e Docker Compose
- Maven
- Um cliente de email Gmail (para envio de emails)
- Uma conta no CloudAMQP (para RabbitMQ)

## 🔧 Configuração

### Configurando o Banco de Dados

O projeto utiliza PostgreSQL como banco de dados. Para iniciar o banco de dados, execute:

```bash
docker-compose up -d
```

Isso irá criar um container PostgreSQL com as seguintes configurações:
- Porta: 5433
- Usuário: admin
- Senha: admin
- Database: ms-email

### Configurando o Email

Para configurar o serviço de email, você precisa atualizar as seguintes propriedades no arquivo `application.properties`:

```properties
spring.mail.username=seuEmail@gmail.com
spring.mail.password=sua_senha_de_app
```

Nota: Para o Gmail, você precisará gerar uma senha de aplicativo específica.

### Configurando o RabbitMQ

Configure sua conexão com o RabbitMQ atualizando a seguinte propriedade:

```properties
spring.rabbitmq.addresses=seu_endereco_rabbitmq
```

## 🚀 Executando o Projeto

1. Primeiro, inicie o banco de dados:
```bash
docker-compose up -d
```

2. Execute o projeto usando Maven:
```bash
./mvnw spring-boot:run
```

O serviço estará disponível na porta padrão 8080.

## 📦 Estrutura do Projeto

```
src/main/java/com/ms/email/
├── config/
│   └── RabbitMQConfig.java
├── consumers/
│   └── EmailConsumer.java
├── dto/
│   └── EmailRecordDTO.java
├── email/
│   ├── EmailEntity.java
│   ├── repository/
│   │   └── EmailRepository.java
│   └── service/
│       └── EmailService.java
├── exception/
│   └── EmailFoundException.java
└── EmailApplication.java
```

## 🛠️ Funcionalidades

- Envio assíncrono de emails
- Persistência de histórico de emails enviados
- Fila de processamento com RabbitMQ
- Tratamento de exceções
- Validação de dados

## 🔄 Estados do Email

O serviço utiliza um enum `StatusEmail` para controlar os estados dos emails:
- ENVIADO
- ERRO

## 🔐 Perfis de Execução

O projeto possui dois perfis de execução:
- dev (desenvolvimento)
- prod (produção)

Para alterar o perfil, modifique a propriedade `spring.profiles.active` no arquivo `application.properties`.

## 📄 Licença

Este projeto está sob a licença [MIT](LICENSE).

## ✒️ Autores

* **Plataforma Zeelus** - *Desenvolvimento* - [Zeelus](https://github.com/zeelus) 