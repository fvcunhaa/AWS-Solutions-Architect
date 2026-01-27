# AWS Outposts – Documentação de Estudo

**Serviço:** AWS Outposts  
**Categoria:** Computação / Infraestrutura híbrida  
**Documentação oficial:** https://aws.amazon.com/pt/outposts/

---

## Visão Geral

O **AWS Outposts** é um serviço que estende a infraestrutura, serviços e APIs da AWS para **ambientes on-premises**, permitindo executar workloads locais com a **mesma experiência operacional da nuvem AWS**.

Ele é projetado para cenários que exigem:
- Baixa latência
- Requisitos regulatórios ou de soberania de dados
- Integração profunda entre on-premises e cloud
- Arquiteturas híbridas consistentes

---

## Conceitos

### Outposts Rack
Rack físico entregue e gerenciado pela AWS, instalado no data center do cliente, contendo capacidade de computação, armazenamento e rede.

### VPC Estendida
Os recursos do Outposts fazem parte de uma **VPC da AWS**, permitindo uso dos mesmos conceitos de:
- Subnets
- Route tables
- Security Groups
- IAM

### Service Link
Conexão segura entre o Outposts e a região AWS, usada para gerenciamento, controle e serviços regionais.

### Local Gateway (LGW)
Gateway local que permite comunicação direta entre workloads on-premises e recursos locais ou externos, sem passar pela região.

### Serviços Suportados
- Amazon EC2
- Amazon EBS
- Amazon S3 on Outposts
- Amazon RDS on Outposts (casos específicos)

---

## Arquitetura – AWS Outposts High Availability & Data Protection



**Fonte oficial:**  
https://docs.aws.amazon.com/pt_br/whitepapers/latest/aws-outposts-high-availability-design/data-protection.html

---

### Visão Geral da Arquitetura
<img width="727" height="487" alt="image" src="https://github.com/user-attachments/assets/63927949-3402-423d-bf2f-36b70e7ad728" />

Esta arquitetura demonstra um **design de alta disponibilidade e proteção de dados** utilizando **múltiplos racks AWS Outposts**, integrados a uma VPC na AWS.

O objetivo é garantir:
- Continuidade operacional
- Redundância entre racks
- Proteção e replicação de dados
- Integração segura com a região AWS

---

### Descrição do Fluxo

1. **Virtual Private Cloud (VPC)**
   - Abrange tanto a região AWS quanto os racks Outposts
   - Unifica rede, segurança e governança

2. **AWS Outposts Rack A e B**
   - Racks físicos instalados no data center do cliente
   - Cada rack em uma subnet privada distinta

3. **VPC Access Points**
   - Controlam acesso aos serviços locais
   - Aplicam políticas de segurança

4. **Amazon S3 on Outposts**
   - Armazenamento de objetos local
   - Usado para dados sensíveis ou de baixa latência

5. **S3 Replication on Outposts**
   - Replicação entre racks
   - Aumenta durabilidade e disponibilidade dos dados

6. **Local Gateway (LGW)**
   - Comunicação direta entre workloads locais
   - Reduz dependência da região AWS

7. **AWS CloudWatch e EventBridge**
   - Monitoramento e eventos operacionais
   - Integração com automações e alertas

---

## Casos de Uso

Os casos de uso abaixo são baseados na documentação oficial e no whitepaper da AWS:

### 1. Workloads com baixa latência
Execução de aplicações que não toleram latência de ida e volta até a região AWS.

🔗 https://aws.amazon.com/pt/outposts/

---

### 2. Requisitos regulatórios e soberania de dados
Manter dados localmente atendendo exigências legais.

🔗 https://docs.aws.amazon.com/pt_br/whitepapers/latest/aws-outposts-high-availability-design/data-protection.html

---

### 3. Arquiteturas híbridas consistentes
Uso das mesmas APIs, ferramentas e práticas da AWS em cloud e on-premises.

🔗 https://aws.amazon.com/pt/outposts/

---

### 4. Continuidade de negócios on-premises
Alta disponibilidade e proteção de dados com múltiplos racks Outposts.

🔗 https://docs.aws.amazon.com/pt_br/whitepapers/latest/aws-outposts-high-availability-design/data-protection.html

---

## Boas Práticas

### Arquitetura
- Utilize múltiplos racks para alta disponibilidade
- Planeje corretamente subnets e endereçamento IP
- Separe workloads críticos e não críticos

---

### Resiliência
- Configure replicação de dados entre racks
- Monitore falhas de hardware e conectividade
- Teste cenários de falha regularmente

---

### Segurança
- Utilize IAM para controle de acesso
- Restrinja tráfego com Security Groups e NACLs
- Proteja a conexão Service Link

---

### Operação
- Monitore métricas via CloudWatch
- Integre eventos com EventBridge
- Planeje capacidade considerando crescimento futuro

---

## Observações Finais

O AWS Outposts é a solução ideal para organizações que precisam **levar a nuvem AWS para dentro do data center**, mantendo consistência operacional, segurança e governança.

Ele reduz drasticamente a complexidade de ambientes híbridos e permite modernizar workloads locais sem reescrever aplicações, sendo especialmente indicado para cenários corporativos e regulados.
