# Amazon DynamoDB 
**Serviço:** Amazon DynamoDB  
**Categoria:** Banco de Dados / NoSQL / Chave-Valor e Documentos  
**Documentação oficial:** https://aws.amazon.com/pt/dynamodb/

---

## Visão Geral

O **Amazon DynamoDB** é um banco de dados **NoSQL totalmente gerenciado e serverless**, projetado para oferecer **latência de milissegundos de um dígito em qualquer escala**. Ele elimina a necessidade de provisionar ou gerenciar servidores, sendo ideal para aplicações modernas e distribuídas.

É amplamente utilizado em arquiteturas:
- Serverless
- Event-driven
- Microsserviços
- Alta escala global

---

## Conceitos

### Tabela
Estrutura básica do DynamoDB, composta por itens e atributos.

### Chave Primária
- **Partition key** (obrigatória)
- **Sort key** (opcional)
Define como os dados são distribuídos e consultados.

### Item
Registro individual dentro de uma tabela.

### Modelo Serverless
- Sem gerenciamento de infraestrutura
- Escalabilidade automática
- Alta disponibilidade nativa

### Streams
Captura alterações (INSERT, MODIFY, REMOVE) para integração com outros serviços.

### Modos de Capacidade
- **On-Demand:** escala automática
- **Provisioned:** controle fino de throughput

---

## Arquitetura – Workflows Automatizados com DynamoDB



**Fonte oficial:**  
https://aws.amazon.com/pt/blogs/architecture/genomics-workflows-part-5-automated-benchmarking/

---

### Visão Geral da Arquitetura

<img width="648" height="322" alt="image" src="https://github.com/user-attachments/assets/e166d7c2-a828-4aae-8f75-8bff57cfc617" />


Esta arquitetura demonstra o uso do **Amazon DynamoDB como banco central** em um workflow automatizado, integrando **streams, eventos e orquestração serverless**.

O objetivo é criar pipelines altamente escaláveis e desacoplados, utilizando serviços gerenciados da AWS.

---

### Descrição do Fluxo

1. **Amazon DynamoDB Streams**
   - Captura alterações nos dados
   - Publica eventos de mudança

2. **Amazon EventBridge**
   - Recebe eventos do DynamoDB
   - Roteia eventos para workflows

3. **AWS Step Functions**
   - Orquestra o fluxo de processamento
   - Coordena múltiplas etapas

4. **AWS Lambda**
   - Executa lógica customizada
   - Processa dados e decisões

5. **AWS Batch**
   - Executa workloads intensivos ou de longa duração

6. **AWS Cloud Financial Management**
   - Analisa custos e métricas do processamento

7. **Amazon DynamoDB**
   - Armazena estado e resultados do workflow

---

## Casos de Uso

Os casos de uso abaixo são baseados na documentação oficial da AWS:

### 1. Aplicações serverless
Backends escaláveis sem gerenciamento de servidores.

🔗 https://aws.amazon.com/pt/dynamodb/

---

### 2. Sistemas event-driven
Reação a eventos em tempo real usando streams.

🔗 https://aws.amazon.com/pt/dynamodb/

---

### 3. Microsserviços em larga escala
Armazenamento desacoplado e altamente disponível.

🔗 https://aws.amazon.com/pt/dynamodb/

---

### 4. Workflows distribuídos
Orquestração de processos complexos com Step Functions.

🔗 https://aws.amazon.com/pt/blogs/architecture/genomics-workflows-part-5-automated-benchmarking/

---

## Boas Práticas

### Arquitetura
- Modele dados baseado nos padrões de acesso
- Evite scans sempre que possível
- Utilize índices secundários corretamente

---

### Performance
- Escolha corretamente o modo de capacidade
- Utilize chaves bem distribuídas
- Monitore latência e throughput

---

### Segurança
- Utilize criptografia em repouso e em trânsito
- Controle acesso com IAM
- Restrinja acesso via VPC endpoints

---

### Operação
- Monitore métricas no CloudWatch
- Utilize TTL para expiração automática
- Planeje estratégias de backup e restore

---

## Observações Finais

O **Amazon DynamoDB** é um dos pilares das arquiteturas modernas na AWS, oferecendo **escala massiva, simplicidade operacional e integração profunda com serviços serverless**.

Ele é ideal para aplicações que exigem **baixa latência, alta disponibilidade e elasticidade automática**, sendo uma escolha estratégica para soluções globais e distribuídas.
