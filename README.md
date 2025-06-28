# Microservice-Email

Projeto de microsserviços desenvolvido em Java 20 com Spring Boot para gerenciar usuários e envio de emails.  
O sistema é dividido em dois microserviços principais:

- **User Service**: responsável pela gestão de usuários.
- **Email Service**: responsável pelo envio de emails.

A comunicação entre os microserviços é feita via **RabbitMQ**, utilizando filas para o processamento assíncrono de mensagens.

---

## Tecnologias Utilizadas

- Java 20
- Spring Boot
- RabbitMQ
- Maven
- PostgreSQL (presumido, pode ajustar conforme seu banco)
- Git e GitHub para controle de versão

---

## Estrutura do Projeto

```
Microservice-Email/
├── email/          # Microserviço responsável pelo envio de emails
├── user/           # Microserviço responsável pela gestão de usuários
```

---

## Como Executar

### Pré-requisitos

- Java 20 instalado
- Maven instalado
- RabbitMQ rodando localmente ou em servidor acessível
- Banco de dados configurado (ex: PostgreSQL)
- Configurar as propriedades no arquivo `application.properties` de cada microserviço conforme seu ambiente

### Passos para rodar localmente

1. Clone o repositório:

```bash
git clone https://github.com/MarcosFelipeDSilva/Microservice-Email.git
cd Microservice-Email
```

2. Execute cada microserviço separadamente:

No terminal 1 (User Service):

```bash
cd user
mvn spring-boot:run
```

No terminal 2 (Email Service):

```bash
cd email
mvn spring-boot:run
```

---

## Configurações Importantes

- **RabbitMQ:**  
  Configure o host, usuário e senha no arquivo `application.properties` de ambos os microserviços para garantir que a comunicação funcione corretamente.

- **Banco de Dados:**  
  Ajuste as configurações do banco (URL, usuário, senha) nos arquivos `application.properties`.

---

## Como Funciona

- O **User Service** gerencia os dados dos usuários e publica mensagens na fila do RabbitMQ para acionar o envio de emails.
- O **Email Service** consome as mensagens da fila e envia os emails conforme as informações recebidas.
