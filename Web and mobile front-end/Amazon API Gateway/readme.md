# Amazon API Gateway – Documentação de Estudo

**Serviço:** Amazon API Gateway  
**Categoria:** Integração / APIs / Front-End  
**Documentação oficial:** https://aws.amazon.com/pt/api-gateway/



## Visão Geral

O **Amazon API Gateway** é um serviço totalmente gerenciado que permite criar, publicar, manter, monitorar e proteger **APIs REST, HTTP e WebSocket** em qualquer escala.

Ele funciona como **porta de entrada das suas APIs**, oferecendo:

- Deploy de APIs com segurança
- Autenticação e autorização
- Throttling e caching
- Monitoramento e auditoria
- Integração com backends serverless e clássicos

O API Gateway é ideal para aplicações Web e Mobile que demandam **backend escalável, seguro e desacoplado**.



## Conceitos

### Tipos de API

| Tipo | Descrição |
|------|-------------|
| **REST API** | APIs completas e flexíveis, com métodos, recursos, deploys e stages |
| **HTTP API** | API mais leve e com menor latência, ideal para backends modernos |
| **WebSocket API** | Comunicação bidirecional para aplicações em tempo real |



### Autenticação e Segurança

O API Gateway pode ser integrado com:

- Amazon **Cognito** para autenticação de usuários
- IAM para autorização granular
- Lambda Authorizers para lógica customizada
- Integração com WAF para proteção de APIs



### Deploy e Versionamento

- **Stages** (dev, test, prod)
- **Custom domains** com certificados SSL (via ACM)
- Versionamento da API com suporte a múltiplas versões



## Arquitetura – Cargas de Trabalho Híbridas com API Gateway

<img width="795" height="395" alt="image" src="https://github.com/user-attachments/assets/3f805275-1cb4-48d7-b478-691fb3ee12d9" />


::contentReference[oaicite:0]{index=0}


**Fonte oficial:**  
https://aws.amazon.com/pt/blogs/aws-brasil/potencializando-cargas-de-trabalho-hibridas-com-o-amazon-api-gateway/



### Visão Geral da Arquitetura



Este padrão demonstra como o **Amazon API Gateway** pode ser utilizado para expor APIs que atendem tanto backends executando na AWS quanto backends **on-premises ou híbridos**, integrando-se com serviços internos de forma segura e escalável.

O foco é unificar a interface da API, adicionar autenticação e permitir governança centralizada, sem necessidade de alterações profundas no backend já existente.



### Descrição do Fluxo

1. **Clientes Web e Mobile**
   - Chamadas para APIs públicas ou privadas

2. **Amazon API Gateway**
   - Recebe as requisições
   - Aplica autenticação, autorização e políticas

3. **Workloads Backend**
   - APIs serverless via **AWS Lambda**
   - Serviços containerizados (ECS / EKS)
   - Endpoints internos on-premises
   - Integração com VPC Link / PrivateLink

4. **Segurança**
   - Autenticação com **Cognito**
   - Proteção com **AWS WAF**
   - Controle de acesso via IAM

5. **Observabilidade**
   - Logs de acesso e execução
   - Métricas no **CloudWatch**
   - Trace distribuído (opcional com X-Ray)



## Casos de Uso

### 1. Backend unificado para aplicações Web & Mobile
Criação de APIs que atendem apps diversos com segurança e governança.

🔗 https://aws.amazon.com/pt/api-gateway/



### 2. Workloads híbridos
Integração de APIs com serviços tanto na AWS quanto on-premises.

🔗 https://aws.amazon.com/pt/blogs/aws-brasil/potencializando-cargas-de-trabalho-hibridas-com-o-amazon-api-gateway/



### 3. Microsserviços desacoplados
Orquestração de chamadas para serviços diversos de forma escalável.

🔗 https://aws.amazon.com/pt/api-gateway/



### 4. APIs em produção com alta demanda
Serviços expostos com throttling, caching e proteção contra abuso.

🔗 https://aws.amazon.com/pt/api-gateway/



## Boas Práticas

### Segurança
- Autenticação com **Cognito ou IAM**
- Use **WAF** para proteção contra ataques
- Habilite SSL com **ACM** em domains personalizados



### Performance
- Habilite **cache** para endpoints que permitem
- Utilize **throttling** para proteger backends
- Configure **HTTP API** quando apropriado (latência menor)



### Operação
- Monitore métricas e logs no **CloudWatch**
- Use **X-Ray** para tracing distribuído
- Teste APIs regularmente



## Observações Finais

O **Amazon API Gateway** é um componente central em arquiteturas modernas baseadas em APIs, permitindo:

- APIs seguras e escaláveis
- Integração entre aplicações internas e externas
- Governança centralizada
- Suporte para cargas híbridas

Com suporte aos principais padrões de API (REST, HTTP e WebSocket), ele atende desde microsserviços até backends complexos.



📌 Recomendações:
- Combine API Gateway com **Cognito** e **WAF** para melhor segurança
- Utilize **CloudFront** na frente da API para cache global em APIs públicas
- Monitore e trace com **CloudWatch + X-Ray**
