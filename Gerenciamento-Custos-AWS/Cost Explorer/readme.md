# AWS Cost Explorer – Documentação de Estudo

**Serviço:** AWS Cost Explorer  
**Categoria:** Gerenciamento de custos / Análise financeira  
**Documentação oficial:** https://aws.amazon.com/pt/aws-cost-management/aws-cost-explorer/

---

## Visão Geral

O **AWS Cost Explorer** é a ferramenta da AWS para **visualização, análise e previsão de custos e uso**, permitindo entender rapidamente **onde, como e por que** os gastos estão ocorrendo.

Ele oferece uma interface gráfica interativa para:
- Análise histórica de custos
- Comparação entre períodos
- Agrupamento por serviço, conta, região e tags
- Previsão de gastos futuros

É uma ferramenta essencial para **monitoramento contínuo** e tomada de decisão rápida em iniciativas de **FinOps**.

---

## Conceitos

### Visualização de Custos
Permite analisar custos por diferentes dimensões:
- Serviço
- Conta
- Região
- Tipo de uso
- Tags de alocação de custos

### Filtros e Agrupamentos
Facilitam a identificação de:
- Serviços mais caros
- Tendências de crescimento
- Desvios de custo

### Previsões
O Cost Explorer utiliza dados históricos para estimar custos futuros, auxiliando no planejamento financeiro.

### Integração com Tags
O uso de **tags de alocação de custos** permite atribuir gastos a:
- Times
- Projetos
- Centros de custo

---

## Arquitetura – Cost Analysis for EMR Using Cost Explorer
<img width="605" height="395" alt="image" src="https://github.com/user-attachments/assets/b75f2259-a81e-46ab-b150-ffbc5ca15ef1" />



**Fonte oficial:**  
https://docs.aws.amazon.com/pt_br/prescriptive-guidance/latest/patterns/create-detailed-cost-and-usage-reports-for-amazon-emr-clusters-by-using-aws-cost-explorer.html

---

### Visão Geral da Arquitetura

Esta arquitetura demonstra como utilizar **tags de alocação de custos** em clusters **Amazon EMR** para analisar gastos de forma segmentada no **AWS Cost Explorer**.

O objetivo é permitir **visibilidade financeira por time, projeto ou centro de custo**, sem necessidade de processamento complexo de dados.

---

### Descrição do Fluxo

1. **Clusters Amazon EMR**
   - Cada cluster é criado com **tags padronizadas**
   - Exemplo de tags:
     - `Team`
     - `Cost Center`
     - `Project`

2. **AWS Account**
   - Centraliza o consumo de recursos
   - Consolida custos de todos os clusters

3. **Cloud Financial Management**
   - Coleta dados de uso e custo
   - Processa informações com base nas tags

4. **AWS Cost Explorer**
   - Apresenta visualizações de custo
   - Permite filtrar e agrupar gastos por tag
   - Facilita análise comparativa entre projetos e times

---

## Casos de Uso

Os casos de uso abaixo são baseados na documentação e no guia prescritivo oficial:

### 1. Análise de custos por projeto
Permite identificar quanto cada projeto está consumindo em recursos.

🔗 https://aws.amazon.com/pt/aws-cost-management/aws-cost-explorer/

---

### 2. Controle financeiro por time ou centro de custo
Uso de tags para separar custos entre áreas da organização.

🔗 https://docs.aws.amazon.com/pt_br/prescriptive-guidance/latest/patterns/create-detailed-cost-and-usage-reports-for-amazon-emr-clusters-by-using-aws-cost-explorer.html

---

### 3. Identificação de tendências de gasto
Análise histórica para detectar crescimento anormal de custos.

🔗 https://aws.amazon.com/pt/aws-cost-management/aws-cost-explorer/

---

### 4. Planejamento financeiro e previsões
Uso das previsões do Cost Explorer para estimar gastos futuros.

🔗 https://aws.amazon.com/pt/aws-cost-management/aws-cost-explorer/

---

## Boas Práticas

### Governança
- Padronize **tags obrigatórias** desde o provisionamento
- Ative tags de alocação de custos na conta
- Garanta consistência entre times

---

### Análise
- Revise custos semanalmente
- Compare períodos equivalentes
- Utilize filtros para isolar variações relevantes

---

### Operação
- Combine Cost Explorer com AWS Budgets para controle proativo
- Utilize o CUR para análises mais profundas quando necessário
- Documente dashboards e visões padrão

---

### Segurança
- Restrinja acesso ao Cost Explorer a perfis autorizados
- Centralize análises financeiras em contas de gestão
- Audite alterações em tags e permissões

---

## Observações Finais

O AWS Cost Explorer é a principal ferramenta para **análise visual e rápida de custos na AWS**. Embora não ofereça o nível de detalhe do Cost and Usage Report, ele é ideal para **monitoramento contínuo, identificação de tendências e suporte à tomada de decisão**.

Para uma estratégia completa de gerenciamento de custos, o Cost Explorer deve ser utilizado em conjunto com **AWS Budgets, Cost and Usage Report e Savings Plans**.
