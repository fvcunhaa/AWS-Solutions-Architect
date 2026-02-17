# Amazon Textract – Documentação de Estudo

**Serviço:** Amazon Textract  
**Categoria:** Machine Learning / Extração Inteligente de Documentos  
**Documentação oficial:** https://aws.amazon.com/pt/textract/



## Visão Geral

O **Amazon Textract** é um serviço de Machine Learning que extrai automaticamente:

- Texto
- Formulários (pares chave-valor)
- Tabelas
- Estrutura de documentos

a partir de:

- PDFs
- Imagens digitalizadas
- Documentos escaneados

Diferente de OCR tradicional, o Textract entende a estrutura do documento.



## Principais Funcionalidades

### 1. Extração de Texto (OCR avançado)
Extrai texto impresso ou manuscrito.



### 2. Extração de Formulários
Identifica automaticamente:
- Campos
- Valores associados
- Checkboxes



### 3. Extração de Tabelas
Reconhece:
- Linhas
- Colunas
- Estrutura tabular



### 4. Processamento Assíncrono
Ideal para:
- Grandes volumes
- PDFs extensos



### 5. Integração com Outros Serviços AWS
Funciona integrado com:

- Amazon S3
- AWS Lambda
- Amazon Comprehend
- Amazon OpenSearch
- Amazon SNS
- Amazon SQS



## Arquitetura – Extração Automatizada de Documentos

<img width="858" height="424" alt="image" src="https://github.com/user-attachments/assets/83c44c50-ade4-4bba-ad1f-dd0e6eea43f1" />


Baseado na arquitetura apresentada (Oil Well Data Extraction):



### Componentes da Arquitetura

1. Amazon S3 (armazenamento do documento)
2. AWS Lambda (Fn-A)
3. Amazon Textract
4. Amazon SNS
5. Amazon SQS
6. AWS Lambda (Fn-B)
7. Amazon Comprehend
8. Amazon OpenSearch
9. Kibana (visualização)



## Fluxo da Arquitetura

### 1️⃣ Upload
Usuário envia imagem ou PDF para o Amazon S3.



### 2️⃣ Trigger
Evento do S3 ativa AWS Lambda (Fn-A).



### 3️⃣ Extração
Lambda chama Amazon Textract para extrair:
- Texto
- Campos estruturados



### 4️⃣ Notificação
Textract envia status via Amazon SNS.



### 5️⃣ Fila
SNS publica mensagem para Amazon SQS.



### 6️⃣ Processamento
SQS ativa AWS Lambda (Fn-B).



### 7️⃣ Enriquecimento
Lambda chama Amazon Comprehend para:
- Análise de entidades
- Análise de sentimento
- Classificação



### 8️⃣ Indexação
Dados são enviados para Amazon OpenSearch.



### 9️⃣ Visualização
Kibana exibe dashboards e consultas.



## Benefícios da Arquitetura

- Totalmente serverless
- Escalável
- Processamento assíncrono
- Baixa manutenção
- Pipeline automatizado



## Casos de Uso

### 1. Processamento de Notas Fiscais
Extração automática de:
- CNPJ
- Valores
- Datas



### 2. Análise de Contratos
Extração de cláusulas e termos.



### 3. Processamento de Formulários Bancários
Automatização de cadastro.



### 4. Prontuários Médicos
Digitalização estruturada.



### 5. Indústria de Óleo e Gás
Extração de dados técnicos de relatórios PDF.



## Boas Práticas

### Armazenamento

- Use Amazon S3 como repositório central.
- Separe buckets por ambiente (dev, prod).



### Processamento

- Use processamento assíncrono para PDFs grandes.
- Utilize SQS para desacoplamento.



### Segurança

- Habilite criptografia no S3.
- Use IAM com princípio de menor privilégio.
- Audite com CloudTrail.



### Escalabilidade

- Lambda + SQS para alta demanda.
- Use Dead Letter Queue para falhas.



## Limitações Importantes

- Não substitui revisão humana em documentos críticos.
- Modelos são generalistas (não customizáveis).
- Pode ter limitações com documentos extremamente complexos.



## Comparação: Textract vs OCR Tradicional

| OCR Tradicional | Amazon Textract |
|--|-|
| Extrai texto simples | Entende estrutura |
| Não identifica campos | Identifica chave-valor |
| Não reconhece tabelas | Reconhece tabelas |
| Sem integração nativa | Integrado com AWS |



## Conclusão

O Amazon Textract é ideal para:

- Automatizar processamento de documentos
- Reduzir trabalho manual
- Estruturar dados não estruturados
- Integrar com pipelines de IA

É amplamente utilizado em:

- Bancos
- Seguradoras
- Saúde
- Governo
- Indústrias com alto volume documental
