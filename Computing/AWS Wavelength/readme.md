# AWS Wavelength 

**Serviço:** AWS Wavelength  
**Categoria:** Computação / Edge Computing / 5G  
**Documentação oficial:** https://aws.amazon.com/pt/wavelength/

---

## Visão Geral

O **AWS Wavelength** leva serviços de computação e armazenamento da AWS para a **borda das redes 5G**, posicionando a infraestrutura **dentro dos data centers das operadoras de telecomunicações**.

O principal objetivo é reduzir drasticamente a **latência**, permitindo o desenvolvimento de aplicações que exigem **respostas em tempo quase real**, algo que não é possível apenas com regiões tradicionais da AWS.

---

## Conceitos

### Wavelength Zone
Zona de infraestrutura AWS implantada fisicamente dentro do data center da operadora (CSP – Communication Service Provider).

### Integração com Região AWS
Cada Wavelength Zone está associada a uma **região AWS pai**, utilizada para:
- Plano de controle
- Serviços não suportados localmente
- Gerenciamento e observabilidade

### Carrier Gateway
Gateway que permite comunicação direta entre:
- Recursos na Wavelength Zone
- Rede da operadora (5G)
- Dispositivos conectados

### Tipos de Recursos
- Amazon EC2
- Amazon EBS
- Amazon VPC (subnets específicas para Wavelength)

### Casos Sensíveis à Latência
Projetado para workloads que exigem latência de **milissegundos de um dígito**.

---

## Arquitetura – Deploy em Wavelength Zone



**Fonte oficial:**  
https://docs.aws.amazon.com/pt_br/prescriptive-guidance/latest/patterns/deploy-resources-wavelength-zone-using-terraform.html

---

### Visão Geral da Arquitetura

<img width="877" height="321" alt="image" src="https://github.com/user-attachments/assets/463b8f37-08c4-4bb4-bb50-925dfedb66e0" />

Esta arquitetura demonstra a implantação de recursos de computação em uma **Wavelength Zone**, conectando diretamente aplicações executadas na borda da rede 5G a **dispositivos e sistemas on-premises**.

O objetivo é **minimizar latência**, mantendo integração nativa com a AWS.

---

### Descrição do Fluxo

1. **Região AWS**
   - Gerencia o plano de controle
   - Centraliza monitoramento, logs e governança

2. **Amazon VPC**
   - Estende-se da região para a Wavelength Zone
   - Mantém isolamento e controle de rede

3. **Wavelength Zone**
   - Localizada no data center da operadora
   - Contém subnets públicas específicas

4. **Amazon EC2 (na Wavelength Zone)**
   - Executa aplicações sensíveis à latência
   - Atende diretamente dispositivos 5G

5. **Carrier Gateway**
   - Conecta workloads à rede da operadora
   - Permite tráfego direto para dispositivos móveis

6. **Rede da Operadora (CSP Network)**
   - Transporta dados 5G
   - Conecta dispositivos finais e internet

7. **Dispositivos On-Premises / 5G**
   - Câmeras IP
   - Dispositivos IoT
   - Aplicações móveis e edge

---

## Casos de Uso

Os casos de uso abaixo são baseados na documentação oficial da AWS:

### 1. Aplicações de baixa latência
Execução de aplicações que exigem resposta em tempo real.

🔗 https://aws.amazon.com/pt/wavelength/

---

### 2. IoT e Edge Computing
Processamento local de dados gerados por dispositivos distribuídos.

🔗 https://aws.amazon.com/pt/wavelength/

---

### 3. Jogos online e streaming interativo
Redução de latência para experiências imersivas.

🔗 https://aws.amazon.com/pt/wavelength/

---

### 4. Indústria, manufatura e cidades inteligentes
Automação, monitoramento e controle em tempo real.

🔗 https://docs.aws.amazon.com/pt_br/prescriptive-guidance/latest/patterns/deploy-resources-wavelength-zone-using-terraform.html

---

## Boas Práticas

### Arquitetura
- Separe workloads de borda e regionais
- Use Wavelength apenas para partes sensíveis à latência
- Centralize dados de longo prazo na região AWS

---

### Rede
- Planeje CIDRs cuidadosamente
- Utilize Carrier Gateway corretamente
- Restrinja tráfego com Security Groups

---

### Operação
- Monitore latência e disponibilidade
- Use CloudWatch para métricas e logs
- Automatize provisionamento com Terraform ou CloudFormation

---

### Custos
- Utilize Wavelength apenas quando houver real necessidade
- Combine com serviços regionais para reduzir custo
- Avalie impacto financeiro do edge computing

---

## Observações Finais

O AWS Wavelength é uma solução estratégica para aplicações que **não podem tolerar latência de rede tradicional**, aproximando a computação do usuário final.

Ele complementa — e não substitui — as regiões AWS, sendo ideal para arquiteturas híbridas que combinam **edge computing, 5G e serviços gerenciados da nuvem**.

Com isso, o AWS Wavelength fecha o portfólio de computação da AWS para cenários modernos e altamente distribuídos.
