# AWS Savings Plans – Documentação de Estudo

**Serviço:** AWS Savings Plans  
**Categoria:** Gerenciamento de custos / Otimização financeira  
**Documentação oficial:** https://aws.amazon.com/pt/savingsplans/

---

## Visão Geral

O **AWS Savings Plans** é um modelo de **desconto baseado em compromisso de uso**, que permite reduzir significativamente os custos da AWS em troca de um compromisso de gasto consistente ao longo do tempo (1 ou 3 anos).

Ele substitui e complementa o modelo tradicional de **Reserved Instances**, oferecendo mais flexibilidade e simplicidade para otimização financeira.

Savings Plans são um dos pilares de uma estratégia madura de **FinOps** na AWS.

---

## Conceitos

### Compromisso de Uso
Valor em dólares por hora que o cliente se compromete a gastar em serviços elegíveis da AWS.

Exemplo:
- Compromisso: USD 10/h
- Duração: 1 ou 3 anos

### Tipos de Savings Plans

| Tipo | Descrição |
|----|---------|
| **Compute Savings Plans** | Maior flexibilidade, aplica-se a EC2, Lambda e Fargate, independentemente de região, instância ou família |
| **EC2 Instance Savings Plans** | Menor flexibilidade, maior desconto, específico para uma família de instâncias em uma região |

---

### Aplicação Automática
- O desconto é aplicado **automaticamente**
- Não requer alterações em workloads
- Não depende de ação manual após a compra

---

### Escopo
- Savings Plans podem ser aplicados em:
  - Conta individual
  - AWS Organizations (escopo compartilhado)

---

## Arquitetura

O **AWS Savings Plans não possui uma arquitetura de referência oficial**, pois não é um serviço de execução ou processamento, mas sim um **modelo financeiro de cobrança e desconto**.

Seu funcionamento ocorre **no plano de billing da AWS**, sendo aplicado automaticamente sobre workloads elegíveis, como:
- Amazon EC2
- AWS Lambda
- AWS Fargate

Apesar de não ter uma arquitetura técnica, o Savings Plans **impacta diretamente arquiteturas existentes**, reduzindo custos sem alterações estruturais.

---

## Casos de Uso

Os casos de uso abaixo são baseados na documentação oficial do serviço:

### 1. Redução de custos em workloads previsíveis
Ideal para aplicações com consumo estável ao longo do tempo.

🔗 https://aws.amazon.com/pt/savingsplans/

---

### 2. Otimização financeira sem refatoração
Permite economizar sem necessidade de alterar código ou arquitetura.

🔗 https://aws.amazon.com/pt/savingsplans/

---

### 3. Padronização de compromissos em ambientes corporativos
Uso de Savings Plans compartilhados via AWS Organizations.

🔗 https://docs.aws.amazon.com/pt_br/savingsplans/latest/userguide/what-is-savings-plans.html

---

### 4. Estratégias FinOps de médio e longo prazo
Planejamento financeiro com previsibilidade e controle de gastos.

🔗 https://aws.amazon.com/pt/aws-cost-management/

---

## Boas Práticas

### Planejamento
- Analise histórico de uso antes de contratar
- Utilize AWS Cost Explorer e recomendações da AWS
- Evite compromissos acima do uso mínimo garantido

---

### Governança
- Centralize a compra de Savings Plans
- Use contas de gestão (management account)
- Documente compromissos assumidos

---

### Operação
- Monitore a taxa de utilização dos Savings Plans
- Combine com AWS Budgets para alertas
- Revise compromissos periodicamente

---

### Estratégia
- Prefira **Compute Savings Plans** para maior flexibilidade
- Use **EC2 Instance Savings Plans** apenas para workloads muito estáveis
- Combine Savings Plans com rightsizing contínuo

---

## Observações Finais

O AWS Savings Plans é uma ferramenta poderosa para **redução de custos recorrentes**, oferecendo economia significativa com baixo esforço operacional.

Por não exigir mudanças técnicas, ele deve ser considerado **obrigatório** em ambientes produtivos e previsíveis. Quando combinado com **AWS Budgets, Cost Explorer e Cost and Usage Report**, forma a base de uma estratégia sólida de **gerenciamento financeiro na AWS**.
