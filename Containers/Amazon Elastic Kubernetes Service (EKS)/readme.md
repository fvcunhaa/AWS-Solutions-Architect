# Amazon Elastic Kubernetes Service (EKS) 

**Serviço:** Amazon Elastic Kubernetes Service (Amazon EKS)  
**Categoria:** Contêineres / Kubernetes gerenciado  
**Documentação oficial:** https://aws.amazon.com/pt/eks/

---

## Visão Geral

O **Amazon EKS** é o serviço gerenciado de **Kubernetes** da AWS que simplifica a criação, operação e escalabilidade de clusters Kubernetes na nuvem. A AWS gerencia o **control plane**, garantindo alta disponibilidade, segurança e conformidade, enquanto o cliente foca nos workloads.

O EKS é indicado para:
- Microsserviços em Kubernetes
- Plataformas de dados e streaming
- Machine learning e workloads intensivos
- Ambientes corporativos Kubernetes

---

## Conceitos

### Cluster Kubernetes
Conjunto de componentes que executam aplicações containerizadas, composto por **control plane** e **worker nodes**.

### Control Plane Gerenciado
A AWS gerencia:
- API Server
- Scheduler
- Controller Manager
- Alta disponibilidade e patches de segurança

### Worker Nodes
Executam os pods e podem ser:
- **EC2** (controle total)
- **AWS Fargate** (serverless)

### Namespaces
Isolamento lógico de recursos dentro do cluster.

### Integrações Nativas
- Amazon ECR (imagens)
- IAM (IRSA)
- VPC CNI
- CloudWatch (logs e métricas)
- ALB/NLB (exposição de serviços)

---

## Arquitetura – Plataforma de Dados com Amazon EKS



**Fonte oficial:**  
https://aws.amazon.com/pt/blogs/architecture/field-notes-building-a-data-service-for-autonomous-driving-systems-development-using-amazon-eks/

---

### Visão Geral da Arquitetura

<img width="594" height="307" alt="image" src="https://github.com/user-attachments/assets/81cbfc5c-0529-401a-9b7d-f1098818817d" />

Esta arquitetura demonstra o uso do **Amazon EKS** como núcleo de uma **plataforma de dados** para desenvolvimento de sistemas autônomos, integrando streaming, armazenamento de alto desempenho e analytics.

O objetivo é suportar **processamento intensivo, escalabilidade e baixa latência**, mantendo governança e observabilidade.

---

### Descrição do Fluxo

1. **Cliente (NICE DCV)**
   - Usuários acessam ambientes gráficos para análise e desenvolvimento

2. **Amazon VPC**
   - Isolamento de rede para todos os componentes
   - Subnets públicas e privadas distribuídas por AZ

3. **Amazon EKS**
   - Orquestra workloads containerizados
   - Executa serviços de processamento e ingestão

4. **Amazon MSK (Kafka)**
   - Streaming de dados em tempo real
   - Ingestão de grandes volumes de eventos

5. **Amazon S3**
   - Armazenamento durável de dados brutos
   - Data lake para processamento posterior

6. **Amazon FSx for Lustre**
   - Armazenamento de alto desempenho
   - Suporte a workloads intensivos de I/O

7. **Amazon Redshift**
   - Analytics e consultas em larga escala
   - Consumo de dados processados pelo EKS

---

## Casos de Uso

Os casos de uso abaixo são baseados na documentação oficial e no artigo de arquitetura:

### 1. Plataformas de dados e streaming
Execução de pipelines de ingestão e processamento em Kubernetes.

🔗 https://aws.amazon.com/pt/eks/

---

### 2. Workloads intensivos e distribuídos
Machine learning, simulações e processamento paralelo.

🔗 https://aws.amazon.com/pt/blogs/architecture/field-notes-building-a-data-service-for-autonomous-driving-systems-development-using-amazon-eks/

---

### 3. Microsserviços corporativos
Execução de aplicações escaláveis e resilientes.

🔗 https://aws.amazon.com/pt/eks/

---

### 4. Ambientes Kubernetes padronizados
Adoção de Kubernetes com governança e segurança gerenciadas.

🔗 https://aws.amazon.com/pt/eks/

---

## Boas Práticas

### Arquitetura
- Utilize múltiplas AZs para alta disponibilidade
- Separe workloads por namespaces
- Prefira serviços gerenciados para dependências (MSK, S3, Redshift)

---

### Segurança
- Use **IAM Roles for Service Accounts (IRSA)**
- Aplique Network Policies
- Mantenha o cluster atualizado

---

### Escalabilidade
- Configure HPA e Cluster Autoscaler
- Utilize Fargate para workloads event-driven
- Dimensione corretamente os node groups

---

### Operação
- Centralize logs e métricas
- Automatize deploys com GitOps/CI-CD
- Teste upgrades regularmente

---

## Observações Finais

O **Amazon EKS** é a escolha ideal para organizações que desejam **Kubernetes gerenciado com alto nível de controle**, integração nativa com a AWS e capacidade de escalar workloads complexos.

Ele combina a flexibilidade do Kubernetes com a confiabilidade da AWS, sendo indicado para **plataformas críticas, dados, microsserviços e aplicações modernas**.
