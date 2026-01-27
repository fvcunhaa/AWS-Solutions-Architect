# Amazon Elastic Compute Cloud (EC2)

**Serviço:** Amazon EC2  
**Categoria:** Computação / Máquinas virtuais  
**Documentação oficial:** https://aws.amazon.com/pt/ec2/

---

## Visão Geral

O **Amazon EC2 (Elastic Compute Cloud)** é o serviço de computação da AWS que fornece **instâncias de máquinas virtuais sob demanda**, permitindo controle total sobre sistema operacional, capacidade de computação, rede e armazenamento.

O EC2 é a base para grande parte das arquiteturas na AWS, sendo utilizado tanto para workloads tradicionais quanto para aplicações modernas e distribuídas.

---

## Conceitos

### Instância
Servidor virtual que executa aplicações e serviços. Pode variar em:
- CPU
- Memória
- Armazenamento
- GPU
- Capacidade de rede

### Tipos de Instância
Famílias otimizadas para diferentes workloads:
- **General Purpose**
- **Compute Optimized**
- **Memory Optimized**
- **Storage Optimized**
- **Accelerated Computing**

### AMI (Amazon Machine Image)
Template que define o sistema operacional, configurações e softwares da instância.

### Modelos de Compra
- **On-Demand**
- **Reserved Instances**
- **Savings Plans**
- **Spot Instances**

### Monitoramento
Integração nativa com **Amazon CloudWatch** para métricas, logs e alarmes.

---

## Arquitetura – Instance Scheduler para Otimização de Custos


**Fonte oficial:**  
https://aws.amazon.com/pt/blogs/aws-brasil/explorando-o-instance-scheduler-para-otimizar-os-custos-de-amazon-elastic-compute-cloud-amazon-ec2/

---

### Visão Geral da Arquitetura
<img width="1167" height="584" alt="image" src="https://github.com/user-attachments/assets/7a663f17-0994-4322-9b46-bcf0c8f06886" />


Esta arquitetura demonstra o uso do **EC2 Instance Scheduler**, uma solução que permite **iniciar e parar instâncias automaticamente** com base em **agendamentos**, reduzindo custos em ambientes que não precisam ficar ativos 24x7.

Ela é especialmente útil em ambientes:
- Desenvolvimento
- Testes
- Homologação
- Laboratórios

---

### Descrição do Fluxo

1. **Amazon CloudWatch**
   - Dispara eventos em horários programados

2. **AWS Lambda**
   - Executa a lógica de agendamento
   - Avalia regras e janelas de operação

3. **Amazon DynamoDB**
   - Armazena configurações de agendamento
   - Mantém estado e regras

4. **Amazon EC2 / Amazon RDS**
   - Instâncias são iniciadas ou paradas automaticamente
   - Pode operar em múltiplas contas e regiões

5. **Amazon CloudWatch (Logs e Métricas)**
   - Registra execuções
   - Permite auditoria e troubleshooting

---

## Casos de Uso

Os casos de uso abaixo são baseados na documentação e no artigo oficial:

### 1. Otimização de custos em ambientes não produtivos
Redução significativa de custos ao desligar instâncias fora do horário comercial.

🔗 https://aws.amazon.com/pt/blogs/aws-brasil/explorando-o-instance-scheduler-para-otimizar-os-custos-de-amazon-elastic-compute-cloud-amazon-ec2/

---

### 2. Execução de aplicações legadas
Ideal para aplicações que exigem controle total do sistema operacional.

🔗 https://aws.amazon.com/pt/ec2/

---

### 3. Ambientes customizados e altamente configuráveis
Uso de instâncias específicas para workloads especializados.

🔗 https://aws.amazon.com/pt/ec2/

---

### 4. Workloads previsíveis com controle financeiro
Combinação de EC2 com Savings Plans e agendamentos.

🔗 https://aws.amazon.com/pt/ec2/

---

## Boas Práticas

### Arquitetura
- Utilize **Auto Scaling** para alta disponibilidade
- Separe ambientes por conta ou VPC
- Combine EC2 com serviços gerenciados quando possível

---

### Custos
- Utilize **Instance Scheduler** para ambientes não críticos
- Prefira **Savings Plans** para workloads previsíveis
- Use **Spot Instances** para workloads tolerantes a interrupções

---

### Segurança
- Utilize **IAM Roles** em vez de credenciais estáticas
- Restrinja acesso via Security Groups
- Mantenha AMIs atualizadas

---

### Operação
- Monitore métricas de CPU, memória e disco
- Automatize provisionamento com IaC
- Documente padrões de uso e manutenção

---

## Observações Finais

O Amazon EC2 oferece **flexibilidade máxima** para execução de workloads na AWS. Essa flexibilidade exige boas práticas de **governança, segurança e otimização de custos**.

Quando bem combinado com **Auto Scaling, monitoramento e modelos de compra adequados**, o EC2 se torna uma base sólida para arquiteturas escaláveis, resilientes e financeiramente eficientes.
