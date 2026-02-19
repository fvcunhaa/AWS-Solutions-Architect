# Auto Scaling na AWS

## 1. Visão Geral

O **Amazon EC2 Auto Scaling** é um serviço da Amazon Web Services (AWS) que permite ajustar automaticamente a quantidade de instâncias EC2 em execução com base na demanda da aplicação.

Seu objetivo principal é garantir:

- Alta disponibilidade  
- Elasticidade automática  
- Otimização de custos  
- Resiliência a falhas  

O Auto Scaling permite que aplicações mantenham desempenho estável durante picos de carga e reduzam recursos quando a demanda diminui.



## 2. Principais Funcionalidades

### 2.1 Escalabilidade Automática

O serviço ajusta automaticamente a quantidade de instâncias EC2 com base em:

- Uso de CPU
- Métricas customizadas do CloudWatch
- Número de requisições
- Latência
- Fila de processamento

### 2.2 Alta Disponibilidade

- Distribuição de instâncias entre múltiplas Availability Zones
- Substituição automática de instâncias não saudáveis
- Integração nativa com Elastic Load Balancing (ELB)

### 2.3 Políticas de Escala

- **Target Tracking Scaling** (manter métrica alvo, ex: CPU em 60%)
- **Step Scaling** (escala progressiva baseada em thresholds)
- **Simple Scaling** (baseado em alarme)
- **Scheduled Scaling** (escala programada por horário)

### 2.4 Health Check e Self-Healing

O Auto Scaling verifica continuamente a saúde das instâncias:

- Health check do EC2
- Health check do Load Balancer

Instâncias não saudáveis são automaticamente substituídas.



## 3. Arquitetura

A arquitetura típica com Auto Scaling é composta por:

<img width="859" height="563" alt="image" src="https://github.com/user-attachments/assets/e04107ba-78ed-4dfe-bbeb-0c62a0b884e5" />



### 3.1 Componentes Principais

1. **Launch Template / Launch Configuration**  
   Define o padrão das instâncias (AMI, tipo, segurança, armazenamento, user data).

2. **Auto Scaling Group (ASG)**  
   Controla:
   - Número mínimo de instâncias
   - Número máximo de instâncias
   - Capacidade desejada

3. **Elastic Load Balancer (ELB)**  
   Distribui o tráfego entre as instâncias ativas.

4. **Amazon CloudWatch**  
   Monitora métricas e dispara políticas de escala.



### 3.2 Explicação da Arquitetura

Considerando uma arquitetura multi-tier:

- A aplicação está distribuída em múltiplas Availability Zones dentro de uma VPC.
- Existem dois níveis principais:
  - **Web Tier**
  - **App Tier**
- Cada tier possui:
  - Um Elastic Load Balancer
  - Um Auto Scaling Group
  - Múltiplas instâncias EC2

Fluxo operacional:

1. O tráfego entra pelo Load Balancer do Web Tier.
2. O ASG garante que haja instâncias suficientes para suportar a carga.
3. O tráfego é encaminhado ao App Tier, também protegido por Load Balancer e ASG.
4. A camada de banco (por exemplo, Amazon Aurora) opera com instância primária e standby.

Esse modelo permite:

- Escala independente por camada
- Alta disponibilidade multi-AZ
- Resiliência automática



## 4. Casos de Uso

### 4.1 Aplicações Web com Tráfego Variável
E-commerces, portais, SaaS e APIs públicas.

### 4.2 Processamento Sob Demanda
Jobs batch ou workers que precisam escalar conforme fila.

### 4.3 Arquiteturas Multi-Tier
Separação entre Web, Application e Database com escala independente.

### 4.4 Redução de Custos
Ambientes que precisam reduzir infraestrutura fora do horário comercial.



## 5. Integração com Outros Serviços

O Auto Scaling integra-se de forma nativa com:

- Amazon EC2
- Elastic Load Balancing (ALB/NLB)
- Amazon CloudWatch
- AWS IAM
- Amazon VPC
- Amazon Aurora
- AWS Systems Manager
- Amazon ECS
- DynamoDB

Também pode escalar recursos adicionais por meio do **Application Auto Scaling**.



## 6. Boas Práticas

### 6.1 Definir Limites Adequados

- **Min**: evitar indisponibilidade
- **Max**: evitar consumo descontrolado
- **Desired**: base operacional estável

### 6.2 Utilizar Target Tracking

Preferir políticas baseadas em meta (ex: CPU 60%) para maior previsibilidade.

### 6.3 Escalar Baseado em Métrica de Negócio

CPU nem sempre é a melhor métrica. Avaliar:

- Requests por segundo
- Tamanho de fila
- Latência
- Métricas customizadas

### 6.4 Multi-AZ Obrigatório

Sempre distribuir instâncias entre múltiplas zonas.

### 6.5 Warm-up Time Configurado

Evitar escalas excessivas configurando tempo adequado de inicialização das instâncias.

### 6.6 Utilizar Launch Template

Preferir Launch Template em vez de Launch Configuration (modelo mais moderno e flexível).



## 7. Limitações

- Não substitui planejamento de capacidade
- Pode haver atraso na escala (instâncias levam tempo para iniciar)
- Escala baseada apenas nas métricas configuradas
- Pode gerar custo elevado se mal configurado
- Não atua diretamente sobre banco de dados (exceto via Application Auto Scaling)



## 8. Conclusão

O Amazon EC2 Auto Scaling é um componente essencial em arquiteturas modernas na AWS, permitindo elasticidade automática, alta disponibilidade e otimização de custos.

Quando combinado com Load Balancer, CloudWatch e arquitetura multi-tier, torna-se um mecanismo robusto de resiliência e escalabilidade para aplicações críticas.

Sua correta configuração é fundamental para evitar desperdício de recursos e garantir desempenho consistente.
