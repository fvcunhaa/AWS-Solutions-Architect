# Amazon Aurora Serverless 
**Serviço:** Amazon Aurora Serverless  
**Categoria:** Banco de Dados / Relacional serverless  
**Documentação oficial:** https://aws.amazon.com/pt/rds/aurora/serverless/

---

## Visão Geral

O **Amazon Aurora Serverless** é uma opção **serverless** do Amazon Aurora que ajusta automaticamente a **capacidade de computação** do banco de dados conforme a demanda, sem necessidade de provisionar ou gerenciar instâncias.

Ele é ideal para workloads:
- Intermitentes ou imprevisíveis
- Ambientes de desenvolvimento e teste
- Aplicações com variação significativa de carga
- Casos onde simplicidade operacional é prioridade

---

## Conceitos

### Arquitetura Serverless
- Não há instâncias fixas de banco de dados
- Capacidade é medida em **Aurora Capacity Units (ACUs)**
- Escala automaticamente para cima ou para baixo

### Cluster Aurora Serverless
- Possui endpoints de leitura e escrita
- Gerencia failover e disponibilidade automaticamente

### Alta Disponibilidade
- Storage distribuído em múltiplas AZs
- Failover automático sem intervenção manual

### Escalabilidade Automática
- Ajuste de capacidade conforme carga
- Redução de custo em períodos ociosos

### Compatibilidade
- Compatível com **MySQL** e **PostgreSQL**
- Suporte a aplicações e ferramentas existentes

---

## Arquitetura – Plataforma de Dados com Aurora Serverless



**Fonte oficial:**  
https://aws.amazon.com/pt/blogs/aws-brasil/inteligencia-artificial-no-mercado-financeiro/

---

### Visão Geral da Arquitetura
<img width="788" height="591" alt="image" src="https://github.com/user-attachments/assets/306a5d5f-ec19-45fb-8377-4f205a0c0737" />

Esta arquitetura demonstra o uso do **Amazon Aurora Serverless** como banco de dados relacional central em uma **plataforma distribuída**, integrada a serviços de analytics e processamento de dados.

O foco é oferecer **alta disponibilidade, escalabilidade automática e custo eficiente**, sem gerenciamento manual de instâncias.

---

### Descrição do Fluxo

1. **Clientes Corporativos**
   - Acessam aplicações via VPN
   - Conectam-se de forma segura ao ambiente AWS

2. **Application Load Balancer**
   - Distribui requisições entre aplicações
   - Garante alta disponibilidade

3. **Auto Scaling Group (Aplicação)**
   - Executa a camada de aplicação
   - Escala horizontalmente conforme demanda

4. **Amazon Aurora Serverless Cluster**
   - Banco de dados relacional serverless
   - Ajusta capacidade automaticamente
   - Distribuído em múltiplas AZs

5. **Integrações Analíticas**
   - Amazon S3 para data lake
   - AWS Glue Catalog para metadados
   - Amazon Athena para consultas
   - Databricks para processamento avançado

---

## Casos de Uso

Os casos de uso abaixo são baseados na documentação e no artigo oficial da AWS:

### 1. Workloads intermitentes
Aplicações que não possuem carga constante ao longo do tempo.

🔗 https://aws.amazon.com/pt/rds/aurora/serverless/

---

### 2. Ambientes de desenvolvimento e teste
Redução de custo e simplicidade operacional.

🔗 https://aws.amazon.com/pt/rds/aurora/serverless/

---

### 3. Plataformas analíticas e financeiras
Integração com serviços de analytics e big data.

🔗 https://aws.amazon.com/pt/blogs/aws-brasil/inteligencia-artificial-no-mercado-financeiro/

---

### 4. Aplicações com crescimento imprevisível
Escalabilidade automática sem planejamento prévio de capacidade.

🔗 https://aws.amazon.com/pt/rds/aurora/serverless/

---

## Boas Práticas

### Arquitetura
- Utilize subnets privadas para o banco
- Planeje endpoints corretamente
- Separe camada de aplicação e banco

---

### Performance
- Defina limites mínimos e máximos de ACU adequados
- Monitore latência e throughput
- Avalie compatibilidade com o workload

---

### Segurança
- Ative criptografia em repouso e em trânsito
- Controle acesso com Security Groups
- Restrinja conectividade via VPC

---

### Custos
- Ajuste limites de capacidade para evitar picos desnecessários
- Utilize para workloads variáveis
- Monitore consumo regularmente

---

## Observações Finais

O **Amazon Aurora Serverless** é uma excelente opção para quem busca **banco de dados relacional com simplicidade operacional**, eliminando a necessidade de gerenciar instâncias e capacidade.

Ele se destaca em cenários onde **elasticidade e custo eficiente** são mais importantes do que controle detalhado de infraestrutura, sendo uma escolha estratégica para arquiteturas modernas e dinâmicas.
