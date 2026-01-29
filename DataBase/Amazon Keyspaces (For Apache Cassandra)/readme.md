# Amazon Keyspaces (for Apache Cassandra) – Documentação de Estudo

**Serviço:** Amazon Keyspaces (for Apache Cassandra)  
**Categoria:** Banco de Dados / NoSQL / Wide-column  
**Documentação oficial:** https://aws.amazon.com/pt/keyspaces/

---

## Visão Geral

O **Amazon Keyspaces (for Apache Cassandra)** é um serviço **NoSQL serverless** compatível com **Apache Cassandra**, projetado para executar workloads de **alta escala, alta taxa de escrita e baixa latência**, sem a necessidade de gerenciar infraestrutura.

Ele elimina a complexidade de operar clusters Cassandra, oferecendo **escalabilidade automática, alta disponibilidade e pagamento por uso**.

---

## Conceitos

### Modelo Wide-Column
- Dados organizados em **keyspaces** e **tabelas**
- Ideal para grandes volumes de dados distribuídos
- Acesso eficiente por chave de partição

### Compatibilidade com Apache Cassandra
- Compatível com **CQL (Cassandra Query Language)**
- Drivers Cassandra existentes funcionam sem alterações significativas

### Serviço Serverless
- Sem gerenciamento de nós ou clusters
- Escalabilidade automática de throughput
- Alta disponibilidade nativa

### Capacidade
- **On-Demand:** escala automaticamente
- **Provisioned:** controle explícito de leitura e escrita

### Segurança e Durabilidade
- Criptografia em repouso e em trânsito
- Replicação automática multi-AZ

---

## Arquitetura – API Serverless com Amazon Keyspaces


::contentReference[oaicite:0]{index=0}


**Fonte oficial:**  
https://aws.amazon.com/pt/blogs/aws/new-amazon-keyspaces-for-apache-cassandra-is-now-generally-available/

---

### Visão Geral da Arquitetura

<img width="588" height="291" alt="image" src="https://github.com/user-attachments/assets/a707ffbf-3553-4e7d-b29c-d2c33cfdfcfc" />


Esta arquitetura demonstra o uso do **Amazon Keyspaces** como banco de dados NoSQL backend em uma **arquitetura serverless**, acessada por meio de APIs.

O objetivo é oferecer **baixa latência, alta escalabilidade e simplicidade operacional**, integrando serviços totalmente gerenciados da AWS.

---

### Descrição do Fluxo

1. **Usuários**
   - Enviam requisições HTTP para a aplicação

2. **Amazon API Gateway**
   - Expõe endpoints REST
   - Gerencia autenticação e throttling

3. **AWS Lambda**
   - Processa requisições
   - Executa lógica de negócio
   - Interage com o Amazon Keyspaces

4. **Amazon Keyspaces**
   - Armazena dados em tabelas Cassandra
   - Escala automaticamente conforme demanda
   - Retorna dados com baixa latência

---

## Casos de Uso

Os casos de uso abaixo são baseados na documentação oficial da AWS:

### 1. Aplicações em escala massiva
Sistemas que exigem milhões de operações por segundo.

🔗 https://aws.amazon.com/pt/keyspaces/

---

### 2. Workloads time-series
Armazenamento de eventos, métricas e logs.

🔗 https://aws.amazon.com/pt/keyspaces/

---

### 3. Microsserviços distribuídos
Backends altamente disponíveis e desacoplados.

🔗 https://aws.amazon.com/pt/keyspaces/

---

### 4. Migração de Cassandra autogerenciado
Modernização de clusters Cassandra on-premises ou em outras nuvens.

🔗 https://aws.amazon.com/pt/blogs/aws/new-amazon-keyspaces-for-apache-cassandra-is-now-generally-available/

---

## Boas Práticas

### Arquitetura
- Modele dados com foco em padrões de acesso
- Escolha corretamente a chave de partição
- Evite consultas que exijam varredura completa

---

### Performance
- Utilize capacidade on-demand para cargas imprevisíveis
- Monitore latência e throughput
- Distribua bem as chaves para evitar hotspots

---

### Segurança
- Utilize IAM para controle de acesso
- Restrinja conectividade via VPC endpoints
- Ative criptografia sempre que possível

---

### Operação
- Monitore métricas no CloudWatch
- Planeje TTL para dados temporários
- Teste consultas em ambientes não produtivos

---

## Observações Finais

O **Amazon Keyspaces** é ideal para workloads que exigem **escala extrema, baixa latência e simplicidade operacional**, mantendo compatibilidade com Apache Cassandra.

Ele é especialmente indicado para **aplicações distribuídas, time-series e microsserviços**, onde o gerenciamento tradicional de clusters se torna um gargalo operacional.
