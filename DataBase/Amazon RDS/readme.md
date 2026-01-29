# Amazon Relational Database Service (Amazon RDS) – Documentação de Estudo

**Serviço:** Amazon Relational Database Service (Amazon RDS)  
**Categoria:** Banco de Dados / Relacional gerenciado  
**Documentação oficial:** https://aws.amazon.com/pt/rds/

---

## Visão Geral

O **Amazon RDS** é um serviço totalmente gerenciado de **bancos de dados relacionais**, que facilita a criação, operação e escalabilidade de bancos na AWS, removendo a complexidade de tarefas operacionais como provisionamento, backups, patching e failover.

O RDS suporta múltiplos engines populares e é amplamente utilizado em aplicações corporativas, transacionais e sistemas legados modernizados.

---

## Conceitos

### Engines Suportados
- Amazon Aurora
- MySQL
- PostgreSQL
- MariaDB
- Oracle
- SQL Server

### Instância RDS
Ambiente isolado que executa um engine de banco de dados específico, com CPU, memória e storage definidos.

### Storage Gerenciado
- Amazon EBS como backend
- Backups automáticos
- Snapshots manuais

### Alta Disponibilidade (Multi-AZ)
- Réplica síncrona em outra AZ
- Failover automático
- Redução de downtime

### RDS Custom
Modelo que permite **acesso ao sistema operacional** da instância, mantendo automações do RDS.

---

## Arquitetura – Amazon RDS Custom



**Fonte oficial:**  
https://docs.aws.amazon.com/pt_br/AmazonRDS/latest/UserGuide/custom-concept.html

---

### Visão Geral da Arquitetura

<img width="654" height="583" alt="image" src="https://github.com/user-attachments/assets/5fdbdfbc-cd10-469d-8dee-ba3bc05a4a5c" />


Esta arquitetura apresenta o **Amazon RDS Custom**, uma variação do RDS que oferece maior controle sobre o ambiente do banco de dados, permitindo acesso ao **sistema operacional** e ao **filesystem**, sem perder os benefícios de automação e gerenciamento do serviço.

É indicada para workloads que exigem customizações específicas ou ferramentas não suportadas no RDS padrão.

---

### Descrição do Fluxo

1. **Amazon VPC**
   - Isolamento de rede para o banco de dados
   - Subnets privadas dedicadas

2. **RDS Custom Instance**
   - Executa sobre uma instância Amazon EC2
   - Engine relacional com acesso ao SO

3. **Sistema Operacional**
   - Controle parcial pelo cliente
   - Instalação de agentes e ferramentas adicionais

4. **Amazon EBS**
   - Storage persistente
   - Backups e snapshots gerenciados

5. **Endpoint RDS**
   - Ponto de acesso para aplicações
   - Abstrai detalhes da infraestrutura

6. **Automação e Monitoramento**
   - Backups automáticos
   - Monitoramento via CloudWatch

7. **Integrações**
   - Logs e auditoria via CloudTrail
   - Armazenamento de backups no Amazon S3

---

## Casos de Uso

Os casos de uso abaixo são baseados na documentação oficial da AWS:

### 1. Aplicações transacionais tradicionais
Sistemas OLTP que dependem de bancos relacionais.

🔗 https://aws.amazon.com/pt/rds/

---

### 2. Migração de bancos on-premises
Modernização de bancos legados com mínima refatoração.

🔗 https://aws.amazon.com/pt/rds/

---

### 3. Workloads que exigem customização
Uso de agentes, extensões ou ferramentas específicas (RDS Custom).

🔗 https://docs.aws.amazon.com/pt_br/AmazonRDS/latest/UserGuide/custom-concept.html

---

### 4. Ambientes corporativos regulados
Controle, auditoria e conformidade com padrões de segurança.

🔗 https://aws.amazon.com/pt/rds/

---

## Boas Práticas

### Arquitetura
- Utilize Multi-AZ para produção
- Separe ambientes por contas ou VPCs
- Escolha corretamente o engine

---

### Performance
- Dimensione corretamente a instância
- Utilize índices adequados
- Monitore IOPS e latência

---

### Segurança
- Utilize subnets privadas
- Restrinja acesso com Security Groups
- Ative criptografia em repouso e em trânsito

---

### Operação
- Automatize backups e retenção
- Monitore métricas no CloudWatch
- Planeje janelas de manutenção

---

## Observações Finais

O **Amazon RDS** é a base relacional da AWS, oferecendo um equilíbrio ideal entre **simplicidade operacional, confiabilidade e flexibilidade**.

Com opções como **Multi-AZ, Read Replicas e RDS Custom**, ele atende desde aplicações simples até **ambientes corporativos complexos**, sendo uma escolha sólida para modernização e operação de bancos relacionais na nuvem.
