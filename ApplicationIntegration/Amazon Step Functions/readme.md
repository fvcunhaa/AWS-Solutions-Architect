# AWS Step Functions – Documentação de Estudo

**Serviço:** AWS Step Functions  
**Categoria:** Orquestração de workflows / Serverless  
**Documentação oficial:** https://aws.amazon.com/pt/step-functions/

---

## Visão Geral

O **AWS Step Functions** é um serviço totalmente gerenciado para **orquestração de workflows**, permitindo coordenar múltiplos serviços AWS em fluxos visuais, confiáveis e escaláveis.

Ele é amplamente utilizado para:
- Orquestrar funções Lambda
- Controlar fluxos de negócio complexos
- Implementar retries, paralelismo e tratamento de erros
- Automatizar pipelines serverless e batch

O Step Functions permite modelar workflows usando **Amazon States Language (ASL)**, com controle explícito de estados, transições e falhas.

---

## Conceitos

### State Machine
Definição do workflow. Contém todos os estados e regras de transição.

### Estados (States)
Representam etapas do fluxo. Principais tipos:
- **Task:** executa um serviço (Lambda, Batch, etc.)
- **Choice:** decisões condicionais
- **Parallel:** execução paralela
- **Wait:** espera por tempo ou evento
- **Fail / Succeed:** finalização do fluxo

### Execution
Instância em execução de uma state machine.

### Integrações nativas
O Step Functions integra diretamente com:
- AWS Lambda
- Amazon EventBridge
- AWS Batch
- DynamoDB
- SQS, SNS
- Serviços de analytics e ML

### Tratamento de erros
Permite configurar:
- Retries automáticos
- Backoff exponencial
- Captura e roteamento de falhas

---

## Arquitetura – Automated Benchmarking with Step Functions

<img width="796" height="418" alt="image" src="https://github.com/user-attachments/assets/cfb34327-2f1d-43cb-87e1-380837d71cad" />


**Fonte oficial:**  
https://aws.amazon.com/pt/blogs/architecture/genomics-workflows-part-5-automated-benchmarking/

---

### Visão Geral da Arquitetura

Esta arquitetura demonstra um **workflow automatizado de benchmarking**, onde o **AWS Step Functions** coordena múltiplos serviços para executar tarefas computacionalmente intensivas de forma controlada e escalável.

O fluxo é **event-driven**, iniciado a partir de mudanças em dados e executado de forma totalmente serverless.

---

### Descrição do Fluxo

1. **Amazon DynamoDB Stream**
   - Detecta alterações nos dados
   - Emite eventos automaticamente

2. **Amazon EventBridge**
   - Captura eventos do DynamoDB Stream
   - Dispara a execução do workflow

3. **AWS Step Functions**
   - Orquestra todo o processo
   - Controla a ordem, paralelismo e falhas

4. **AWS Lambda (Task States)**
   - Executa lógica de negócio
   - Prepara dados e valida condições

5. **AWS Batch**
   - Executa workloads computacionalmente intensivos
   - Ideal para tarefas de longa duração

6. **AWS Cloud Financial Management**
   - Coleta dados de custo e uso
   - Permite análise financeira do processamento

7. **Amazon DynamoDB**
   - Armazena resultados finais
   - Persiste estado e métricas do workflow

---

## Casos de Uso

Os casos abaixo são derivados diretamente do artigo de arquitetura oficial:

### 1. Orquestração de workflows científicos e de dados
Coordenação de pipelines complexos com múltiplas etapas dependentes.

🔗 https://aws.amazon.com/pt/blogs/architecture/genomics-workflows-part-5-automated-benchmarking/

---

### 2. Automação de pipelines serverless
Controle de execução, retries e paralelismo sem código adicional.

🔗 https://aws.amazon.com/pt/step-functions/

---

### 3. Integração entre eventos e processamento batch
Inicia workflows batch a partir de eventos em tempo real.

🔗 https://aws.amazon.com/pt/blogs/architecture/genomics-workflows-part-5-automated-benchmarking/

---

### 4. Governança e rastreabilidade de processos
Cada execução é auditável, com histórico completo e visualização gráfica.

🔗 https://aws.amazon.com/pt/step-functions/

---

## Boas Práticas

### Arquitetura
- Divida workflows grandes em **state machines menores**
- Use **Parallel states** quando possível
- Prefira integrações nativas a Lambdas intermediárias

---

### Resiliência
- Configure retries com backoff exponencial
- Trate falhas explicitamente com estados Fail
- Use DLQs nos serviços integrados quando aplicável

---

### Performance e Custo
- Evite estados desnecessários
- Use Standard ou Express conforme o caso:
  - **Standard:** workflows longos e críticos
  - **Express:** alto volume e baixa latência

---

### Observabilidade
- Utilize logs e métricas no CloudWatch
- Monitore tempo de execução e falhas
- Use histórico de execuções para troubleshooting

---

## Observações Finais

O AWS Step Functions é a peça central para **orquestração de workflows serverless** na AWS. Ele reduz drasticamente a complexidade de código, aumenta a confiabilidade dos processos e fornece visibilidade completa sobre fluxos complexos.

É especialmente indicado quando há necessidade de **coordenação entre múltiplos serviços**, controle de estado, retries e paralelismo — algo difícil de manter apenas com código imperativo.
