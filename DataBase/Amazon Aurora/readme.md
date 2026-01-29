# Amazon Aurora 

**Serviço:** Amazon Aurora  
**Categoria:** Banco de Dados / Relacional gerenciado  
**Documentação oficial:** https://aws.amazon.com/pt/rds/aurora/

---

## Visão Geral

O **Amazon Aurora** é um banco de dados relacional **totalmente gerenciado**, compatível com **MySQL e PostgreSQL**, projetado para oferecer **alta performance, alta disponibilidade e escalabilidade automática** superiores aos bancos tradicionais.

Ele combina a simplicidade do Amazon RDS com uma **arquitetura distribuída nativa da AWS**, sendo amplamente utilizado em aplicações críticas e de missão essencial.

---

## Conceitos

### Compatibilidade MySQL e PostgreSQL
Aurora é compatível com ferramentas, drivers e aplicações existentes, facilitando migrações.

### Storage Distribuído
- Dados replicados automaticamente em **6 cópias distribuídas em 3 AZs**
- Tolerância a falhas sem intervenção manual

### Writer e Readers
- 1 instância **writer**
- Até 15 instâncias **read replicas**
- Failover automático em segundos

### Escalabilidade
- Storage cresce automaticamente até **128 TB**
- Leitura escalável horizontalmente

### Alta Disponibilidade
- Failover rápido
- Recuperação automática de falhas de storage

---

## Arquitetura – Migração de PostgreSQL On-Premises para Aurora



**Fonte oficial:**  
https://docs.aws.amazon.com/pt_br/prescriptive-guidance/latest/patterns/migrate-an-on-premises-postgresql-database-to-aurora-postgresql.html

---

### Visão Geral da Arquitetura
<img width="580" height="450" alt="image" src="https://github.com/user-attachments/assets/96a87325-69de-4e00-9e10-899c27b24207" />

Esta arquitetura demonstra a migração de um **banco PostgreSQL on-premises** para o **Amazon Aurora PostgreSQL-Compatible**, utilizando o **AWS Database Migration Service (DMS)**.

O objetivo é realizar uma migração **segura, controlada e com mínimo downtime**, mantendo conectividade privada e alta disponibilidade.

---

### Descrição do Fluxo

1. **Banco PostgreSQL On-Premises**
   - Fonte de dados original
   - Continua operando durante a migração

2. **Firewall e Internet**
   - Controlam acesso seguro ao ambiente AWS

3. **Amazon VPC**
   - Isola o ambiente de banco de dados
   - Contém subnets privadas

4. **AWS DMS**
   - Replica dados do banco on-premises
   - Suporta migração contínua (CDC)

5. **Amazon Aurora PostgreSQL-Compatible**
   - Banco de destino
   - Recebe dados replicados
   - Assume carga após migração

6. **Clientes (Web / SQL)**
   - Passam a se conectar ao Aurora após o cutover

---

## Casos de Uso

Os casos de uso abaixo são baseados na documentação oficial da AWS:

### 1. Aplicações transacionais críticas
Sistemas que exigem alta disponibilidade e performance.

🔗 https://aws.amazon.com/pt/rds/aurora/

---

### 2. Migração de bancos relacionais
Substituição de bancos on-premises ou RDS tradicionais.

🔗 https://docs.aws.amazon.com/pt_br/prescriptive-guidance/latest/patterns/migrate-an-on-premises-postgresql-database-to-aurora-postgresql.html

---

### 3. Escalabilidade de leitura
Uso intensivo de leitura com múltiplas réplicas.

🔗 https://aws.amazon.com/pt/rds/aurora/

---

### 4. Arquiteturas multi-AZ
Aplicações que não podem tolerar downtime.

🔗 https://aws.amazon.com/pt/rds/aurora/

---

## Boas Práticas

### Arquitetura
- Utilize subnets privadas para o banco
- Separe writers e readers corretamente
- Planeje endpoints de leitura e escrita

---

### Performance
- Ajuste parâmetros do engine
- Utilize índices adequados
- Use read replicas para escalar leitura

---

### Segurança
- Utilize criptografia em repouso e em trânsito
- Controle acesso com Security Groups
- Integre com IAM quando possível

---

### Operação
- Monitore métricas no CloudWatch
- Automatize backups
- Teste failover periodicamente

---

## Observações Finais

O **Amazon Aurora** é uma das soluções de banco de dados mais robustas da AWS, indicado para workloads **críticos, escaláveis e de alta disponibilidade**.

Ele é ideal para organizações que desejam **modernizar bancos relacionais**, reduzir esforço operacional e obter performance superior sem abrir mão da compatibilidade com MySQL e PostgreSQL.
