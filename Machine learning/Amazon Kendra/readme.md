# Amazon Kendra – Documentação de Estudo

**Serviço:** Amazon Kendra  
**Categoria:** Machine Learning / Busca Inteligente  
**Documentação oficial:** https://aws.amazon.com/pt/kendra/



## Visão Geral

O **Amazon Kendra** é um serviço de busca inteligente baseado em Machine Learning que permite criar mecanismos de busca corporativos altamente precisos.

Ele utiliza NLP e modelos de deep learning para:

- Entender linguagem natural
- Fornecer respostas contextuais
- Classificar relevância automaticamente
- Indexar múltiplas fontes de dados

O Kendra é ideal para:

- Portais internos
- FAQs corporativas
- Central de conhecimento
- Busca em documentos empresariais
- Atendimento automatizado



## Conceitos

### Index
Repositório onde os documentos são processados e armazenados para busca.



### Data Source
Fonte de dados conectada ao Kendra:
- Amazon S3
- SharePoint
- Salesforce
- Banco de dados
- Sistemas internos



### Documento
Arquivo indexado contendo:
- Conteúdo textual
- Metadados
- Permissões de acesso



### FAQ
Conjunto estruturado de perguntas e respostas para otimizar buscas frequentes.



### Relevância
Algoritmo de ML que classifica resultados com base no contexto da consulta.



## Arquitetura – Versionamento Automatizado de FAQs

<img width="876" height="553" alt="image" src="https://github.com/user-attachments/assets/27b31a08-d5d3-41ed-995b-be15319d5dda" />


Baseado no artigo oficial:

https://aws.amazon.com/pt/blogs/machine-learning/automate-and-implement-version-control-for-amazon-kendra-faqs/



### Componentes da Arquitetura

1. Usuário faz upload de documento (FAQ)
2. Amazon S3 armazena arquivo
3. Evento S3 dispara AWS Lambda
4. Lambda atualiza ou versiona FAQ no Amazon Kendra
5. Amazon SNS envia notificações (opcional)



### Descrição do Fluxo

1. Usuário envia novo documento de FAQ.
2. Documento é armazenado em um bucket S3.
3. Evento S3 aciona uma função Lambda.
4. Lambda:
   - Processa documento
   - Atualiza índice do Kendra
   - Controla versionamento
5. Kendra indexa automaticamente o conteúdo.
6. Usuários realizam buscas com linguagem natural.
7. Resultados são retornados com base em relevância e contexto.



## Casos de Uso

### 1. Portal de Conhecimento Corporativo
Busca em documentos internos, políticas, manuais e FAQs.

🔗 https://aws.amazon.com/pt/kendra/



### 2. Central de Atendimento
Respostas automáticas baseadas em perguntas frequentes.



### 3. Busca em Documentos Jurídicos
Indexação de contratos e relatórios.



### 4. Base de Conhecimento para Chatbots
Integração com Amazon Lex ou aplicações customizadas.



## Boas Práticas

### Indexação
- Estruture documentos com metadados
- Utilize permissões de acesso adequadas
- Separe índices por domínio quando necessário



### Arquitetura
- Use S3 como fonte primária
- Automatize ingestão via Lambda
- Versione FAQs e documentos



### Segurança
- Configure controle de acesso por usuário
- Utilize IAM e integração com sistemas de identidade
- Proteja dados sensíveis



### Performance
- Monitore métricas de relevância
- Ajuste pesos de ranking
- Atualize dados periodicamente



## Observações Finais

O Amazon Kendra permite construir mecanismos de busca corporativos com alta precisão sem necessidade de desenvolver algoritmos complexos de NLP.

Integrado com S3, Lambda e SNS, é possível criar soluções automatizadas, escaláveis e orientadas a conhecimento.

É ideal para empresas que desejam transformar documentos e FAQs em sistemas inteligentes de busca.
