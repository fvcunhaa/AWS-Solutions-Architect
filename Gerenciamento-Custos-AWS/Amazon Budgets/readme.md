# AWS Budgets – Documentação de Estudo

**Serviço:** AWS Budgets  
**Categoria:** Gerenciamento de custos / Governança financeira  
**Documentação oficial:** https://aws.amazon.com/pt/aws-cost-management/aws-budgets/

---

## Visão Geral

O **AWS Budgets** é um serviço de gerenciamento financeiro que permite **definir orçamentos personalizados** e **monitorar custos, uso e compromissos**, acionando alertas e automações quando limites são atingidos.

Ele é amplamente utilizado para:
- Controle proativo de gastos
- Governança financeira em ambientes multi-conta
- Apoio a práticas **FinOps**
- Prevenção de custos inesperados

---

## Conceitos

### Orçamento (Budget)
Definição de um limite financeiro ou de uso, baseado em:
- Custo
- Uso
- Utilização de Savings Plans ou Reserved Instances

### Alertas
Notificações disparadas quando o orçamento atinge um percentual ou valor definido.

### Ações de Orçamento
Permitem executar **ações automáticas** quando um limite é ultrapassado, como:
- Envio de notificações
- Bloqueio ou restrição de recursos
- Execução de funções Lambda

### Integração com outros serviços
O AWS Budgets integra-se nativamente com:
- Amazon SNS
- AWS Lambda
- AWS Service Catalog
- AWS Organizations

---

## Arquitetura – Smart Budgeting with Lambda and Service Catalog
<img width="809" height="399" alt="image" src="https://github.com/user-attachments/assets/0a83a0d8-e2c9-4d2e-a0c7-8468e3a46d14" />



**Fonte oficial:**  
https://aws.amazon.com/pt/blogs/mt/smart-budgeting-using-lambda-and-service-catalog/

---

### Visão Geral da Arquitetura

Esta arquitetura demonstra um modelo de **orçamento inteligente**, onde o **AWS Budgets** não apenas alerta sobre custos, mas também **executa ações automatizadas** para reforçar a governança financeira.

O objetivo é **prevenir gastos excessivos**, aplicando controles técnicos de forma automática.

---

### Descrição do Fluxo

1. **AWS Budgets**
   - Monitora continuamente os custos da conta ou projeto
   - Dispara um **Budget Alarm** ao atingir um limite configurado

2. **Amazon SNS**
   - Recebe o alerta do orçamento
   - Envia notificações (ex.: e-mail) para administradores

3. **AWS Lambda**
   - Executa ações automáticas ao receber o evento do SNS
   - Pode aplicar regras de controle ou mitigação

4. **AWS Service Catalog**
   - Controla quais produtos e recursos podem ser provisionados
   - Aplica **constraints** em templates CloudFormation

5. **Administrador / Usuários**
   - Administradores recebem alertas
   - Usuários finais são impactados por restrições de provisionamento

---

## Casos de Uso

Os casos de uso abaixo são baseados na documentação e no artigo oficial:

### 1. Alertas automáticos de custo
Notificação imediata quando gastos se aproximam ou excedem o orçamento.

🔗 https://aws.amazon.com/pt/aws-cost-management/aws-budgets/

---

### 2. Governança financeira automatizada
Execução de ações automáticas para impedir novos provisionamentos ao exceder o orçamento.

🔗 https://aws.amazon.com/pt/blogs/mt/smart-budgeting-using-lambda-and-service-catalog/

---

### 3. Controle de custos por projeto ou ambiente
Criação de orçamentos específicos para times, aplicações ou ambientes.

🔗 https://aws.amazon.com/pt/aws-cost-management/aws-budgets/

---

### 4. Apoio a práticas FinOps
Uso de budgets como mecanismo de feedback contínuo para times técnicos e financeiros.

🔗 https://aws.amazon.com/pt/aws-cost-management/

---

## Boas Práticas

### Governança
- Defina budgets desde o início do projeto
- Crie orçamentos separados por ambiente (prod, dev, stage)
- Utilize tags para granularidade de controle

---

### Automação
- Combine AWS Budgets com Lambda para ações corretivas
- Utilize SNS para múltiplos canais de notificação
- Integre com Service Catalog para controle de provisionamento

---

### Operação
- Revise budgets periodicamente
- Ajuste limites conforme crescimento do negócio
- Monitore alarmes recorrentes para identificar desvios estruturais

---

### Segurança
- Restrinja quem pode criar ou alterar budgets
- Use AWS Organizations para padronizar regras
- Centralize a gestão de custos em contas master

---

## Observações Finais

O AWS Budgets é uma ferramenta fundamental para **controle proativo de custos** na AWS. Quando combinado com automação e governança, ele deixa de ser apenas um sistema de alerta e passa a ser um **mecanismo ativo de controle financeiro**.

Essa abordagem é essencial para ambientes escaláveis e organizações que adotam práticas maduras de **FinOps**.
