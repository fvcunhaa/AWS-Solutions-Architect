# Bancos de Dados na AWS

Este diretório reúne a documentação de estudo dos **serviços de banco de dados da AWS**, cobrindo modelos **relacionais, NoSQL, chave-valor, grafos, cache, ledger, data warehouse e bancos distribuídos**.

O objetivo é fornecer uma base sólida para **decisão arquitetural**, entendimento de **casos de uso**, **boas práticas** e **trade-offs** entre os diferentes serviços de banco de dados da AWS.

---

## 🎯 Visão Geral

A AWS oferece um dos portfólios de bancos de dados mais completos do mercado, permitindo escolher o banco **ideal para cada tipo de workload**, sem a necessidade de adaptação forçada de um único modelo.

Os serviços abordados neste diretório atendem cenários como:
- Aplicações transacionais
- Microsserviços
- Big Data e analytics
- Baixa latência
- Alta escalabilidade
- Governança e compliance
- Sistemas imutáveis e auditáveis

---

## 🧠 Serviços Abordados

### 🟦 Amazon RDS
Banco de dados relacional gerenciado que suporta múltiplos engines.

**Engines suportados:**
- MySQL
- PostgreSQL
- MariaDB
- Oracle
- SQL Server

📂 Pasta: `amazon-rds/`

---

### 🟩 Amazon Aurora
Banco relacional compatível com MySQL e PostgreSQL, otimizado para alta performance e disponibilidade.

**Destaques:**
- Performance superior ao RDS tradicional
- Alta disponibilidade nativa
- Escalabilidade automática de storage

📂 Pasta: `amazon-aurora/`

---

### ⚡ Amazon Aurora Serverless
Versão serverless do Aurora, com escalabilidade automática de capacidade.

**Principais usos:**
- Workloads intermitentes
- Ambientes dev/test
- Aplicações imprevisíveis

📂 Pasta: `amazon-aurora-serverless/`

---

### 🟠 Amazon DynamoDB
Banco NoSQL chave-valor e documentos, totalmente serverless.

**Principais usos:**
- Aplicações em escala massiva
- Baixa latência (single-digit ms)
- Arquiteturas event-driven

📂 Pasta: `amazon-dynamodb/`

---

### 🟣 Amazon DocumentDB (compatível com MongoDB)
Banco de documentos compatível com MongoDB, totalmente gerenciado.

**Principais usos:**
- Dados semiestruturados
- Migração de workloads MongoDB
- Catálogos e perfis

📂 Pasta: `amazon-documentdb/`

---

### 🔵 Amazon ElastiCache
Serviço de cache em memória compatível com Redis e Memcached.

**Principais usos:**
- Cache de dados
- Sessões de usuário
- Filas e pub/sub (Redis)

📂 Pasta: `amazon-elasticache/`

---

### 🟢 Amazon Keyspaces (for Apache Cassandra)
Banco NoSQL compatível com Cassandra, totalmente serverless.

**Principais usos:**
- Altíssima escala
- Escritas distribuídas
- Workloads time-series

📂 Pasta: `amazon-keyspaces/`

---

### 🟡 Amazon Neptune
Banco de dados orientado a grafos.

**Principais usos:**
- Grafos de relacionamento
- Recomendação
- Detecção de fraude
- Redes sociais

📂 Pasta: `amazon-neptune/`

---

### 🟤 Amazon Quantum Ledger Database (QLDB)
Banco ledger totalmente gerenciado, imutável e auditável.

**Principais usos:**
- Trilhas de auditoria
- Registros financeiros
- Compliance e rastreabilidade

📂 Pasta: `amazon-qldb/`

---

### 🔴 Amazon Redshift
Data warehouse totalmente gerenciado para analytics em larga escala.

**Principais usos:**
- BI e analytics
- Processamento de grandes volumes de dados
- Integração com data lakes

📂 Pasta: `amazon-redshift/`

---

## 🏗️ Organização do Diretório

Estrutura sugerida:
├── amazon-aurora/

├── amazon-aurora-serverless/

├── amazon-documentdb/

├── amazon-dynamodb/

├── amazon-elasticache/

├── amazon-keyspaces/

├── amazon-neptune/

├── amazon-qldb/

├── amazon-rds/

├── amazon-redshift/

└── README.md


Cada pasta conterá documentação detalhada seguindo o padrão:
- Visão Geral
- Conceitos
- Arquitetura
- Casos de Uso
- Boas Práticas
- Observações Finais

---

## 📌 Boas Práticas Gerais

- Escolha o banco baseado no **tipo de acesso**, não apenas familiaridade
- Separe workloads transacionais de analíticos
- Utilize serviços serverless quando possível
- Planeje alta disponibilidade e backup desde o início
- Monitore custo, performance e escalabilidade

---

## 📚 Público-Alvo

Este material é indicado para:
- Arquitetos Cloud
- Engenheiros de Software
- Engenheiros de Dados
- SRE / DevOps
- Profissionais que projetam arquiteturas modernas na AWS

---

## ✍️ Observações Finais

O uso correto dos serviços de banco de dados da AWS é fundamental para garantir **performance, escalabilidade, segurança e custo eficiente**.

Este diretório serve como base de estudo e referência prática para apoiar decisões arquiteturais e a construção de soluções robustas e modernas na nuvem AWS.

