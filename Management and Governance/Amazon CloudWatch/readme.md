# Monitoramento com Amazon CloudWatch

## 1. Visão Geral

O **Amazon CloudWatch** é o serviço de monitoramento e observabilidade da AWS, responsável por coletar, armazenar e analisar métricas, logs e eventos de recursos e aplicações executados na nuvem.

Ele permite:

- Monitoramento em tempo real de recursos AWS
- Criação de alarmes baseados em métricas
- Centralização de logs
- Visualização de dados por meio de dashboards
- Automação baseada em eventos

No contexto desta arquitetura, o CloudWatch atua como o componente central de monitoramento das instâncias **Amazon RDS**, avaliando métricas de desempenho e capacidade, e acionando notificações automáticas por meio do **Amazon SNS** sempre que condições críticas são identificadas.

O foco da solução é transformar métricas técnicas em alertas acionáveis, permitindo resposta proativa a incidentes e maior confiabilidade operacional.



## 2. Principais Funcionalidades

### 2.1 Coleta de Métricas

O CloudWatch coleta automaticamente métricas padrão de serviços AWS, incluindo:

- CPUUtilization
- FreeableMemory
- ReadLatency
- WriteLatency
- DatabaseConnections
- FreeStorageSpace
- DiskQueueDepth
- ReadIOPS / WriteIOPS

### 2.2 Alarmes

Permite criar alarmes baseados em:

- Threshold estático
- Percentual
- Métricas compostas
- Avaliação por múltiplos períodos

### 2.3 Estatísticas e Visualização

- Média
- Soma
- Máximo
- Mínimo
- Percentis
- Dashboards personalizados

### 2.4 Integração com SNS

Quando um alarme entra em estado **ALARM**, o CloudWatch pode:

- Enviar notificação via SNS
- Acionar função Lambda
- Executar automação adicional



## 3. Arquitetura

<img width="675" height="442" alt="image" src="https://github.com/user-attachments/assets/b2f2a923-5a7a-4195-a975-3aa6896789a1" />


### 3.1 Componentes

1. **Amazon RDS**
   - Publica métricas automaticamente no CloudWatch.

2. **Amazon CloudWatch**
   - Coleta e armazena métricas.
   - Avalia regras de alarme.
   - Gera estatísticas e dashboards.

3. **CloudWatch Alarm**
   - Define condições de disparo.
   - Envia ações quando o estado muda.

4. **Amazon SNS**
   - Distribui notificações para e-mail ou endpoints HTTP.



### 3.2 Fluxo Operacional

1. Instâncias RDS geram métricas.
2. CloudWatch coleta e armazena os dados.
3. Alarmes avaliam métricas conforme regras definidas.
4. Ao ultrapassar um limite:
   - O alarme entra em estado ALARM.
   - O SNS é acionado.
5. O SNS envia notificação aos responsáveis.



## 4. Casos de Uso

### 4.1 Monitoramento de Banco de Dados

Identificação de:

- Saturação de CPU
- Degradação de latência
- Falta de memória
- Crescimento anormal de conexões

### 4.2 Operação NOC / SRE

Integração com processos de:

- Resposta a incidentes
- Escalonamento técnico
- Gestão de SLA

### 4.3 Ambientes Críticos

Aplicações que exigem alta disponibilidade e visibilidade contínua.



## 5. Integração com Outros Serviços

O CloudWatch pode integrar-se com:

- Amazon SNS
- AWS Lambda
- AWS EventBridge
- AWS Systems Manager
- AWS Auto Scaling
- AWS Security Hub
- Ferramentas externas de monitoramento



## 6. Boas Práticas

### 6.1 Definir Thresholds Realistas

Evitar alarmes excessivos ou subdimensionados.

### 6.2 Utilizar Períodos de Avaliação

Exigir múltiplos datapoints para disparo.

### 6.3 Monitorar Tendências

Avaliar comportamento ao longo do tempo, não apenas picos isolados.

### 6.4 Segmentar Alarmes por Severidade

Criar níveis distintos de criticidade.

### 6.5 Utilizar Dashboards

Centralizar visualização operacional para times técnicos.



## 7. Limitações

- Alarmes baseados em thresholds podem não capturar anomalias complexas.
- Dependência de configuração correta de métricas.
- Notificações dependem de configuração adequada do SNS.
- Métricas detalhadas podem exigir recursos adicionais (ex: Enhanced Monitoring).



## 8. Conclusão

O Amazon CloudWatch é o componente central de observabilidade na AWS, permitindo monitoramento contínuo, geração de alertas e integração com mecanismos de resposta automática.

Quando aplicado ao monitoramento do Amazon RDS, possibilita:

- Detecção antecipada de problemas
- Redução de tempo de resposta
- Aumento da confiabilidade
- Governança operacional estruturada

Sua correta configuração é essencial para ambientes produtivos que demandam alta disponibilidade e controle contínuo de desempenho.
