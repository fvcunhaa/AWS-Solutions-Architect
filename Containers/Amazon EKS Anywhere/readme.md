# Amazon EKS Anywhere – Documentação de Estudo

**Serviço:** Amazon EKS Anywhere  
**Categoria:** Contêineres / Kubernetes / Híbrido e On-premises  
**Documentação oficial:** https://aws.amazon.com/pt/eks/eks-anywhere/

---

## Visão Geral

O **Amazon EKS Anywhere** permite criar e operar **clusters Kubernetes on-premises** utilizando a **mesma distribuição e ferramentas do Amazon EKS**, garantindo consistência operacional entre ambientes locais e a nuvem AWS.

Ele foi projetado para organizações que precisam:
- Executar Kubernetes fora da AWS
- Manter controle total da infraestrutura
- Padronizar ambientes híbridos
- Facilitar futuras migrações para a nuvem

---

## Conceitos

### Kubernetes Upstream
O EKS Anywhere utiliza Kubernetes **100% compatível com o upstream**, garantindo portabilidade e aderência ao padrão open source.

### Cluster EKS Anywhere
Cluster Kubernetes executado on-premises (bare metal ou virtualização), gerenciado com ferramentas da AWS.

### EKS Distro
Distribuição Kubernetes mantida pela AWS, com:
- Patches de segurança
- Versões testadas e validadas
- Binários consistentes com o EKS gerenciado

### Ferramentas de Gerenciamento
- `eksctl`
- GitOps (Flux)
- Integração com ferramentas CI/CD

### Independência da Nuvem
O cluster **não depende de conectividade contínua** com a AWS para operar.

---

## Arquitetura – Kubernetes Cluster em Ação



**Fonte oficial:**  
https://docs.aws.amazon.com/pt_br/eks/latest/userguide/kubernetes-concepts.html

---

### Visão Geral da Arquitetura

<img width="888" height="472" alt="image" src="https://github.com/user-attachments/assets/d7c93486-102a-4cda-8b31-dde218a4b7df" />


Esta arquitetura representa um **cluster Kubernetes padrão**, aplicável tanto ao **Amazon EKS** quanto ao **Amazon EKS Anywhere**, destacando os principais componentes e fluxos de operação.

O objetivo é ilustrar como aplicações containerizadas são construídas, distribuídas e executadas em um ambiente Kubernetes.

---

### Descrição do Fluxo

1. **Desenvolvedor**
   - Cria aplicações containerizadas
   - Publica imagens em um registry (ex.: Amazon ECR)

2. **Registro de Contêiner**
   - Armazena imagens versionadas
   - Disponibiliza imagens para o cluster

3. **Control Plane**
   - Gerencia o estado do cluster
   - Controla agendamento, escalabilidade e saúde

4. **Worker Nodes**
   - Executam os pods e containers
   - Consomem imagens do registry

5. **Kubernetes Services / Load Balancer**
   - Expõem aplicações
   - Permitem acesso interno ou externo

6. **Usuários da Aplicação**
   - Acessam aplicações publicadas no cluster

---

## Casos de Uso

Os casos de uso abaixo são baseados na documentação oficial do serviço:

### 1. Kubernetes on-premises padronizado
Execução de clusters Kubernetes locais com a mesma experiência do EKS na AWS.

🔗 https://aws.amazon.com/pt/eks/eks-anywhere/

---

### 2. Ambientes híbridos
Clusters locais integrados a pipelines e práticas cloud-native.

🔗 https://aws.amazon.com/pt/eks/eks-anywhere/

---

### 3. Compliance e soberania de dados
Execução de workloads em ambientes controlados e regulados.

🔗 https://aws.amazon.com/pt/eks/eks-anywhere/

---

### 4. Preparação para migração à nuvem
Facilita migração futura para Amazon EKS gerenciado.

🔗 https://aws.amazon.com/pt/eks/eks-anywhere/

---

## Boas Práticas

### Arquitetura
- Planeje alta disponibilidade do control plane
- Utilize múltiplos worker nodes
- Separe workloads críticos por namespaces

---

### Operação
- Automatize upgrades com ferramentas oficiais
- Utilize GitOps para padronização
- Monitore saúde do cluster continuamente

---

### Segurança
- Aplique RBAC corretamente
- Utilize Network Policies
- Mantenha o cluster atualizado

---

### Governança
- Padronize versões Kubernetes
- Documente processos de operação
- Centralize logs e métricas

---

## Observações Finais

O **Amazon EKS Anywhere** é a escolha ideal para organizações que desejam **adotar Kubernetes de forma consistente em ambientes on-premises**, sem abrir mão de padrões, segurança e boas práticas adotadas na AWS.

Ele atua como ponte entre o mundo on-premises e a nuvem, permitindo modernização gradual, redução de riscos e padronização operacional em larga escala.
