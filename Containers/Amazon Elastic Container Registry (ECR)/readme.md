# Amazon Elastic Container Registry (ECR) 

**Serviço:** Amazon Elastic Container Registry (Amazon ECR)  
**Categoria:** Contêineres / Registro de imagens  
**Documentação oficial:** https://aws.amazon.com/pt/ecr/

---

## Visão Geral

O **Amazon Elastic Container Registry (ECR)** é um serviço totalmente gerenciado de **registro de imagens de contêiner**, utilizado para armazenar, versionar e distribuir imagens Docker de forma **segura, escalável e integrada à AWS**.

O ECR é amplamente utilizado em conjunto com:
- Amazon ECS
- Amazon EKS
- AWS Batch
- Pipelines CI/CD

Ele elimina a necessidade de gerenciar registros privados e integra-se nativamente com **IAM, VPC, CloudTrail e serviços de segurança** da AWS.

---

## Conceitos

### Repositório (Repository)
Local lógico onde as imagens de contêiner são armazenadas e versionadas.

### Imagem de Contêiner
Artefato imutável que contém:
- Sistema base
- Dependências
- Aplicação
- Metadados

### Tag
Identificador de versão da imagem (ex.: `latest`, `v1.0.3`).

### Image Digest
Hash único que identifica uma imagem de forma imutável.

### Image Manifest
Estrutura que descreve:
- Configurações da imagem
- Camadas (layers)
- Metadados e arquitetura

### Integrações Nativas
- IAM para autenticação e autorização
- Amazon ECS / EKS para pull de imagens
- CI/CD para build e push automatizado

---

## Arquitetura – Estrutura de Imagens no Amazon ECR



**Fonte oficial:**  
https://aws.amazon.com/pt/blogs/aws-brasil/explorando-as-5-principais-funcionalidades-do-amazon-elastic-container-registry-amazon-ecr/

---

### Visão Geral da Arquitetura
<img width="832" height="526" alt="image" src="https://github.com/user-attachments/assets/63ca51ac-9190-490a-ac45-fc48d50f3204" />

Esta arquitetura demonstra como o **Amazon ECR armazena imagens de contêiner**, organizando-as em **repositórios**, com cada imagem sendo composta por **camadas (layers)** e um **manifesto** que descreve sua configuração.

O modelo de camadas permite:
- Reuso eficiente de dados
- Redução de espaço em disco
- Pull mais rápido de imagens

---

### Descrição do Fluxo

1. **Repositório ECR**
   - Armazena imagens de contêiner
   - Controla acesso e versionamento

2. **Image Manifest**
   - Contém metadados da imagem
   - Define arquitetura, sistema operacional e tags

3. **Camadas (Layers)**
   - Cada camada representa uma modificação incremental
   - Exemplo:
     - Layer 0: sistema base
     - Layer 1: dependências
     - Layer 2: aplicação

4. **Image ID / Digest**
   - Identificador imutável da imagem
   - Usado para garantir integridade

5. **Consumidores**
   - ECS, EKS ou outros serviços fazem pull da imagem
   - Apenas camadas não existentes localmente são baixadas

---

## Casos de Uso

Os casos de uso abaixo são baseados na documentação oficial do Amazon ECR:

### 1. Registro privado de imagens Docker
Armazenamento seguro de imagens proprietárias.

🔗 https://aws.amazon.com/pt/ecr/

---

### 2. Integração com pipelines CI/CD
Build, versionamento e publicação automática de imagens.

🔗 https://aws.amazon.com/pt/ecr/

---

### 3. Execução de workloads em ECS e EKS
Fonte central de imagens para clusters de contêineres.

🔗 https://aws.amazon.com/pt/ecr/

---

### 4. Segurança e conformidade
Análise de vulnerabilidades e controle de acesso via IAM.

🔗 https://aws.amazon.com/pt/ecr/

---

## Boas Práticas

### Arquitetura
- Separe repositórios por aplicação ou domínio
- Utilize múltiplas contas para isolamento
- Centralize imagens base (base images)

---

### Versionamento
- Evite depender apenas da tag `latest`
- Utilize versionamento semântico
- Faça referência a imagens por digest em produção

---

### Segurança
- Utilize IAM com menor privilégio
- Ative **image scanning**
- Use políticas de repositório restritivas

---

### Operação
- Configure políticas de lifecycle para limpeza automática
- Monitore uso de storage
- Audite acessos com CloudTrail

---

## Observações Finais

O Amazon ECR é um componente fundamental de qualquer arquitetura baseada em contêineres na AWS. Ele fornece **segurança, performance e integração nativa**, simplificando o gerenciamento do ciclo de vida de imagens.

Quando combinado com **ECS, EKS e pipelines CI/CD**, o ECR se torna a base confiável para entrega contínua de aplicações containerizadas em ambientes modernos.
