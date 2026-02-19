# Notificação Automática na Criação de Usuário IAM

## 1. Visão Geral

Esta arquitetura implementa um mecanismo automatizado de auditoria e notificação sempre que um novo usuário IAM é criado na conta AWS.

A solução utiliza eventos do AWS CloudTrail integrados ao Amazon EventBridge (CloudWatch Events), acionando uma função AWS Lambda que pode registrar informações em um bucket Amazon S3 e enviar notificações por meio do Amazon SNS.

Objetivos principais:

- Aumentar a visibilidade sobre criação de identidades
- Reforçar governança e conformidade
- Implementar resposta automática a eventos sensíveis
- Garantir rastreabilidade de ações administrativas



## 2. Principais Funcionalidades

- Monitoramento de eventos de criação de usuário IAM
- Processamento automático orientado a eventos
- Persistência opcional de logs estruturados em S3
- Envio automático de notificação por e-mail via SNS
- Arquitetura serverless e escalável



## 3. Arquitetura

<img width="793" height="291" alt="image" src="https://github.com/user-attachments/assets/cf3c1c78-8d8b-4a76-b24e-c7bd2fa0b256" />


### 3.1 Componentes

1. **IAM**
   - Evento monitorado: `CreateUser`

2. **AWS CloudTrail**
   - Registra eventos de API na conta
   - Captura a criação do usuário IAM

3. **Amazon EventBridge (CloudWatch Events)**
   - Regra configurada para capturar eventos específicos do CloudTrail
   - Filtra eventos onde `eventName = CreateUser`

4. **AWS Lambda**
   - Processa o evento recebido
   - Pode formatar dados, enriquecer informações e armazenar no S3
   - Publica mensagem no SNS

5. **Amazon S3**
   - Armazena registros estruturados do evento (opcional)

6. **Amazon SNS**
   - Envia notificação por e-mail aos administradores



### 3.2 Fluxo Operacional

1. Um administrador cria um novo usuário IAM.
2. O CloudTrail registra o evento `CreateUser`.
3. O EventBridge identifica o evento com base na regra configurada.
4. A regra aciona a função Lambda.
5. A Lambda:
   - Extrai informações do evento (quem criou, quando, qual usuário foi criado)
   - Armazena log no S3 (opcional)
   - Publica notificação no SNS
6. O SNS envia e-mail aos destinatários configurados.



## 4. Casos de Uso

### 4.1 Governança de Identidades

Monitoramento contínuo de criação de usuários fora de processos padronizados.

### 4.2 Auditoria e Compliance

Atendimento a requisitos regulatórios que exigem rastreamento de criação de identidades.

### 4.3 Segurança Proativa

Identificação imediata de criação indevida ou não autorizada de usuários IAM.

### 4.4 Integração com SOC / SIEM

A Lambda pode ser adaptada para enviar eventos a ferramentas externas de segurança.



## 5. Integração com Outros Serviços

A solução integra-se com:

- AWS IAM
- AWS CloudTrail
- Amazon EventBridge
- AWS Lambda
- Amazon S3
- Amazon SNS
- AWS Organizations (em ambientes multi-conta)

Pode ser expandida para:

- AWS Security Hub
- AWS Config
- Sistemas externos via webhook



## 6. Boas Práticas

### 6.1 Monitorar Eventos Sensíveis

Além de `CreateUser`, considerar monitorar:

- `AttachUserPolicy`
- `PutUserPolicy`
- `CreateAccessKey`
- `AddUserToGroup`

### 6.2 Princípio do Menor Privilégio

A função Lambda deve possuir apenas permissões mínimas necessárias.

### 6.3 Criptografia

- Habilitar criptografia no bucket S3
- Utilizar SNS com políticas restritivas

### 6.4 Centralizar Logs

Utilizar uma conta dedicada para log archive em ambientes multi-conta.

### 6.5 Alertas Granulares

Enviar notificações diferentes conforme tipo de evento.



## 7. Limitações

- Dependência do CloudTrail estar habilitado
- Pequeno atraso entre evento e notificação
- Notificação por e-mail depende da confirmação de assinatura SNS
- Não bloqueia a ação, apenas notifica (controle detectivo)



## 8. Conclusão

Essa arquitetura implementa um controle detectivo eficiente e automatizado para eventos sensíveis no IAM.

A combinação de CloudTrail, EventBridge, Lambda e SNS permite:

- Monitoramento em tempo real
- Resposta automatizada
- Auditoria estruturada
- Escalabilidade serverless

Trata-se de uma prática recomendada para ambientes que exigem governança forte e visibilidade sobre atividades administrativas.
