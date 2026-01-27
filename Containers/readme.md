# Contêineres na AWS

Este diretório reúne a documentação de estudo relacionada aos **serviços de contêineres da AWS**, cobrindo desde orquestração gerenciada até execução de workloads Kubernetes e ECS fora da nuvem (on-premises e edge).

O objetivo é fornecer uma base sólida para **arquiteturas modernas baseadas em contêineres**, com foco em escalabilidade, portabilidade, automação e boas práticas operacionais.

---

## 🎯 Visão Geral

A AWS oferece um ecossistema completo para execução de aplicações em contêineres, atendendo diferentes necessidades:

- Orquestração gerenciada (ECS e EKS)
- Execução híbrida e on-premises
- Compatibilidade com Kubernetes open source
- Registro e gerenciamento de imagens de contêiner
- Integração com serviços nativos da AWS

Esses serviços são fundamentais para arquiteturas:
- Cloud-native
- Microsserviços
- Híbridas e multicloud
- Edge computing

---

## 🧠 Serviços Abordados

### 📦 Amazon Elastic Container Registry (ECR)
Registro de imagens de contêiner totalmente gerenciado, seguro e integrado à AWS.

**Principais usos:**
- Armazenamento de imagens Docker
- Integração com CI/CD
- Controle de versões e vulnerabilidades

📂 Pasta: `amazon-ecr/`

---

### 🚀 Amazon Elastic Container Service (ECS)
Orquestrador de contêineres nativo da AWS, simples e altamente integrado.

**Principais usos:**
- Execução de microsserviços
- Workloads containerizados
- Arquiteturas serverless com AWS Fargate

📂 Pasta: `amazon-ecs/`

---

### ☸️ Amazon Elastic Kubernetes Service (EKS)
Serviço gerenciado de Kubernetes, compatível com o padrão open source.

**Principais usos:**
- Orquestração Kubernetes gerenciada
- Portabilidade entre ambientes
- Ambientes corporativos Kubernetes

📂 Pasta: `amazon-eks/`

---

### 🌍 Amazon ECS Anywhere
Extensão do ECS para executar contêineres **fora da AWS**, usando a mesma API e ferramentas.

**Principais usos:**
- Execução on-premises
- Ambientes híbridos
- Edge computing com ECS

📂 Pasta: `ecs-anywhere/`

---

### 🌐 Amazon EKS Anywhere
Distribuição Kubernetes da AWS para execução **on-premises**, com foco em consistência operacional.

**Principais usos:**
- Kubernetes em data centers locais
- Ambientes híbridos padronizados
- Controle total da infraestrutura

📂 Pasta: `eks-anywhere/`

---

### 🧩 Amazon EKS Distro
Distribuição open source do Kubernetes usada pelo EKS, mantida pela AWS.

**Principais usos:**
- Kubernetes gerenciado pelo próprio time
- Ambientes customizados
- Controle total de ciclo de vida do Kubernetes

📂 Pasta: `eks-distro/`

---

## 🏗️ Organização do Diretório

Estrutura sugerida:
├── amazon-ecr/

├── amazon-ecs/

├── amazon-eks/

├── ecs-anywhere/

├── eks-anywhere/

├── eks-distro/

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

- Utilize imagens pequenas e seguras
- Automatize build e deploy com CI/CD
- Separe ambientes (dev, stage, prod)
- Monitore consumo de recursos
- Escolha o orquestrador adequado ao nível de complexidade

---

## 📚 Público-Alvo

Este material é indicado para:
- Arquitetos Cloud
- Engenheiros DevOps / SRE
- Desenvolvedores backend
- Times de plataforma
- Profissionais que trabalham com microsserviços

---

## ✍️ Observações Finais

Os serviços de contêineres da AWS permitem criar arquiteturas **altamente escaláveis, portáveis e resilientes**, atendendo desde workloads simples até ambientes corporativos complexos.

Este diretório servirá como base de estudo e referência prática para decisões de arquitetura, operação e modernização de aplicações baseadas em contêineres.
