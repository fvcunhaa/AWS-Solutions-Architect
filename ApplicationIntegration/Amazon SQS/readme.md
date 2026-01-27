# Amazon Simple Queue Service (SQS) 
**Serviço:** Amazon Simple Queue Service (SQS)  
**Categoria:** Integração de aplicações / Mensageria assíncrona  
**Documentação oficial:** https://aws.amazon.com/pt/sqs/

---

## Visão Geral

O **Amazon SQS** é um serviço totalmente gerenciado de **filas de mensagens** que permite desacoplar componentes de sistemas distribuídos, garantindo **processamento assíncrono, escalável e resiliente**.

Ele é amplamente utilizado para:
- Processamento em background
- Controle de carga (buffer)
- Comunicação assíncrona entre microsserviços
- Workloads distribuídos e concorrentes

O SQS elimina a necessidade de gerenciar infraestrutura de mensageria, oferecendo alta disponibilidade e durabilidade nativas.

---

## Conceitos

### Fila (Queue)
Estrutura que armazena mensagens até que sejam consumidas por um ou mais consumidores.

### Produtor
Aplicação que envia mensagens para a fila.

### Consumidor
Aplicação que lê e processa mensagens da fila.

### Tipos de fila

| Tipo | Características |
|----|----------------|
| **Standard** | Alta taxa de throughput, entrega pelo menos uma vez, ordem não garantida |
| **FIFO** | Ordem garantida, exatamente uma vez, throughput controlado |

### Visibility Timeout
Período em que a mensagem fica invisível após ser consumida, evitando processamento duplicado.

### Dead Letter Queue (DLQ)
Fila usada para armazenar mensagens que falharam após múltiplas tentativas de processamento.

---

## Arquitetura – Processamento Assíncrono com SQS Standard e FIFO



**Fonte oficial:**  
https://aws.amazon.com/pt/blogs/aws-brasil/8541-2/

---

### Visão Geral da Arquitetura
<img width="1097" height="718" alt="image" src="https://github.com/user-attachments/assets/f237ddda-2508-427f-986f-cab77d23ad0b" />

Esta arquitetura demonstra um **fluxo de importação assíncrona**, combinando **SQS Standard e SQS FIFO** para atender diferentes necessidades de processamento:

- **Alta concorrência**
- **Processamento paralelo**
- **Atualização ordenada de status**
- **Notificação em tempo real ao cliente**

---

### Descrição do Fluxo

1. **Cliente (Web ou Mobile)**
   - Inicia o processo de importação
   - Realiza upload de arquivos via URL pré-assinada no S3

2. **API Gateway**
   - Recebe a requisição inicial
   - Aciona uma função Lambda

3. **Lambda (Início do Processo)**
   - Valida a requisição
   - Enfileira mensagens no **SQS Standard** para processamento concorrente

4. **SQS Standard**
   - Distribui mensagens para múltiplos workers
   - Permite alto throughput e paralelismo

5. **Lambdas Workers**
   - Processam mensagens em paralelo
   - Persistem dados intermediários no DynamoDB
   - Enviam atualizações de status para o SQS FIFO

6. **SQS FIFO (Update Status)**
   - Garante **ordem e consistência** das atualizações de status

7. **Lambda (Update Status)**
   - Atualiza o estado do processamento no Aurora PostgreSQL
   - Publica eventos de progresso

8. **API Gateway (WebSocket)**
   - Notifica o cliente em tempo real sobre o progresso da importação

---

## Casos de Uso

Os casos de uso abaixo são baseados na documentação e no artigo oficial:

### 1. Processamento assíncrono de arquivos
Ideal para uploads grandes e tarefas demoradas.

🔗 https://aws.amazon.com/pt/blogs/aws-brasil/8541-2/

---

### 2. Workloads concorrentes e escaláveis
Permite processamento paralelo sem sobrecarregar sistemas downstream.

🔗 https://aws.amazon.com/pt/sqs/

---

### 3. Controle de ordem em processos críticos
Uso de filas FIFO para garantir consistência em atualizações de estado.

🔗 https://aws.amazon.com/pt/sqs/

---

### 4. Integração entre microsserviços
Comunicação desacoplada e tolerante a falhas.

🔗 https://docs.aws.amazon.com/pt_br/AWSSimpleQueueService/latest/SQSDeveloperGuide/welcome.html

---

## Boas Práticas

### Arquitetura
- Use **SQS Standard** para alto volume e paralelismo
- Use **SQS FIFO** quando ordem e deduplicação forem críticas
- Combine SQS com Lambda para arquiteturas serverless

---

### Resiliência
- Configure **Dead Letter Queues (DLQ)**
- Ajuste corretamente o **visibility timeout**
- Trate idempotência no consumidor

---

### Performance
- Ajuste batch size de consumo
- Evite processamento muito longo por mensagem
- Escale consumidores conforme throughput

---

### Segurança
- Restrinja acesso via **IAM policies**
- Use criptografia em repouso (SSE)
- Evite exposição pública de filas

---

## Observações Finais

O Amazon SQS é um dos pilares de arquiteturas distribuídas na AWS. Ele oferece uma forma simples e robusta de **desacoplar sistemas**, lidar com picos de carga e garantir processamento confiável.

Em arquiteturas modernas, o SQS é frequentemente combinado com **SNS, EventBridge e Step Functions**, formando pipelines resilientes e altamente escaláveis.
