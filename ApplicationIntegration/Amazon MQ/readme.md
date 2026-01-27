# Amazon MQ – Documentação de Estudo

**Serviço:** Amazon MQ  
**Categoria:** Integração de aplicações / Mensageria gerenciada  
**Documentação oficial:** https://aws.amazon.com/pt/amazon-mq/

---

## Visão Geral

O **Amazon MQ** é um serviço gerenciado de **mensageria tradicional**, compatível com **Apache ActiveMQ** e **RabbitMQ**, projetado principalmente para **migração de aplicações legadas** ou cenários que exigem **protocolos de mensageria clássicos**.

Diferente de serviços nativos serverless como SQS ou EventBridge, o Amazon MQ mantém o modelo de **broker**, oferecendo compatibilidade com protocolos amplamente utilizados no mercado.

---

## Conceitos

### Broker
Instância gerenciada que atua como intermediária no envio e recebimento de mensagens entre produtores e consumidores.

### Protocolos suportados
- AMQP
- MQTT
- STOMP
- OpenWire
- JMS (via ActiveMQ)
- RabbitMQ protocol

### Filas e Exchanges
- **Filas:** armazenam mensagens até serem consumidas
- **Exchanges (RabbitMQ):** roteiam mensagens para filas com base em regras

### Alta disponibilidade
O Amazon MQ pode ser configurado com **múltiplos brokers em diferentes Availability Zones**, garantindo tolerância a falhas.

### Persistência
Mensagens persistentes são armazenadas em **volumes EBS**, garantindo durabilidade mesmo em falhas de instância.

---

## Arquitetura – RabbitMQ Broker Architecture



**Fonte oficial:**  
https://docs.aws.amazon.com/pt_br/amazon-mq/latest/developer-guide/rabbitmq-broker-architecture.html

---

### Visão Geral da Arquitetura

Esta arquitetura demonstra um **cluster de brokers RabbitMQ no Amazon MQ**, distribuídos em **múltiplas Availability Zones**, com **balanceamento de carga** e **armazenamento persistente**.

O objetivo é garantir:
- Alta disponibilidade
- Persistência de mensagens
- Continuidade do serviço em falhas de zona
  
<img width="755" height="651" alt="image" src="https://github.com/user-attachments/assets/fe7c3869-a887-45bc-97cb-9cfee3bfaf3b" />


---

### Descrição do Fluxo

1. **Client**
   - Aplicações produtoras e consumidoras
   - Conectam-se usando protocolos tradicionais (AMQP, MQTT, etc.)

2. **Network Load Balancer**
   - Distribui conexões entre os brokers disponíveis
   - Mantém alta disponibilidade e failover

3. **Amazon MQ Brokers**
   - Brokers RabbitMQ distribuídos em múltiplas AZs
   - Responsáveis pelo roteamento e entrega das mensagens

4. **EBS Volumes**
   - Armazenam mensagens persistentes
   - Garantem durabilidade em falhas de instância

5. **Replicação entre Brokers**
   - Sincronização de estado entre brokers
   - Garante continuidade do serviço em falhas de AZ

---

## Casos de Uso

Os casos abaixo são baseados na documentação oficial do Amazon MQ:

### 1. Migração de aplicações legadas
Ideal para workloads que utilizam ActiveMQ ou RabbitMQ on-premises.

🔗 https://aws.amazon.com/pt/amazon-mq/

---

### 2. Mensageria com protocolos tradicionais
Quando há dependência de protocolos como AMQP, MQTT ou JMS.

🔗 https://aws.amazon.com/pt/amazon-mq/

---

### 3. Integração híbrida (on-premises + cloud)
Permite comunicação entre aplicações on-premises e AWS sem reescrita de código.

🔗 https://docs.aws.amazon.com/pt_br/amazon-mq/latest/developer-guide/

---

### 4. Workloads que exigem controle fino do broker
Cenários que necessitam de:
- Controle de filas
- Exchanges customizadas
- Políticas específicas de roteamento

🔗 https://docs.aws.amazon.com/pt_br/amazon-mq/latest/developer-guide/rabbitmq-broker-architecture.html

---

## Boas Práticas

### Arquitetura
- Utilize **multi-AZ** sempre que possível
- Separe ambientes (prod, staging, dev) por brokers
- Planeje corretamente throughput e conexões simultâneas

---

### Resiliência
- Configure **Network Load Balancer** para alta disponibilidade
- Use filas duráveis para mensagens críticas
- Monitore replicação entre brokers

---

### Segurança
- Restrinja acesso via **Security Groups**
- Utilize autenticação forte nos brokers
- Evite exposição pública desnecessária

---

### Operação
- Monitore métricas de:
  - Conexões
  - Latência
  - Uso de disco (EBS)
- Planeje crescimento de storage antecipadamente
- Realize backups conforme criticidade do workload

---

## Observações Finais

O Amazon MQ é a escolha certa quando há necessidade de **compatibilidade com mensageria tradicional**, especialmente em processos de **migração para a AWS**.

Para arquiteturas novas e totalmente serverless, serviços como **SQS, SNS ou EventBridge** costumam ser mais indicados. Já para cenários legados ou híbridos, o Amazon MQ oferece estabilidade, compatibilidade e alta disponibilidade com menor esforço operacional.
