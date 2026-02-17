# Amazon Rekognition – Documentação de Estudo

**Serviço:** Amazon Rekognition  
**Categoria:** Machine Learning / Visão Computacional  
**Documentação oficial:** https://aws.amazon.com/pt/rekognition/



## Visão Geral

O **Amazon Rekognition** é um serviço de análise de imagens e vídeos baseado em Deep Learning que permite identificar objetos, pessoas, texto e atividades em mídias visuais.

Ele oferece APIs prontas para:

- Detecção de objetos
- Reconhecimento facial
- Análise de vídeo
- Detecção de texto em imagens
- Moderação de conteúdo
- Análise de comportamento

O Rekognition permite incorporar visão computacional em aplicações sem necessidade de treinar modelos complexos.



## Conceitos

### Detecção de Objetos
Identifica objetos presentes em imagens ou vídeos.



### Reconhecimento Facial
- Detecta rostos
- Compara faces
- Identifica indivíduos (com coleção treinada)



### Moderação de Conteúdo
Detecta conteúdo impróprio ou sensível.



### Análise de Texto
Extrai texto visível em imagens.



### Análise de Vídeo
Detecta eventos e atividades ao longo do tempo.



## Arquitetura – Monitoramento de Distanciamento Social

<img width="1229" height="496" alt="image" src="https://github.com/user-attachments/assets/25f1da7f-6a7c-47b7-ab06-913a596cba6e" />


Baseado no artigo oficial:

https://aws.amazon.com/pt/blogs/aws-brasil/utilizando-o-amazon-rekognition-para-identificar-situacoes-de-descumprimento-ao-distanciamento-social/



### Componentes da Arquitetura

1. Câmera (fonte de imagem)
2. Amazon S3 (armazenamento das imagens)
3. AWS Lambda (processamento)
4. Amazon Rekognition (análise visual)
5. Amazon SNS (alertas)
6. Email (notificação)



### Descrição do Fluxo

1. Câmera envia imagem para bucket Amazon S3.
2. Evento S3 aciona função AWS Lambda.
3. Lambda chama Amazon Rekognition.
4. Rekognition:
   - Detecta pessoas na imagem
   - Calcula distância entre indivíduos
5. Se distância mínima não for respeitada:
   - Lambda grava imagem no bucket de alertas
   - Lambda envia notificação via SNS
6. SNS envia alerta por email.



### Benefícios da Arquitetura

- Totalmente serverless
- Escalável automaticamente
- Monitoramento em tempo real
- Baixa latência



## Casos de Uso

### 1. Segurança e Vigilância
Monitoramento de áreas públicas e privadas.

🔗 https://aws.amazon.com/pt/rekognition/



### 2. Reconhecimento Facial
Controle de acesso e autenticação.



### 3. Moderação de Conteúdo
Análise automática de imagens enviadas por usuários.



### 4. Análise de Vídeo
Identificação de eventos e comportamentos.



### 5. Compliance e Segurança Sanitária
Monitoramento automático de distanciamento social.

🔗 https://aws.amazon.com/pt/blogs/aws-brasil/utilizando-o-amazon-rekognition-para-identificar-situacoes-de-descumprimento-ao-distanciamento-social/



## Boas Práticas

### Arquitetura
- Utilize S3 como ponto central de ingestão
- Automatize processamento com Lambda
- Use SNS para alertas em tempo real



### Performance
- Utilize processamento assíncrono para vídeos
- Armazene resultados em banco para análise posterior



### Segurança
- Restrinja acesso a imagens sensíveis
- Utilize criptografia em repouso
- Configure IAM adequadamente



### Custos
- Processe apenas imagens necessárias
- Configure retenção de dados
- Monitore uso via CloudWatch



## Observações Finais

O Amazon Rekognition permite implementar soluções avançadas de visão computacional com baixa complexidade operacional.

Integrado com S3, Lambda e SNS, possibilita arquiteturas serverless escaláveis para:

- Segurança
- Monitoramento
- Moderação de conteúdo
- Análise inteligente de imagens e vídeos

É ideal para empresas que desejam aplicar inteligência visual de forma rápida e segura.
