# Amazon EventBridge –

**Serviço:** Amazon EventBridge  
**Categoria:** Integração de aplicações / Barramento de eventos  
**Documentação oficial:** https://aws.amazon.com/pt/eventbridge/

---

## 🎯 Visão Geral

O **Amazon EventBridge** é um serviço gerenciado de barramento de eventos (event bus) que facilita a construção de arquiteturas orientadas a eventos, permitindo que aplicações e serviços publiquem e consumam eventos de forma desacoplada e escalável.

Ele suporta eventos de diversas fontes:
- AWS services
- Aplicações SaaS
- Aplicações customizadas

O EventBridge substitui o antigo CloudWatch Events, com suporte ampliado e mais integração com eventos SaaS.

---

## 🧠 1. Conceitos

### O que é EventBridge?

O EventBridge é um **sistema de roteamento de eventos** que entrega eventos de produtores para consumidores com base em regras definidas pelo usuário.

---

### Componentes principais

| Componente | Descrição |
|------------|-----------|
| **Event Bus** | Recebe eventos; pode ser padrão (AWS), customizado ou de parceiros SaaS |
| **Event** | Mensagem que representa uma mudança de estado ou ação |
| **Rule (Regra)** | Define como os eventos serão roteados aos destinos |
| **Target (Destino)** | Receptores dos eventos: Lambda, SQS, SNS, Step Functions, etc. |

---

### Tipos de barramento

- **AWS Default Event Bus:** Eventos de serviços AWS
- **Custom Event Bus:** Eventos da sua aplicação
- **Partner Event Bus:** Eventos de aplicações SaaS de parceiros

---

## 🏛️ 2. Arquitetura – Serverless Custom Retry Mechanism

**Fonte Oficial:**  
https://aws.amazon.com/pt/blogs/architecture/create-a-serverless-custom-retry-mechanism-for-stateless-queue-consumers/

---

### 🏗️ Diagrama de Arquitetura

<img width="872" height="518" alt="image" src="https://github.com/user-attachments/assets/07b76371-c293-42ae-841f-155c3c0d19e8" />


---

### 🔄 Descrição do Fluxo de Eventos

Esta arquitetura demonstra um padrão de **retry customizado para consumidores sem estado (stateless)** utilizando EventBridge e outras integrações serverless.

1. **Produtor de Eventos**
   - Publica eventos no **EventBridge Custom Event Bus**
   - Pode ser qualquer aplicação ou serviço

2. **EventBridge Rules**
   - Define regras que capturam determinados tipos de eventos
   - Roteia para destinos como SQS, Lambda ou Step Functions

3. **Lambda Functions / Step Functions**
   - Consumidores dos eventos
   - Executam a lógica de processamento principal

4. **Retry Customizado**
   - Quando ocorre falha ou erro, uma regra do EventBridge pode redirecionar o evento
   - Encaminha para filas SQS ou reprocessadores
   - Gatilhos adicionais para retries sem intervenção manual

5. **Dead Letter Queue (DLQ)**
   - Eventos que ultrapassam o limite de retries vão para uma fila de erro
   - Permite inspeção e auditoria

---

## 🚀 3. Casos de Uso

### 1. Arquiteturas serverless desacopladas  
- Separar produtores e consumidores sem dependências rígidas

---

### 2. Roteamento de eventos de aplicações SaaS  
- Integrar eventos de serviços SaaS diretamente

---

### 3. Orquestração de workflows  
- Combinar com Step Functions para fluxos complexos

---

### 4. Processamento de eventos em tempo real  
- Notificações, logs, métricas e auditoria

---

### 5. Retries e DLQ sem código adicional  
- Permite lógica de retry reutilizável e configurável

---


---

## 📌 4. Boas Práticas

### 🛠️ Modelo de Eventos

- Use **schemas claros e versionados**
- Evite estruturas muito genéricas
- Padronize campos principais (ex.: source, eventType, timestamp)

---

### 🚦 Regras e Filtros

- Aproveite filtros por conteúdo (event pattern)
- Separe regras por domínio lógico
- Evite regras muito amplas que capturam muitos eventos

---

### 📈 Performance e Escalabilidade

- EventBridge é escalável nativamente
- Combine com SQS e Lambda para buffer e controle de taxa
- Planeje limites de throughput conforme necessidade

---

### 🔒 Segurança

- Controle com **IAM roles e policies**
- Restrinja quem pode publicar em cada barramento
- Use tagging para identificação e governança

---

### 📊 Monitoramento

- Ative métricas no CloudWatch
- Monitore invocations, erros e throttles
- Configure alarmes para padrões suspeitos

---

## 📚 Resumo Rápido

| Aspecto | Descrição |
|---------|-----------|
| Tipo | Barramento de eventos |
| Estilo | Event-driven |
| Escalabilidade | Alta, serverless |
| Ideal para | Integração desacoplada e real-time |
| Destinos | Lambda, SQS, SNS, Step Functions |

