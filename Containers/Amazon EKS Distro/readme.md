# Amazon EKS Distro – Documentação de Estudo

**Serviço:** Amazon EKS Distro (EKS-D)  
**Categoria:** Contêineres / Kubernetes / Distribuição open source  
**Documentação oficial:**  
- https://aws.amazon.com/pt/eks/eks-distro/  
- https://aws.amazon.com/pt/blogs/opensource/introducing-amazon-eks-distro/

---

## Visão Geral

O **Amazon EKS Distro (EKS-D)** é a **distribuição open source do Kubernetes** mantida pela AWS, utilizada internamente pelo **Amazon EKS** e disponibilizada para execução **fora do serviço gerenciado**, como em ambientes **on-premises, edge ou outras nuvens**.

O objetivo do EKS Distro é fornecer:
- Kubernetes compatível com o upstream
- Binários testados e validados pela AWS
- Consistência entre ambientes gerenciados e autogerenciados

---

## Conceitos

### Kubernetes Upstream
O EKS Distro segue rigorosamente o padrão do **Kubernetes open source**, sem extensões proprietárias.

### Componentes Incluídos
O EKS Distro fornece binários validados para:
- kube-apiserver
- kube-controller-manager
- kube-scheduler
- kubelet
- etcd
- CoreDNS
- CNI plugins

### Modelo de Responsabilidade
No EKS Distro, o **cliente é responsável** por:
- Provisionamento de infraestrutura
- Operação do cluster
- Atualizações
- Alta disponibilidade

A AWS fornece:
- Binários
- Patches de segurança
- Validação de versões

### Relação com Amazon EKS
O EKS Distro é a **base tecnológica do Amazon EKS**, garantindo compatibilidade total entre:
- EKS Distro
- EKS Anywhere
- EKS gerenciado na AWS

---

## Arquitetura – Posicionamento do EKS Distro



**Fonte oficial:**  
https://aws.amazon.com/pt/blogs/opensource/introducing-amazon-eks-distro/

---

### Visão Geral da Arquitetura

<img width="653" height="369" alt="image" src="https://github.com/user-attachments/assets/94b23ed9-dd1a-4b7e-a984-bbc2ec6d0349" />


Esta arquitetura ilustra o **posicionamento do Amazon EKS Distro** em relação às demais ofertas Kubernetes da AWS, destacando os **níveis de responsabilidade** entre cliente e AWS.

O EKS Distro está no extremo **self-managed**, oferecendo máxima flexibilidade e controle.

---

### Modelo de Responsabilidade

| Camada | Responsável |
|------|-------------|
| Control Plane | Cliente |
| Compute | Cliente |
| Data Plane | Cliente |
| Suporte | Comunidade |
| Atualizações | Cliente |

Em comparação:
- **Amazon EKS (gerenciado):** AWS gerencia control plane
- **Amazon EKS on Fargate:** AWS gerencia quase tudo
- **EKS Distro:** controle total do cliente

---

## Casos de Uso

Os casos de uso abaixo são baseados na documentação oficial:

### 1. Kubernetes autogerenciado padronizado
Uso de uma distribuição validada pela AWS para clusters próprios.

🔗 https://aws.amazon.com/pt/eks/eks-distro/

---

### 2. Ambientes híbridos e multicloud
Execução de Kubernetes fora da AWS mantendo compatibilidade com EKS.

🔗 https://aws.amazon.com/pt/eks/eks-distro/

---

### 3. Edge computing
Clusters leves e controlados em ambientes de borda.

🔗 https://aws.amazon.com/pt/eks/eks-distro/

---

### 4. Plataformas internas de Kubernetes
Base para construção de plataformas próprias (IDP – Internal Developer Platform).

🔗 https://aws.amazon.com/pt/blogs/opensource/introducing-amazon-eks-distro/

---

## Boas Práticas

### Arquitetura
- Planeje alta disponibilidade do control plane
- Separe nós de control plane e worker nodes
- Utilize etcd com backup frequente

---

### Operação
- Automatize provisionamento com Ansible, Terraform ou similares
- Documente processos de upgrade
- Teste upgrades em ambientes não produtivos

---

### Segurança
- Aplique RBAC corretamente
- Utilize Network Policies
- Mantenha binários sempre atualizados

---

### Governança
- Padronize versões Kubernetes
- Centralize logs e métricas
- Defina SLAs internos claros

---

## Observações Finais

O **Amazon EKS Distro** é a escolha ideal para organizações que precisam de **controle total sobre Kubernetes**, mas desejam manter **compatibilidade, segurança e previsibilidade** alinhadas ao Amazon EKS.

Ele não é indicado para times que buscam simplicidade operacional, mas sim para equipes maduras que desejam construir **plataformas Kubernetes próprias**, híbridas ou multicloud, com base sólida e confiável.
