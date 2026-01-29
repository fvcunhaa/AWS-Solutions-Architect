# Amazon Elastic Container Service (ECS)

**Serviço:** Amazon Elastic Container Service (Amazon ECS)  
**Categoria:** Contêineres / Orquestração  
**Documentação oficial:** https://aws.amazon.com/pt/ecs/

---

## Visão Geral

O **Amazon ECS** é o orquestrador de contêineres **nativo da AWS**, projetado para executar, gerenciar e escalar aplicações containerizadas de forma simples e altamente integrada ao ecossistema AWS.

O ECS permite executar contêineres usando:
- **Amazon EC2** (controle total da infraestrutura)
- **AWS Fargate** (modelo serverless, sem gerenciamento de servidores)

É amplamente utilizado para:
- Microsserviços
- APIs e backends
- Processamento assíncrono
- Workloads containerizados corporativos

---

## Conceitos

### Cluster ECS
Conjunto lógico onde os serviços e tasks são executados.

### Task Definition
Especificação de como um contêiner deve rodar, incluindo:
- Imagem
- CPU e memória
- Variáveis de ambiente
- Portas e volumes

### Task
Instância em execução de uma task definition.

### Service
Mantém um número desejado de tasks em execução, garantindo alta disponibilidade.

### Launch Types
- **EC2:** execução sobre instâncias EC2 gerenciadas pelo cliente
- **Fargate:** execução serverless, gerenciada pela AWS

### Integrações Nativas
- Amazon ECR
- IAM
- VPC
- CloudWatch
- Application Load Balancer

---

## Arquitetura – Microsserviços Java no ECS com AWS Fargate



**Fonte oficial:**  
https://docs.aws.amazon.com/pt_br/prescriptive-guidance/latest/patterns/deploy-java-microservices-on-amazon-ecs-using-aws-fargate.html

---

### Visão Geral da Arquitetura
<img width="561" height="385" alt="image" src="https://github.com/user-attachments/assets/5aa49254-cc03-4c65-b674-825eac7173d9" />

Esta arquitetura demonstra a execução de **microsserviços em contêineres** utilizando **Amazon ECS com AWS Fargate**, eliminando a necessidade de gerenciar servidores.

O objetivo é fornecer:
- Escalabilidade automática
- Isolamento por serviço
- Simplicidade operacional
- Alta disponibilidade

---

### Descrição do Fluxo

1. **Cliente**
   - Envia requisições HTTP (GET, POST, PUT, DELETE)
   - Recebe respostas JSON da aplicação

2. **Amazon VPC**
   - Fornece isolamento de rede
   - Contém subnets privadas e públicas

3. **Amazon ECS Cluster**
   - Gerencia tasks e serviços
   - Orquestra execução dos contêineres

4. **AWS Fargate**
   - Executa as tasks de forma serverless
   - Provisiona automaticamente CPU e memória

5. **Tasks ECS**
   - Executam os microsserviços
   - Escalam automaticamente conforme demanda

6. **Observabilidade**
   - Logs e métricas enviados ao Amazon CloudWatch
   - Monitoramento contínuo da aplicação

---

## Casos de Uso

Os casos de uso abaixo são baseados na documentação oficial:

### 1. Microsserviços serverless
Execução de APIs e serviços desacoplados sem gerenciar infraestrutura.

🔗 https://aws.amazon.com/pt/ecs/

---

### 2. Backends escaláveis
Aplicações que precisam escalar automaticamente conforme tráfego.

🔗 https://aws.amazon.com/pt/ecs/

---

### 3. Modernização de aplicações
Migração de aplicações monolíticas para contêineres.

🔗 https://docs.aws.amazon.com/pt_br/prescriptive-guidance/latest/patterns/deploy-java-microservices-on-amazon-ecs-using-aws-fargate.html

---

### 4. Execução integrada com CI/CD
Deploy contínuo de contêineres a partir do Amazon ECR.

🔗 https://aws.amazon.com/pt/ecs/

---

## Boas Práticas

### Arquitetura
- Prefira **AWS Fargate** para reduzir esforço operacional
- Separe serviços por domínio
- Utilize ALB para balanceamento de carga

---

### Segurança
- Utilize IAM Roles por task
- Restrinja acesso via Security Groups
- Evite segredos hardcoded (use Secrets Manager)

---

### Escalabilidade
- Configure Auto Scaling baseado em métricas
- Ajuste corretamente CPU e memória
- Utilize health checks eficazes

---

### Operação
- Monitore logs e métricas
- Versione task definitions
- Automatize deploys com pipelines CI/CD

---

## Observações Finais

O Amazon ECS é uma solução robusta e simples para **orquestração de contêineres na AWS**, especialmente quando combinado com **AWS Fargate**, que elimina a complexidade de gerenciar servidores.

Ele é ideal para equipes que desejam **produtividade, integração nativa e escalabilidade**, sem a sobrecarga operacional típica de clusters Kubernetes.
