# Amazon EC2 Auto Scaling

**Serviço:** Amazon EC2 Auto Scaling  
**Categoria:** Computação / Escalabilidade automática  
**Documentação oficial:** https://aws.amazon.com/pt/ec2/autoscaling/

---

## Visão Geral

O **Amazon EC2 Auto Scaling** é um serviço que permite **adicionar ou remover automaticamente instâncias EC2** de acordo com políticas definidas, métricas ou eventos programados.

Ele é um componente essencial para arquiteturas que exigem:
- Alta disponibilidade
- Escalabilidade automática
- Otimização de custos
- Resiliência a falhas

O Auto Scaling garante que a aplicação tenha **capacidade adequada no momento certo**, evitando tanto subdimensionamento quanto desperdício de recursos.

---

## Conceitos

### Auto Scaling Group (ASG)
Grupo lógico de instâncias EC2 que compartilham:
- Tipo de instância
- AMI
- Configurações de rede
- Políticas de escalabilidade

### Launch Template
Template que define como novas instâncias serão criadas, incluindo:
- AMI
- Tipo de instância
- Configurações de rede
- IAM Role
- User Data

### Políticas de Escalabilidade
Regras que determinam quando escalar:
- **Target Tracking:** mantém métricas em um valor alvo
- **Step Scaling:** escala em etapas
- **Scheduled Scaling:** escala por horário

### Integração com CloudWatch
Utiliza métricas e alarmes para tomar decisões automáticas de escala.

---

## Arquitetura – Auto Scaling Orientado a Eventos (SAP)

**Fonte oficial:**  
https://docs.aws.amazon.com/pt_br/prescriptive-guidance/latest/strategy-sap-automation/auto-scaling.html

---

### Visão Geral da Arquitetura
<img width="390" height="461" alt="image" src="https://github.com/user-attachments/assets/167826b0-013a-46b3-bbf2-204f00a4f058" />

Esta arquitetura demonstra um modelo de **Auto Scaling orientado a eventos e tempo**, utilizado em workloads **SAP**, onde a capacidade do ambiente é ajustada automaticamente com base em **eventos programados**.

O objetivo é garantir **disponibilidade e performance**, especialmente em janelas críticas de processamento, como fechamentos financeiros.

---

### Descrição do Fluxo

1. **Amazon EventBridge**
   - Dispara eventos baseados em tempo (time-based events)
   - Define janelas específicas de escalabilidade

2. **AWS Lambda**
   - Recebe o evento do EventBridge
   - Executa lógica de decisão e orquestração

3. **Amazon DynamoDB**
   - Armazena configurações, estados e regras de escalabilidade

4. **AWS Systems Manager**
   - Executa comandos e automações
   - Gerencia operações nas instâncias

5. **Auto Scaling Group**
   - Ajusta a quantidade de instâncias EC2
   - Inclui instâncias existentes e novas instâncias adicionais
   - Garante capacidade adequada durante o evento

---

## Casos de Uso

Os casos de uso abaixo são baseados na documentação oficial e no guia prescritivo da AWS:

### 1. Escalabilidade automática para workloads SAP
Ajuste dinâmico de capacidade em períodos de alta demanda.

🔗 https://docs.aws.amazon.com/pt_br/prescriptive-guidance/latest/strategy-sap-automation/auto-scaling.html

---

### 2. Alta disponibilidade de aplicações
Substituição automática de instâncias com falha.

🔗 https://aws.amazon.com/pt/ec2/autoscaling/

---

### 3. Otimização de custos
Redução de recursos em períodos de baixa utilização.

🔗 https://aws.amazon.com/pt/ec2/autoscaling/

---

### 4. Escalabilidade baseada em eventos
Escala ambientes com base em janelas de tempo ou eventos de negócio.

🔗 https://aws.amazon.com/pt/ec2/autoscaling/

---

## Boas Práticas

### Arquitetura
- Utilize múltiplas Availability Zones
- Combine Auto Scaling com Load Balancers
- Use Launch Templates versionados

---

### Escalabilidade
- Prefira Target Tracking para a maioria dos casos
- Teste políticas de escala regularmente
- Evite limites de escala muito restritivos

---

### Custos
- Combine Auto Scaling com Savings Plans
- Utilize Spot Instances quando possível
- Ajuste capacidade mínima com cuidado

---

### Operação
- Monitore métricas de escalabilidade
- Use logs e alarmes para troubleshooting
- Documente regras e janelas de escala

---

## Observações Finais

O Amazon EC2 Auto Scaling é um pilar fundamental para arquiteturas **resilientes, escaláveis e eficientes** na AWS. Ele automatiza decisões críticas de capacidade, reduz esforço operacional e contribui diretamente para otimização de custos.

Quando integrado com **EventBridge, Lambda e Systems Manager**, o Auto Scaling permite criar soluções avançadas e orientadas a eventos, atendendo até mesmo workloads corporativos complexos, como ambientes SAP.
