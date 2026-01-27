# Gerenciamento de Custos da AWS

Este diretório reúne a documentação, conceitos e boas práticas relacionadas aos **serviços de gerenciamento, visibilidade e otimização de custos da AWS**.

O objetivo é fornecer uma base sólida para **controle financeiro (FinOps)**, tomada de decisão, previsibilidade de gastos e otimização contínua do uso da nuvem.

---

## 🎯 Visão Geral

O gerenciamento de custos na AWS é baseado em **visibilidade, controle e otimização contínua**.  
Os serviços abordados neste diretório permitem:

- Monitorar gastos em tempo real
- Analisar histórico de consumo
- Criar alertas e limites de orçamento
- Planejar economia com compromissos de uso

Essas ferramentas são essenciais para ambientes:
- Corporativos
- Multicontas
- Escaláveis
- Orientados a FinOps

---

## 🧠 Serviços Abordados

### 💰 AWS Budgets
Permite criar **orçamentos personalizados** e configurar **alertas automáticos** quando os custos ou o uso ultrapassam limites definidos.

**Principais objetivos:**
- Controle proativo de gastos
- Alertas financeiros
- Governança de custos

📂 Pasta: `aws-budgets/`

---

### 📊 AWS Relatório de Uso e Custo (Cost and Usage Report – CUR)
Serviço que gera o **relatório mais detalhado de custos e uso da AWS**, exportado normalmente para o Amazon S3.

**Principais objetivos:**
- Análise detalhada por serviço, conta, tag e recurso
- Integração com ferramentas de BI
- Base para análises FinOps avançadas

📂 Pasta: `cost-and-usage-report/`

---

### 📈 AWS Cost Explorer
Ferramenta visual para **análise interativa de custos e uso**, com gráficos, filtros e previsões.

**Principais objetivos:**
- Visualização rápida de gastos
- Identificação de tendências
- Análise histórica e previsão de custos

📂 Pasta: `cost-explorer/`

---

### 💸 Savings Plans
Modelo de **desconto baseado em compromisso de uso**, oferecendo economia significativa em troca de previsibilidade.

**Principais objetivos:**
- Redução de custos com workloads previsíveis
- Substituição moderna do Reserved Instances
- Otimização financeira de longo prazo

📂 Pasta: `savings-plans/`

---

## 🏗️ Organização do Diretório

Estrutura sugerida:
├── aws-budgets/

├── cost-and-usage-report/

├── cost-explorer/

├── savings-plans/

└── README.md


Cada pasta conterá:
- Visão geral do serviço
- Conceitos principais
- Arquitetura (quando aplicável)
- Casos de uso
- Boas práticas
- Observações finais

---

## 📌 Boas Práticas Gerais

- Utilize **tags obrigatórias** para melhor visibilidade de custos
- Separe ambientes (prod, dev, stage) por conta ou tag
- Configure **AWS Budgets desde o primeiro dia**
- Analise custos de forma contínua, não pontual
- Combine dados do CUR com ferramentas analíticas

---

## 📚 Público-Alvo

Este material é indicado para:
- Arquitetos Cloud
- Engenheiros DevOps / SRE
- Times FinOps
- Gestores de TI
- Profissionais responsáveis por governança de custos

---

## ✍️ Observações Finais

Gerenciar custos na AWS não é uma atividade pontual, mas um **processo contínuo**.  
Os serviços abordados neste diretório formam a base para **decisões financeiras inteligentes**, garantindo equilíbrio entre performance, escalabilidade e custo.

Este repositório será evoluído continuamente com exemplos práticos, arquiteturas e recomendações baseadas em cenários reais.
