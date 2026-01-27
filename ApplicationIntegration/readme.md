# Integração de Aplicações na AWS

Este diretório reúne documentação, exemplos e boas práticas relacionadas aos principais **serviços de integração de aplicações da AWS**.  
O objetivo é centralizar o conhecimento sobre arquiteturas orientadas a eventos, mensageria, orquestração e integração entre sistemas distribuídos.

---

## 🎯 Objetivo

- Documentar os serviços de integração da AWS
- Apoiar decisões de arquitetura
- Facilitar o entendimento do papel de cada serviço
- Servir como base para estudos, PoCs e projetos reais

---

## 🧩 Serviços Abordados

### 🔄 Amazon AppFlow
Serviço gerenciado para **integração de dados entre aplicações SaaS e a AWS**, sem necessidade de código.

**Principais usos:**
- Sincronização de dados entre SaaS (Salesforce, Slack, etc.) e AWS
- ETL simples e automatizado
- Integração rápida com serviços como S3, Redshift e EventBridge

---

### 🌐 AWS AppSync
Serviço gerenciado para criação de **APIs GraphQL**, com integração nativa a múltiplas fontes de dados.

**Principais usos:**
- APIs GraphQL escaláveis
- Integração com DynamoDB, Lambda e Aurora
- Atualizações em tempo real (subscriptions)

---

### ⚡ Amazon EventBridge
Barramento de eventos serverless para **arquiteturas orientadas a eventos**.

**Principais usos:**
- Comunicação desacoplada entre serviços
- Integração entre aplicações AWS e SaaS
- Reação a eventos de serviços AWS

---

### 📨 Amazon MQ
Serviço gerenciado de **brokers de mensagens** compatível com protocolos tradicionais.

**Principais usos:**
- Migração de aplicações legadas
- Uso de ActiveMQ ou RabbitMQ
- Integração com sistemas on-premises

---

### 📢 Amazon Simple Notification Service (SNS)
Serviço de **publicação e assinatura (pub/sub)** para envio de mensagens.

**Principais usos:**
- Fan-out de mensagens
- Notificações assíncronas
- Integração com SQS, Lambda, HTTP/S, SMS e e-mail

---

### 📬 Amazon Simple Queue Service (SQS)
Serviço de **filas de mensagens totalmente gerenciado**.

**Principais usos:**
- Processamento assíncrono
- Desacoplamento entre sistemas
- Controle de carga e tolerância a falhas

**Tipos de fila:**
- Standard
- FIFO

---

### 🔁 AWS Step Functions
Serviço de **orquestração de workflows**, permitindo coordenar múltiplos serviços AWS.

**Principais usos:**
- Fluxos complexos de negócio
- Orquestração de Lambdas e serviços AWS
- Controle de estados, retries e erros

---

## 🏗️ Organização do Diretório

Sugestão de estrutura:

.
├── appflow/

├── appsync/

├── eventbridge/

├── amazon-mq/

├── sns/

├── sqs/

├── step-functions/

└── README.md


Cada pasta pode conter:
- Conceitos
- Exemplos de arquitetura
- Casos de uso
- Diagramas
- Boas práticas

---

## 📌 Observações

- Os serviços podem ser usados **de forma complementar**
- A escolha depende de fatores como:
  - Latência
  - Volume de mensagens
  - Complexidade do fluxo
  - Integrações legadas vs serverless

---

## 📚 Referências

- Documentação oficial da AWS
- Whitepapers de arquitetura
- Experiências práticas do time

---

## ✍️ Contribuições

Este material está em evolução contínua.  
Sugestões, melhorias e novos exemplos são bem-vindos.
