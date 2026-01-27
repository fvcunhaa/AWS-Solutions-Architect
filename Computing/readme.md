# Computação na AWS

Este diretório reúne a documentação de estudo relacionada aos **serviços de computação da AWS**, cobrindo desde workloads tradicionais em máquinas virtuais até execução de aplicações serverless, batch, híbridas e de edge computing.

O objetivo é fornecer uma visão estruturada dos serviços de computação, seus conceitos, casos de uso e boas práticas, apoiando decisões de arquitetura e operação.

---

## 🎯 Visão Geral

A camada de **Computação da AWS** oferece serviços flexíveis para executar aplicações em diferentes modelos:

- Máquinas virtuais
- Containers e workloads batch
- Plataformas gerenciadas
- Ambientes híbridos e edge
- Serverless e aplicações distribuídas

Esses serviços permitem escalar aplicações de forma elástica, reduzir custos operacionais e adaptar a execução ao tipo de workload.

---

## 🧠 Serviços Abordados

### 🖥️ Amazon EC2
Serviço de **máquinas virtuais (IaaS)** altamente configurável, permitindo controle total sobre sistema operacional, rede e armazenamento.

**Principais usos:**
- Workloads tradicionais
- Aplicações legadas
- Ambientes customizados
- Bancos de dados autogerenciados

📂 Pasta: `amazon-ec2/`

---

### 📈 Amazon EC2 Auto Scaling
Serviço que permite **escalar automaticamente instâncias EC2**, com base em métricas, políticas e demanda.

**Principais usos:**
- Alta disponibilidade
- Escalabilidade automática
- Redução de custos
- Arquiteturas resilientes

📂 Pasta: `ec2-auto-scaling/`

---

### ⚙️ AWS Batch
Serviço gerenciado para **execução de workloads batch**, orquestrando recursos de computação automaticamente.

**Principais usos:**
- Processamento em lote
- Jobs científicos
- Análises de dados
- Workloads de alta performance

📂 Pasta: `aws-batch/`

---

### 🌱 AWS Elastic Beanstalk
Plataforma como serviço (PaaS) para **deploy e gerenciamento de aplicações**, abstraindo infraestrutura.

**Principais usos:**
- Deploy rápido de aplicações
- Ambientes gerenciados
- Redução de complexidade operacional

📂 Pasta: `elastic-beanstalk/`

---

### 🏢 AWS Outposts
Extensão da infraestrutura AWS para **ambientes on-premises**, oferecendo uma experiência híbrida consistente.

**Principais usos:**
- Workloads com baixa latência
- Requisitos regulatórios
- Ambientes híbridos

📂 Pasta: `aws-outposts/`

---

### 📦 AWS Serverless Application Repository
Repositório gerenciado para **aplicações serverless reutilizáveis**, baseadas em AWS SAM.

**Principais usos:**
- Reuso de componentes
- Aceleração de desenvolvimento serverless
- Padronização de soluções

📂 Pasta: `serverless-application-repository/`

---

### 🧩 VMware Cloud on AWS
Serviço que permite executar **workloads VMware nativos** diretamente na infraestrutura da AWS.

**Principais usos:**
- Migração lift-and-shift
- Ambientes híbridos
- Continuidade de negócios

📂 Pasta: `vmware-cloud-on-aws/`

---

### 📡 AWS Wavelength
Infraestrutura de computação e armazenamento integrada às redes **5G**, reduzindo latência para aplicações edge.

**Principais usos:**
- Aplicações de baixa latência
- IoT
- Jogos online
- Realidade aumentada e virtual

📂 Pasta: `aws-wavelength/`

---

## 🏗️ Organização do Diretório

Estrutura sugerida:

├── aws-batch/

├── amazon-ec2/

├── ec2-auto-scaling/

├── elastic-beanstalk/

├── aws-outposts/

├── serverless-application-repository/

├── vmware-cloud-on-aws/

├── aws-wavelength/

└── README.md


Cada pasta conterá:
- Visão Geral
- Conceitos
- Arquitetura (quando aplicável)
- Casos de Uso
- Boas Práticas
- Observações Finais

---

## 📌 Boas Práticas Gerais

- Escolha o modelo de computação adequado ao workload
- Automatize escalabilidade sempre que possível
- Monitore uso e custos de forma contínua
- Combine serviços gerenciados para reduzir esforço operacional
- Considere requisitos de latência, compliance e resiliência

---

## 📚 Público-Alvo

Este material é indicado para:
- Arquitetos Cloud
- Engenheiros DevOps / SRE
- Desenvolvedores
- Times de Infraestrutura
- Profissionais responsáveis por modernização de aplicações

---

## ✍️ Observações Finais

A computação na AWS é extremamente flexível e abrangente. Entender as **diferenças, vantagens e limitações** de cada serviço é essencial para projetar arquiteturas eficientes, seguras e economicamente sustentáveis.

Este diretório será expandido continuamente com exemplos práticos, arquiteturas de referência e recomendações baseadas em cenários reais.
