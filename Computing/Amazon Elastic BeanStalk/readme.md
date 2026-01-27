# AWS Elastic Beanstalk 
**Serviço:** AWS Elastic Beanstalk  
**Categoria:** Computação / Plataforma como Serviço (PaaS)  
**Documentação oficial:** https://aws.amazon.com/pt/elasticbeanstalk/

---

## Visão Geral

O **AWS Elastic Beanstalk** é um serviço de **plataforma como serviço (PaaS)** que simplifica o deploy, gerenciamento e escalabilidade de aplicações na AWS. Ele abstrai a complexidade da infraestrutura, permitindo que os times foquem no **código da aplicação**, enquanto a AWS gerencia provisionamento, balanceamento de carga, escalabilidade e monitoramento.

É amplamente utilizado para:
- Deploy rápido de aplicações web e APIs
- Padronização de ambientes
- Redução de esforço operacional
- Times que não querem gerenciar infraestrutura detalhadamente

---

## Conceitos

### Aplicação
Contêiner lógico que agrupa versões, ambientes e configurações relacionadas a um sistema.

### Ambiente
Conjunto de recursos AWS que executam uma versão específica da aplicação (ex.: ambiente de produção ou homologação).

### Plataforma
Stack gerenciado que define linguagem e runtime, como:
- Java
- .NET
- Node.js
- Python
- Docker

### Versionamento
Cada deploy gera uma **Application Version**, permitindo rollback rápido.

### Gerenciamento de Infraestrutura
O Elastic Beanstalk provisiona automaticamente:
- Amazon EC2
- Auto Scaling
- Elastic Load Balancer
- Monitoramento via CloudWatch

---

## Arquitetura – Elastic Beanstalk em Arquitetura Corporativa



**Fonte oficial:**  
https://aws.amazon.com/pt/blogs/architecture/how-facteus-improved-quantamatics-performance-by-adopting-amazon-aurora-serverless-and-amazon-eks/

---

### Visão Geral da Arquitetura
<img width="783" height="430" alt="image" src="https://github.com/user-attachments/assets/defe95f5-87df-423d-8838-061c175727f2" />

Esta arquitetura demonstra o uso do **AWS Elastic Beanstalk** como camada central para execução de **APIs e aplicações corporativas**, integrando-se com serviços de frontend, bancos de dados e sistemas analíticos.

O objetivo é fornecer **simplicidade operacional**, mantendo escalabilidade, segurança e performance.

---

### Descrição do Fluxo

1. **Usuários Web e Plugins**
   - Usuários acessam a aplicação via navegador ou plugins (ex.: Excel)

2. **Amazon CloudFront**
   - Distribui conteúdo estático e interface
   - Reduz latência e melhora performance

3. **AWS Elastic Beanstalk**
   - Hospeda a API e a lógica da aplicação
   - Gerencia automaticamente EC2, Auto Scaling e Load Balancer

4. **Amazon EC2 (Instâncias da Aplicação)**
   - Executam a aplicação
   - Escalam automaticamente conforme demanda

5. **Amazon EFS**
   - Armazena arquivos compartilhados
   - Disponível para múltiplas instâncias

6. **Amazon RDS / Aurora**
   - Persistência de dados transacionais

7. **Integrações Externas**
   - Conexão com data warehouses e serviços analíticos (ex.: Snowflake)

---

## Casos de Uso

Os casos de uso abaixo são baseados na documentação oficial e no artigo de arquitetura:

### 1. Deploy rápido de aplicações web
Ideal para times que precisam subir aplicações rapidamente sem gerenciar infraestrutura.

🔗 https://aws.amazon.com/pt/elasticbeanstalk/

---

### 2. Padronização de ambientes
Ambientes consistentes entre desenvolvimento, homologação e produção.

🔗 https://aws.amazon.com/pt/elasticbeanstalk/

---

### 3. Escalabilidade automática de aplicações
Auto Scaling gerenciado sem configuração manual complexa.

🔗 https://aws.amazon.com/pt/elasticbeanstalk/

---

### 4. Aplicações corporativas integradas
Execução de APIs que se integram com bancos de dados e plataformas analíticas.

🔗 https://aws.amazon.com/pt/blogs/architecture/how-facteus-improved-quantamatics-performance-by-adopting-amazon-aurora-serverless-and-amazon-eks/

---

## Boas Práticas

### Arquitetura
- Separe ambientes por aplicação e finalidade
- Use VPCs privadas para bancos de dados
- Combine com CloudFront para frontend

---

### Operação
- Utilize versionamento para rollback rápido
- Automatize deploys com CI/CD
- Monitore saúde do ambiente via console

---

### Custos
- Ajuste corretamente tamanho das instâncias
- Utilize Auto Scaling para variação de carga
- Combine com Savings Plans quando aplicável

---

### Segurança
- Utilize IAM Roles para instâncias
- Restrinja acesso via Security Groups
- Mantenha plataformas e runtimes atualizados

---

## Observações Finais

O AWS Elastic Beanstalk é ideal para equipes que desejam **simplicidade operacional sem abrir mão de escalabilidade e boas práticas**. Ele ocupa um espaço intermediário entre infraestrutura totalmente gerenciada e controle total via EC2.

Para arquiteturas mais complexas ou altamente customizadas, serviços como **EKS** ou **EC2 puro** podem ser mais indicados. Para a maioria das aplicações corporativas, o Elastic Beanstalk oferece excelente custo-benefício e velocidade de entrega.
