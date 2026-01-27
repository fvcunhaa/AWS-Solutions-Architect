# AWS Cost and Usage Report (CUR) 
**Serviço:** AWS Cost and Usage Report (Relatório de Uso e Custo)  
**Categoria:** Gerenciamento de custos / Análise financeira  
**Documentação oficial:** https://aws.amazon.com/pt/aws-cost-management/aws-cost-and-usage-reporting/

---

## Visão Geral

O **AWS Cost and Usage Report (CUR)** fornece o **nível mais detalhado de informações sobre custos e uso da AWS**, permitindo análises profundas por serviço, conta, recurso, tags e períodos de tempo.

O CUR é a **fonte de dados mais completa** para iniciativas de **FinOps**, auditoria de custos, chargeback/showback e análises financeiras avançadas.

---

## Conceitos

### Relatório de Uso e Custo (CUR)
Arquivo detalhado, normalmente em formato **Parquet ou CSV**, gerado periodicamente e armazenado no Amazon S3.

### Granularidade
Permite análise por:
- Conta
- Serviço
- Região
- Recurso
- Tags
- Tipo de uso
- Savings Plans e Reserved Instances

### Atualização
- Atualizado várias vezes ao dia
- Contém dados históricos e incrementais

### Integração Analítica
O CUR é comumente integrado com:
- AWS Glue
- Amazon Athena
- Amazon Redshift
- Ferramentas de BI externas

---

## Arquitetura – Detailed Cost and Usage Reporting

<img width="753" height="414" alt="image" src="https://github.com/user-attachments/assets/f05fd1d1-0cea-4d00-8e8d-e22b28bd0c08" />


**Fonte oficial:**  
https://docs.aws.amazon.com/pt_br/prescriptive-guidance/latest/patterns/create-detailed-cost-and-usage-reports-for-amazon-rds-and-amazon-aurora.html

---

### Visão Geral da Arquitetura

Esta arquitetura demonstra como **coletar, processar e analisar relatórios de uso e custo da AWS**, transformando dados brutos do CUR em informações consultáveis e acionáveis.

O objetivo é permitir **análise detalhada e automatizada de custos**, utilizando serviços serverless.

---

### Descrição do Fluxo

1. **AWS Cost and Usage Report**
   - Gera relatórios detalhados de custos e uso
   - Publica os arquivos no **Amazon S3**

2. **Amazon S3**
   - Armazena os relatórios brutos
   - Atua como data lake financeiro

3. **AWS Lambda**
   - Processa novos arquivos do CUR
   - Automatiza tarefas de preparação e validação

4. **AWS Glue Crawler**
   - Analisa os dados no S3
   - Cria ou atualiza o catálogo de metadados

5. **Amazon Athena**
   - Executa consultas SQL diretamente nos dados do CUR
   - Permite análises rápidas e sob demanda

6. **Amazon SNS**
   - Envia notificações sobre processamento ou eventos relevantes

7. **AWS CloudFormation**
   - Padroniza e automatiza a criação da arquitetura

---

## Casos de Uso

Os casos de uso abaixo são baseados na documentação e no guia prescritivo oficial da AWS:

### 1. Análise detalhada de custos por recurso
Permite identificar exatamente onde e como os custos estão sendo gerados.

🔗 https://aws.amazon.com/pt/aws-cost-management/aws-cost-and-usage-reporting/

---

### 2. Chargeback e Showback
Atribuição de custos por time, projeto ou centro de custo utilizando tags.

🔗 https://docs.aws.amazon.com/pt_br/awsaccountbilling/latest/aboutv2/cost-alloc-tags.html

---

### 3. Análise avançada de custos de bancos de dados
Análise detalhada de custos de Amazon RDS e Amazon Aurora.

🔗 https://docs.aws.amazon.com/pt_br/prescriptive-guidance/latest/patterns/create-detailed-cost-and-usage-reports-for-amazon-rds-and-amazon-aurora.html

---

### 4. Base de dados para FinOps
Utilização do CUR como fonte primária para dashboards e análises financeiras.

🔗 https://aws.amazon.com/pt/aws-cost-management/

---

## Boas Práticas

### Arquitetura
- Utilize **formato Parquet** para melhor performance
- Separe buckets por ambiente ou organização
- Automatize a infraestrutura com CloudFormation ou Terraform

---

### Performance
- Utilize particionamento por data no Athena
- Evite consultas sem filtros
- Atualize Glue Crawlers de forma controlada

---

### Governança
- Padronize tags obrigatórias
- Restrinja acesso aos dados financeiros
- Centralize relatórios em contas master

---

### Operação
- Monitore falhas na geração de relatórios
- Valide consistência dos dados
- Documente queries e dashboards padrão

---

## Observações Finais

O AWS Cost and Usage Report é a **base de qualquer estratégia madura de gerenciamento de custos na AWS**. Embora seja mais complexo que outras ferramentas visuais, ele oferece **nível máximo de detalhe e flexibilidade**, sendo indispensável para análises profundas e automação financeira.

Ele deve ser utilizado em conjunto com **AWS Cost Explorer, AWS Budgets e Savings Plans** para uma visão completa de custos.
