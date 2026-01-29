# Amazon DocumentDB (compatível com MongoDB)

**Serviço:** Amazon DocumentDB (with MongoDB compatibility)  
**Categoria:** Banco de Dados / NoSQL / Documentos  
**Documentação oficial:** https://aws.amazon.com/pt/documentdb/

---

## Visão Geral

O **Amazon DocumentDB** é um banco de dados **NoSQL orientado a documentos**, totalmente gerenciado, compatível com **MongoDB**, projetado para oferecer **escala, alta disponibilidade e durabilidade** sem a complexidade operacional de gerenciar clusters MongoDB por conta própria.

Ele é indicado para aplicações modernas que trabalham com **dados semiestruturados**, esquemas flexíveis e grande volume de leitura e escrita.

---

## Conceitos

### Modelo de Documento
- Armazena dados em formato **JSON-like (BSON)**
- Estrutura flexível, sem schema rígido

### Compatibilidade com MongoDB
- Compatível com APIs e drivers do MongoDB
- Facilita migração de aplicações existentes

### Cluster DocumentDB
- 1 instância **primary**
- Até 15 **read replicas**
- Replicação automática em múltiplas AZs

### Storage Distribuído
- Storage desacoplado do compute
- Crescimento automático até **128 TB**
- Alta durabilidade e tolerância a falhas

### Escalabilidade de Leitura
- Leitura distribuída por réplicas
- Ideal para workloads read-heavy

---

## Arquitetura – Auto Scaling de Leitura no Amazon DocumentDB



**Fonte oficial:**  
https://aws.amazon.com/pt/blogs/database/amazon-documentdb-with-mongodb-compatibility-read-autoscaling/

---

### Visão Geral da Arquitetura

<img width="628" height="249" alt="image" src="https://github.com/user-attachments/assets/4b656753-3cff-4a50-aa1c-d4a38f613dc3" />

Esta arquitetura demonstra como implementar **auto scaling de leitura** em um cluster do **Amazon DocumentDB**, utilizando serviços serverless da AWS para ajustar automaticamente o número de **read replicas** conforme a demanda.

O objetivo é garantir **performance consistente**, elasticidade e otimização de custos.

---

### Descrição do Fluxo

1. **Amazon CloudWatch**
   - Monitora métricas do cluster (CPU, conexões, latência)
   - Dispara alarmes conforme limites configurados

2. **Scaling Policy**
   - Define regras de scale in e scale out
   - Baseada em métricas do CloudWatch

3. **Amazon API Gateway**
   - Expõe endpoints REST
   - Permite acionamento controlado das funções Lambda

4. **AWS Lambda (GET)**
   - Consulta status do cluster DocumentDB
   - Retorna informações operacionais

5. **AWS Lambda (PATCH)**
   - Ajusta o número de read replicas
   - Executa ações de escalabilidade

6. **Amazon DocumentDB Cluster**
   - Primary instance para escrita
   - Read replicas para leitura escalável

---

## Casos de Uso

Os casos de uso abaixo são baseados na documentação oficial da AWS:

### 1. Aplicações com dados semiestruturados
Catálogos, perfis de usuários e conteúdos dinâmicos.

🔗 https://aws.amazon.com/pt/documentdb/

---

### 2. Migração de MongoDB para AWS
Modernização de workloads MongoDB on-premises ou em outras nuvens.

🔗 https://aws.amazon.com/pt/documentdb/

---

### 3. Workloads com alta leitura
Aplicações que exigem escalabilidade de leitura horizontal.

🔗 https://aws.amazon.com/pt/blogs/database/amazon-documentdb-with-mongodb-compatibility-read-autoscaling/

---

### 4. Arquiteturas serverless e event-driven
Integração com Lambda, API Gateway e microsserviços.

🔗 https://aws.amazon.com/pt/documentdb/

---

## Boas Práticas

### Arquitetura
- Planeje corretamente o número de read replicas
- Separe leitura e escrita na aplicação
- Utilize subnets privadas para o cluster

---

### Performance
- Crie índices adequados
- Evite documentos excessivamente grandes
- Monitore latência e throughput

---

### Segurança
- Utilize criptografia em repouso e em trânsito
- Controle acesso com Security Groups
- Restrinja acesso via VPC

---

### Operação
- Monitore métricas no CloudWatch
- Automatize escalabilidade quando necessário
- Teste failover periodicamente

---

## Observações Finais

O **Amazon DocumentDB** é uma solução robusta para workloads **NoSQL orientados a documentos**, oferecendo **compatibilidade com MongoDB**, alta disponibilidade e escalabilidade sem a complexidade de gerenciamento manual.

Ele é ideal para aplicações modernas que exigem **flexibilidade de schema, performance previsível e integração nativa com o ecossistema AWS**.
