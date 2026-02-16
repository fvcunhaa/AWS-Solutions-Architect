# Web and Mobile Front-End na AWS

Este diretório reúne a documentação de estudo dos principais serviços da AWS voltados para **desenvolvimento, hospedagem, distribuição e integração de aplicações Web e Mobile**.

O objetivo é fornecer uma visão clara das soluções disponíveis para construção de:

- Aplicações Web modernas (SPA, SSR, estáticas)
- Aplicações Mobile (iOS, Android, híbridas)
- Aplicações Serverless com front-end desacoplado
- Experiências omnichannel

---

## 🎯 Visão Geral

A AWS oferece serviços que suportam toda a camada de front-end, incluindo:

- Hospedagem de aplicações
- Distribuição global via CDN
- Autenticação de usuários
- Integração com APIs e back-end serverless
- Sincronização offline
- Analytics e notificações

Esses serviços permitem criar aplicações altamente escaláveis, seguras e distribuídas globalmente.

---

## 🧠 Serviços Abordados

### 🟢 AWS Amplify
Plataforma para desenvolvimento full-stack com foco em front-end.

**Principais recursos:**
- Hosting automático
- CI/CD integrado
- Integração com API (AppSync / API Gateway)
- Autenticação com Cognito
- DataStore com sincronização offline

📂 Pasta: `aws-amplify/`

---

### 🔵 Amazon CloudFront
Rede de distribuição de conteúdo (CDN).

**Principais usos:**
- Distribuição global de aplicações
- Cache de conteúdo estático
- Proteção contra DDoS
- Integração com S3 e ALB

📂 Pasta: `amazon-cloudfront/`

---

### 🟣 Amazon S3 (Static Hosting)
Hospedagem de sites estáticos.

**Principais usos:**
- SPAs (React, Vue, Angular)
- Landing pages
- Documentações
- Portais institucionais

📂 Pasta: `amazon-s3-static-hosting/`

---

### 🟠 Amazon API Gateway
Exposição de APIs para consumo web e mobile.

**Principais usos:**
- REST APIs
- HTTP APIs
- WebSocket APIs
- Backend para aplicações SPA

📂 Pasta: `amazon-api-gateway/`

---

### 🟡 AWS AppSync
API GraphQL gerenciada.

**Principais recursos:**
- Subscriptions em tempo real
- Sincronização offline
- Integração com DynamoDB
- Integração com Lambda

📂 Pasta: `aws-appsync/`

---

### 🔴 Amazon Cognito
Serviço de autenticação e gerenciamento de usuários.

**Principais recursos:**
- Login social (Google, Facebook, Apple)
- MFA
- JWT Tokens
- User Pools e Identity Pools

📂 Pasta: `amazon-cognito/`

---

### 🟤 AWS Device Farm
Testes automatizados para aplicações mobile.

📂 Pasta: `aws-device-farm/`

---

## 🏗️ Organização do Diretório

Estrutura sugerida:
.
├── aws-amplify/
├── amazon-cloudfront/
├── amazon-s3-static-hosting/
├── amazon-api-gateway/
├── aws-appsync/
├── amazon-cognito/
├── aws-device-farm/
└── README.md


Cada serviço seguirá o padrão:

- Visão Geral
- Conceitos
- Arquitetura
- Casos de Uso
- Boas Práticas
- Observações Finais

---

## 🔄 Arquitetura Moderna de Front-End na AWS

Modelo comum:

1. Front-end hospedado em S3
2. Distribuição via CloudFront
3. Autenticação via Cognito
4. API via API Gateway ou AppSync
5. Backend serverless com Lambda
6. Banco de dados (DynamoDB / Aurora)
7. Observabilidade com CloudWatch e X-Ray

Esse modelo permite:

- Escalabilidade automática
- Baixo custo operacional
- Alta disponibilidade
- Deploy contínuo

---

## 📌 Boas Práticas Gerais

- Utilize CloudFront sempre na frente do S3
- Configure HTTPS com ACM
- Implemente autenticação segura com Cognito
- Separe ambientes (dev / stage / prod)
- Automatize deploy com Amplify ou CodePipeline
- Habilite WAF quando exposto publicamente

---

## 📚 Público-Alvo

Este material é indicado para:

- Desenvolvedores Front-End
- Desenvolvedores Mobile
- Engenheiros Full-Stack
- DevOps Engineers
- Arquitetos Cloud

---

## ✍️ Observações Finais

A AWS fornece um ecossistema completo para construção de aplicações Web e Mobile modernas, combinando:

- Hospedagem global
- Autenticação gerenciada
- APIs escaláveis
- Backend serverless
- Integração contínua

Esse diretório servirá como base para padronização arquitetural e estudo aprofundado de soluções front-end na AWS.

