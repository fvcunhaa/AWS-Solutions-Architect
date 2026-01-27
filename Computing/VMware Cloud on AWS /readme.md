# VMware Cloud on AWS 

**Serviço:** VMware Cloud on AWS  
**Categoria:** Computação / Infraestrutura híbrida / VMware  
**Documentação oficial:** https://aws.amazon.com/pt/vmware/vmwarecloudonaws/

---

## Visão Geral

O **VMware Cloud on AWS** permite executar **workloads VMware nativos** (vSphere, vSAN, NSX) diretamente na infraestrutura da AWS, sem necessidade de refatoração das aplicações.

O serviço é ideal para:
- Migração **lift-and-shift**
- Expansão de data centers on-premises
- Recuperação de desastres
- Estratégias híbridas e multicloud

Ele oferece integração nativa com serviços AWS, mantendo a **experiência operacional VMware** já conhecida pelas equipes.

---

## Conceitos

### SDDC (Software-Defined Data Center)
Ambiente gerenciado que inclui:
- VMware vSphere
- VMware vSAN
- VMware NSX
- VMware vCenter

### Conta SDDC
Conta dedicada onde o ambiente VMware Cloud é provisionado e gerenciado.

### Integração com VPC
Permite comunicação direta e segura entre workloads VMware e recursos AWS nativos.

### Conectividade
- Elastic Network Interface (ENI)
- VPC Router
- Rotas privadas entre VPCs

### Casos comuns
- Migração sem refatoração
- Integração gradual com serviços AWS
- Operações híbridas consistentes

---

## Arquitetura – Account and VPC Considerations

<img width="804" height="424" alt="image" src="https://github.com/user-attachments/assets/481135a5-2da2-43f4-bb0a-6a2db894b6c7" />


**Fonte oficial:**  
https://aws.amazon.com/pt/blogs/apn/account-and-vpc-considerations-for-vmware-cloud-on-aws/

---

### Visão Geral da Arquitetura

Esta arquitetura demonstra a **integração entre o ambiente VMware Cloud on AWS (SDDC)** e uma **VPC do cliente**, permitindo comunicação privada e de baixa latência entre workloads VMware e instâncias EC2.

O objetivo é possibilitar **arquiteturas híbridas**, onde aplicações VMware coexistem e interagem com serviços AWS nativos.

---

### Descrição do Fluxo

1. **VMware Cloud SDDC Account**
   - Ambiente VMware totalmente gerenciado
   - Executa workloads legados e virtualizados

2. **VPC do Cliente**
   - Contém subnets privadas
   - Hospeda instâncias EC2 e outros serviços AWS

3. **Elastic Network Interface (ENI)**
   - Conecta o SDDC à VPC do cliente
   - Permite tráfego privado e seguro

4. **VPC Router**
   - Gerencia o roteamento entre subnets
   - Direciona tráfego entre EC2 e VMware workloads

5. **Instâncias EC2**
   - Consomem ou fornecem serviços para workloads VMware
   - Possibilitam modernização gradual da arquitetura

---

## Casos de Uso

Os casos de uso abaixo são baseados na documentação oficial e no artigo de arquitetura:

### 1. Migração lift-and-shift
Mover workloads VMware para a AWS sem alterações de código.

🔗 https://aws.amazon.com/pt/vmware/vmwarecloudonaws/

---

### 2. Expansão de data center
Utilizar a AWS como extensão do ambiente on-premises.

🔗 https://aws.amazon.com/pt/vmware/vmwarecloudonaws/

---

### 3. Integração com serviços AWS
Conectar aplicações VMware a bancos, analytics e serviços gerenciados da AWS.

🔗 https://aws.amazon.com/pt/blogs/apn/account-and-vpc-considerations-for-vmware-cloud-on-aws/

---

### 4. Recuperação de desastres
Usar VMware Cloud on AWS como ambiente de DR.

🔗 https://aws.amazon.com/pt/vmware/vmwarecloudonaws/

---

## Boas Práticas

### Arquitetura
- Planeje CIDRs para evitar sobreposição
- Separe ambientes por VPCs
- Utilize conectividade privada sempre que possível

---

### Operação
- Monitore latência entre SDDC e VPC
- Planeje capacidade de hosts VMware
- Automatize provisões com Infrastructure as Code

---

### Segurança
- Restrinja rotas e Security Groups
- Utilize NSX para microsegmentação
- Integre com IAM e controles corporativos

---

### Custos
- Planeje corretamente o tamanho do SDDC
- Utilize ambientes sob demanda apenas quando necessário
- Avalie casos de uso para evitar overprovisioning

---

## Observações Finais

O VMware Cloud on AWS é a solução ideal para organizações que desejam **migrar rapidamente para a AWS**, mantendo seus investimentos em VMware e sem interromper operações.

Ele permite uma **transição gradual para a nuvem**, combinando workloads legados e serviços modernos da AWS, com segurança, performance e governança.
